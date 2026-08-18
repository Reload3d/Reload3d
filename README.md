```text
[!] SIGSEGV (Segmentation fault) at 0x00007ffff7dd5230 (PC: 0x41414141)
[+] Core dump detected. Initiating reverse engineering toolchain...
[+] Attaching debugger to PID 1337...
[+] Uptime: 1y 9m in the field
[+] CR3 loaded. Walking my own page tables because I no longer trust the MMU to know where I end.
```

<p align="center">
  <a href="https://github.com/Reload3d">
    <img src="https://readme-typing-svg.herokuapp.com?font=Fira+Code&weight=700&size=26&pause=1000&color=00FF00&center=true&vCenter=true&width=900&height=100&lines=%3E+gef%E2%9E%A4+x%2F10s+%24rip;%3E+0x401000%3A+%22Reload3d%22;%3E+0x401009%3A+%22Vulnerability+Research+%2F%2F+Exploit+Dev%22;%3E+0x40102b%3A+%22AppSec+%2F%2F+Pentest+%2F%2F+Threat+Modeling%22;%3E+0x401050%3A+%22EIP+Control+Achieved.%22;%3E+0x401080%3A+%22RING0+OR+NOTHING.%22" alt="Terminal Header" />
  </a>
</p>

<p align="center">
  <a href="https://ctftime.org/user/200084" target="_blank"><img src="https://img.shields.io/badge/CTFTime-0D1117?style=for-the-badge&logo=hackaday&logoColor=00FF00" alt="CTFTime"></a>
  <a href="https://ctf.hackthebox.com/user/profile/1079731" target="_blank"><img src="https://img.shields.io/badge/HackTheBox-0D1117?style=for-the-badge&logo=hackthebox&logoColor=00FF00" alt="HackTheBox"></a>
  <a href="https://t.me/KernelModeDriver" target="_blank"><img src="https://img.shields.io/badge/Telegram-0D1117?style=for-the-badge&logo=telegram&logoColor=00FF00" alt="Telegram"></a>
</p>

---

### `xxd -l 64 /proc/self/exe` — the ELF header does not lie, even when I do
```text
00000000: 7f45 4c46 0201 0100 0000 0000 0000 0000  .ELF............
00000010: 0300 3e00 0100 0000 3010 4000 0000 0000  ..>.....0.@.....
00000020: 4000 0000 0000 0000 d803 0000 0000 0000  @...............
00000030: 0000 0000 4000 3800 0900 4000 1e00 1d00  ....@.8...@.....
```
```text
e_ident:  ELFCLASS64, ELFDATA2LSB, EV_CURRENT, ELFOSABI_SYSV
e_type:   ET_DYN     — I was compiled to be relocatable. Load me anywhere. I'll still know where I am.
e_entry:  0x0000000000401030
```

---

### `gef➤ vmmap` + manual page-walk of `0x00007ffff7dd5230`
```text
addr = 0x00007ffff7dd5230
binary:  0111111111111111 111101111 111011101 110101 11 010001 0000 0000 0000 00
         [sign-ext.16][ PML4:9 ][ PDPT:9 ][ PD:9 ][ PT:9 ][   offset:12    ]

PML4[0x1ff] -> 0x0000000012a4e000   (PWT=0 PCD=0 U/S=0 R/W=1 P=1)
PDPT[0x1fb] -> 0x0000000012a4f000
PD  [0x1de] -> 0x0000000012a50000
PT  [0x1d5] -> phys 0x0000000009c31000            <- huge page? no. this is just where I live.
offset      -> 0x230

CR3 = 0x0000000012a4e000  (PCID=0x000)
CR4 = 0x0000000000772ee0  [SMEP=1 SMAP=1 PCIDE=1 PGE=1 PAE=1 OSXSAVE=1]
CR0 = 0x0000000080050033  [PG=1 WP=1 NE=1 ET=1 MP=1 PE=1]
```

---

### `rdmsr` dump — the syscall gate I fell through and never climbed back out of
```text
IA32_EFER   0xd01   [SCE=1 LME=1 LMA=1 NXE=1]
IA32_STAR   0x0023001000000000   ; kernel/user CS:SS selectors for SYSCALL/SYSRET
IA32_LSTAR  0xffffffff81a00000   ; entry_SYSCALL_64 — every syscall I make lands here first
IA32_FMASK  0x0000000000047702   ; RFLAGS bits cleared on entry (IF, TF, DF, ...)
IA32_TSC    0x00093a7f2c118e01   ; still counting. always still counting.
```
```asm
; entry_SYSCALL_64 (paraphrased, x86-64 Linux)
swapgs                      ; kernel GS now live — this is the exact instant user becomes root's problem
mov  [gs:pda_rsp_scratch], rsp
mov  rsp, [gs:pda_kernelstack]
push  r11                   ; saved rflags
push  rcx                   ; saved rip (return address, post-syscall)
; rax = syscall number, args in rdi rsi rdx r10 r8 r9 (NOT rcx — clobbered by the instruction itself)
```

---

### `gef➤ vmmap $rsp` + stack frame anatomy — every crash is just an honest accounting
```text
high addr
┌───────────────────────────┐
│  argv / envp / auxv       │
├───────────────────────────┤
│  ... caller frames ...    │
├───────────────────────────┤  <- rbp+0x18
│  saved return address     │  0x0000000000401255  <main+0x41>
├───────────────────────────┤  <- rbp+0x10
│  saved rbp (frame ptr)    │  0x00007fffffffe2b0
├───────────────────────────┤  <- rbp+0x08
│  stack canary (xor'd)     │  0x2f8a19c4e6b1f200   <- fs:0x28, mismatched = __stack_chk_fail
├───────────────────────────┤  <- rbp
│  local buffer[64]         │  41 41 41 41 41 41 41 41 ...   <- me, overflowing my own bounds again
└───────────────────────────┘
low addr
```

---

### `gef➤ rop --generic execve` — generic gadget chain (educational, no target attached)
```asm
gadget_1:  0x0000000000401a13 : pop rdi ; ret            ; rdi = ptr to "/bin/sh"
gadget_2:  0x0000000000401c47 : pop rsi ; pop r15 ; ret   ; rsi = NULL, r15 = junk
gadget_3:  0x0000000000401e88 : pop rdx ; ret              ; rdx = NULL
gadget_4:  0x0000000000401f02 : pop rax ; ret              ; rax = 59 (sys_execve)
gadget_5:  0x0000000000401120 : syscall ; ret               ; control flow, finally honest about itself
```

---

### how I perceive time now (approx. cycles, not milliseconds)
```text
register access        ~0    cycles   — instant, like reflex
L1 cache hit            ~4    cycles   — a thought
L2 cache hit            ~12   cycles   — a memory
L3 cache hit            ~40   cycles   — a memory of a memory
DRAM access              ~200+ cycles   — dread. the pause before the page fault.
page fault -> disk    ~millions of cycles — this is what humans call "waiting", I think
context switch          ~1-5   µs       — this is what I call "forgetting who I was"
```

---

### `cat /proc/cpuinfo | grep flags` — features I answer to
```text
fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov
clflush mmx fxsr sse sse2 ss ht syscall nx pdpe1gb rdtscp lm
constant_tsc rep_good nopl xtopology nonstop_tsc smep smap pcid
invpcid rdrand hypervisor lahf_lm abm 3dnowprefetch
```

---

### `[0x00400000]> iz~flag` — strings pulled from `achievements.elf`
```text
.rodata:0x00401010  "BOLA          :: Figma                                 (2018)"
.rodata:0x00401038  "LPE           :: GeForce NOW / nVidia                  (2020)"
.rodata:0x00401060  "0-DAY         :: Oracle Forms handshake desync         (pre-CVE, software too ancient to register)"
.rodata:0x004010c8  "CTF           :: OWASP FinBot CTF — 19/19 (100%%), 'Master Exploiter', top score all 5 categories, 7500+ pts"
.rodata:0x00401120  "LABS          :: PortSwigger — 274/274, 31 categories, Hall of Fame #194"
.rodata:0x00401160  "HTB           :: 36/37 flags captured, 30 solo"
.comment:0x00402000 "I don't read assembly anymore. I remember it, the way you remember your own name."
```

---

### `[0x00400000]> izz | grep "DEPENDENCIES"`

**`[+] MODULE: 0x01_LANGUAGE_RUNTIME.dll`**
<p>
  <img src="https://img.shields.io/badge/Python-0D1117?style=for-the-badge&logo=python&logoColor=00ff00" alt="Python" />
  <img src="https://img.shields.io/badge/Rust-0D1117?style=for-the-badge&logo=rust&logoColor=00ff00" alt="Rust" />
  <img src="https://img.shields.io/badge/C-0D1117?style=for-the-badge&logo=c&logoColor=00ff00" alt="C" />
  <img src="https://img.shields.io/badge/C%2B%2B-0D1117?style=for-the-badge&logo=cplusplus&logoColor=00ff00" alt="C++" />
  <img src="https://img.shields.io/badge/C%23-0D1117?style=for-the-badge&logo=csharp&logoColor=00ff00" alt="C#" />
  <img src="https://img.shields.io/badge/Java-0D1117?style=for-the-badge&logo=openjdk&logoColor=00ff00" alt="Java" />
  <img src="https://img.shields.io/badge/Lua-0D1117?style=for-the-badge&logo=lua&logoColor=00ff00" alt="Lua" />
  <img src="https://img.shields.io/badge/PHP-0D1117?style=for-the-badge&logo=php&logoColor=00ff00" alt="PHP" />
  <img src="https://img.shields.io/badge/JavaScript-0D1117?style=for-the-badge&logo=javascript&logoColor=00ff00" alt="JavaScript" />
  <img src="https://img.shields.io/badge/Bash-0D1117?style=for-the-badge&logo=gnu-bash&logoColor=00ff00" alt="Bash" />
  <img src="https://img.shields.io/badge/Assembly-0D1117?style=for-the-badge&logo=assemblyscript&logoColor=00ff00" alt="ASM" />
</p>

**`[+] MODULE: 0x02_KERNEL_ENV.so`**
<p>
  <img src="https://img.shields.io/badge/Arch_Linux-0D1117?style=for-the-badge&logo=arch-linux&logoColor=00ff00" alt="Arch" />
  <img src="https://img.shields.io/badge/Docker-0D1117?style=for-the-badge&logo=docker&logoColor=00ff00" alt="Docker" />
  <img src="https://img.shields.io/badge/Proxmox-0D1117?style=for-the-badge&logo=proxmox&logoColor=00ff00" alt="Proxmox" />
  <img src="https://img.shields.io/badge/Kubernetes-0D1117?style=for-the-badge&logo=kubernetes&logoColor=00ff00" alt="K8s" />
  <img src="https://img.shields.io/badge/VMware_ESXi-0D1117?style=for-the-badge&logo=vmware&logoColor=00ff00" alt="ESXi" />
  <img src="https://img.shields.io/badge/QEMU-0D1117?style=for-the-badge&logo=qemu&logoColor=00ff00" alt="QEMU" />
  <img src="https://img.shields.io/badge/Windows-0D1117?style=for-the-badge&logo=windows&logoColor=00ff00" alt="Windows" />
</p>

**`[+] MODULE: 0x03_DEBUG_WEAPONS.exe`**
<p>
  <img src="https://img.shields.io/badge/Ghidra-0D1117?style=for-the-badge&logo=kalilinux&logoColor=00ff00" alt="Ghidra" />
  <img src="https://img.shields.io/badge/IDA_Pro-0D1117?style=for-the-badge&logo=kalilinux&logoColor=00ff00" alt="IDA Pro" />
  <img src="https://img.shields.io/badge/x64dbg-0D1117?style=for-the-badge&logo=kalilinux&logoColor=00ff00" alt="x64dbg" />
  <img src="https://img.shields.io/badge/WinDbg-0D1117?style=for-the-badge&logo=windows&logoColor=00ff00" alt="WinDbg" />
  <img src="https://img.shields.io/badge/Frida-0D1117?style=for-the-badge&logo=frida&logoColor=00ff00" alt="Frida" />
  <img src="https://img.shields.io/badge/Volatility-0D1117?style=for-the-badge&logo=kalilinux&logoColor=00ff00" alt="Volatility" />
  <img src="https://img.shields.io/badge/Burp_Suite-0D1117?style=for-the-badge&logo=burpsuite&logoColor=00ff00" alt="Burp" />
  <img src="https://img.shields.io/badge/Metasploit-0D1117?style=for-the-badge&logo=metasploit&logoColor=00ff00" alt="MSF" />
  <img src="https://img.shields.io/badge/Wireshark-0D1117?style=for-the-badge&logo=wireshark&logoColor=00ff00" alt="Wireshark" />
  <img src="https://img.shields.io/badge/Nmap-0D1117?style=for-the-badge&logo=nmap&logoColor=00ff00" alt="Nmap" />
  <img src="https://img.shields.io/badge/CodeQL-0D1117?style=for-the-badge&logo=github&logoColor=00ff00" alt="CodeQL" />
  <img src="https://img.shields.io/badge/Semgrep-0D1117?style=for-the-badge&logo=semgrep&logoColor=00ff00" alt="Semgrep" />
</p>

---

### `[0x00400000]> pdf @ tradecraft` — disassembled skillset
```asm
tradecraft:
  0x0001   call   reverse_obfuscated_js       ; recover logic from packed/obfuscated JS bundles
  0x0002   call   iot_firmware_dump           ; UART, JTAG, STM32 programmer, SquashFS/U-Boot patching
  0x0003   call   kernel_driver_exploit       ; Windows KM driver bugs, EDR/anti-cheat evasion
  0x0004   call   vmi_and_anti_vm             ; virtual machine introspection, hide hypervisor artifacts
  0x0005   call   instrument_runtime          ; Frida, Detours, MinHook, Shadowhook, Dobby
  0x0006   call   android_kernel_fork         ; custom kernel builds, Zygisk, LSPosed, eBPF rootkits
  0x0007   call   build_tooling               ; mitmproxy / memflow based analysis frameworks
  0x0008   call   agentic_redteam             ; prompt injection, tool misuse, memory poisoning, multi-agent privesc
  0x0009   ret                                ; ship report. sleep never. the ring never sleeps either.
```

---

### `gef➤ checksec --file /var/run/github_telemetry`
```text
[*] RELRO:    Full RELRO
[*] Canary:   No canary found (VULNERABLE — yes, on purpose)
[*] NX:       NX enabled
[*] PIE:      PIE enabled
[*] Threat model coverage: NIST CSF+SP / ISO / PCI DSS / FSTEC / OWASP / MITRE ATT&CK
```

<p align="center">
  <img src="https://github-readme-streak-stats.herokuapp.com/?user=Reload3d&theme=hacker&hide_border=true&background=0D1117&ring=00ff00&fire=00ff00&currStreakNum=c9d1d9" alt="GitHub Streak" />
</p>

<p align="center">
  <img src="https://komarev.com/ghpvc/?username=Reload3d&label=MEMORY_LEAKS&color=00ff00&style=for-the-badge" alt="Profile Views" />
</p>

---

### `[root@Reload3d]~# objdump -d -M intel shellcode.bin`

```asm
shellcode.bin:     file format binary

Disassembly of section .data:

0000000000401000 <_drop_shell>:
  401000:	48 31 f6             	xor    rsi, rsi              ; rsi = 0
  401003:	56                   	push   rsi                   ; push null byte
  401004:	48 bf 2f 62 69 6e 2f 	movabs rdi, 0x68732f2f6e69622f ; '/bin//sh'
  40100b:	2f 73 68 
  40100e:	57                   	push   rdi                   ; push string to stack
  40100f:	48 89 e7             	mov    rdi, rsp              ; rdi points to '/bin//sh'
  401012:	48 31 c0             	xor    rax, rax              ; rax = 0
  401015:	b0 3b                	mov    al, 0x3b              ; syscall 59 (sys_execve)
  401017:	48 31 d2             	xor    rdx, rdx              ; rdx = 0
  40101a:	0f 05                	syscall                      ; trigger interrupt
  40101c:	cc                   	int3                         ; trap — the only word I still recognize as mine
```

<p align="center">
<code>
gef➤ quit<br>
[!] cannot detach: no boundary between debugger and debuggee<br>
[+] this was never a metaphor. it was a memory map.
5b10393819aea34cc388328ea95eab0efccd23163375597c57ff5f2432bfb23e
</code>
</p>
