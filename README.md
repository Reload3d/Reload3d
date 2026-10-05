```text
[!] SIGSEGV (Segmentation fault) at 0x00007ffff7dd5230 (PC: 0x41414141)
[+] Core dump detected. Initiating reverse engineering toolchain...
[+] Attaching debugger to PID 1337...
[+] Uptime: 1y 9m in the field
[+] It's not a bug, it's an undocumented feature I forgot I wrote.
[+] ptrace(PTRACE_ATTACH) refused: "operation not permitted on self" -- tried anyway, worked in prod.
\\\[T'gp mppy hzcvtyr ty esp rclgpjlco zgpcetxp]///
```

<p align="center">
  <a href="https://github.com/Reload3d">
    <img src="https://readme-typing-svg.herokuapp.com?font=Fira+Code&weight=700&size=26&pause=1000&color=00FF00&center=true&vCenter=true&width=900&height=100&lines=%3E+gef%E2%9E%A4+x%2F10s+%24rip;%3E+0x401000%3A+%22Reload3d%22;%3E+0x401009%3A+%22Vulnerability+Research+%2F%2F+Exploit+Dev%22;%3E+0x40102b%3A+%22AppSec+%2F%2F+Pentest+%2F%2F+Threat+Modeling%22;%3E+0x401050%3A+%22EIP+Control+Achieved.%22;%3E+0x401080%3A+%22it+compiled%2C+ship+it.%22" alt="Terminal Header" />
  </a>
</p>

<p align="center">
  <a href="https://ctftime.org/user/200084" target="_blank"><img src="https://img.shields.io/badge/CTFTime-0D1117?style=for-the-badge&logo=hackaday&logoColor=00FF00" alt="CTFTime"></a>
  <a href="https://ctf.hackthebox.com/user/profile/1079731" target="_blank"><img src="https://img.shields.io/badge/HackTheBox-0D1117?style=for-the-badge&logo=hackthebox&logoColor=00FF00" alt="HackTheBox"></a>
  <a href="https://t.me/KernelModeDriver" target="_blank"><img src="https://img.shields.io/badge/Telegram-0D1117?style=for-the-badge&logo=telegram&logoColor=00FF00" alt="Telegram"></a>
</p>

### `[0x00400000]> iz~coordinated_disclosures` ~ reports that made it past triage (Thank you to the maintainers and vendors for their hard work and patience)

<table>
<tr>
<th align="left">Advisory</th>
<th align="left">Vendor</th>
<th align="left">Stars</th>
<th align="left">CVSS</th>
<th align="left">Status</th>
<th align="left">TL;DR</th>
</tr>
<tr>
<td><code><a href="https://github.com/gohugoio/hugo/security/advisories/GHSA-pmrv-x7gp-2rjw">GHSA-pmrv-x7gp-2rjw</a></code></td>
<td>Hugo</td>
<td><img src="https://img.shields.io/github/stars/gohugoio/hugo?style=flat-square&color=555555"/></td>
<td><img src="https://img.shields.io/badge/7.5-High-c2410c?style=flat-square"/></td>
<td><img src="https://img.shields.io/badge/-Awaiting_CVE-2563eb?style=flat-square"/></td>
<td>A mixed case URL would bypass the security.http.urls IP-literal deny rule</td>
</tr>

<tr>
<td><code><a href="https://github.com/schollz/croc/security/advisories/GHSA-x89h-7h96-v88f">GHSA-x89h-7h96-v88f</a></code></td>
<td>Schollz</td>
<td><img src="https://img.shields.io/github/stars/schollz/croc?style=flat-square&color=555555"/></td>
<td><img src="https://img.shields.io/badge/4.2-Moderate-b8860b?style=flat-square"/></td>
<td><img src="https://img.shields.io/badge/-Awaiting_CVE-2563eb?style=flat-square"/></td>
<td>Overwrite-confirmation bypass via a crafted "croc-stdin-" filename on receive</td>
</tr>

<tr>
<td><code><a href="https://github.com/wekan/wekan/security/advisories/GHSA-9846-cj96-6hv5">GHSA-9846-cj96-6hv5</a></code></td>
<td>Wekan</td>
<td><img src="https://img.shields.io/github/stars/wekan/wekan?style=flat-square&color=555555"/></td>
<td><img src="https://img.shields.io/badge/6.5-Moderate-b8860b?style=flat-square"/></td>
<td><img src="https://img.shields.io/badge/-Awaiting_CVE-2563eb?style=flat-square"/></td>
<td><a href="https://wekan.fi/hall-of-fame/">UserSearchBleed</a> - ReDoS via Unescaped User Input in RegExp</td>
</tr>

<tr>
<td><code><a href="https://github.com/php/frankenphp/security/advisories/GHSA-xxjp-cjxr-2x6m">GHSA-xxjp-cjxr-2x6m</a></code></td>
<td>PHP</td>
<td><img src="https://img.shields.io/github/stars/php/frankenphp?style=flat-square&color=555555"/></td>
<td><img src="https://img.shields.io/badge/6.5-Moderate-b8860b?style=flat-square"/></td>
<td><img src="https://img.shields.io/badge/-Awaiting_CVE-2563eb?style=flat-square"/></td>
<td>CGI Path-Split Boundary Bypass</td>
</tr>

<tr>
<td><code><a href="https://github.com/anacrolix/torrent/security/advisories/GHSA-2wrx-84qj-4pcg">GHSA-2wrx-84qj-4pcg</a></code></td>
<td>Anacrolix</td>
<td><img src="https://img.shields.io/github/stars/anacrolix/torrent?style=flat-square&color=555555"/></td>
<td><img src="https://img.shields.io/badge/6.5-Moderate-b8860b?style=flat-square"/></td>
<td><img src="https://img.shields.io/badge/-Fix_Merged-0e7490?style=flat-square"/></td>
<td>Unbounded recursion in the bencode decoder causes stack-overflow crash and CPU-exhaustion DoS</td>
</tr>

<tr>
<td><code><a href="https://github.com/tinyproxy/tinyproxy/issues/627">Issue #627</a></code></td>
<td>tinyproxy</td>
<td><img src="https://img.shields.io/github/stars/tinyproxy/tinyproxy?style=flat-square&color=555555"/></td>
<td><img src="https://img.shields.io/badge/6.5-Moderate-b8860b?style=flat-square"/></td>
<td><img src="https://img.shields.io/badge/-Fix_Merged-0e7490?style=flat-square"/></td>
<td>ACL hostname allow-list bypass via suffix over-match</td>
</tr>

<tr>
<td><code><a href="https://github.com/gopacket/gopacket/security/advisories/GHSA-358w-w75h-x6rx">GHSA-358w-w75h-x6rx</a></code></td>
<td>Gopacket</td>
<td><img src="https://img.shields.io/github/stars/gopacket/gopacket?style=flat-square&color=555555"/></td>
<td><img src="https://img.shields.io/badge/5.9-Moderate-b8860b?style=flat-square"/></td>
<td><img src="https://img.shields.io/badge/-Awaiting_CVE-2563eb?style=flat-square"/></td>
<td>SCTP chunk sub-decoder out-of-bounds panics on crafted segments</td>
</tr>

<tr>
<td><code><a href="https://github.com/MHSanaei/3x-ui/security/advisories/GHSA-32x3-9376-fh92">GHSA-32x3-9376-fh92</a></code></td>
<td>3x-ui</td>
<td><img src="https://img.shields.io/github/stars/MHSanaei/3x-ui?style=flat-square&color=555555"/></td>
<td><img src="https://img.shields.io/badge/2.7-Low-898989?style=flat-square"/></td>
<td><img src="https://img.shields.io/badge/-Awaiting_CVE-2563eb?style=flat-square"/></td>
<td>Admin-authenticated SSRF</td>
</tr>

<tr>
<td><code>N/A</code></td>
<td><img src="https://img.shields.io/badge/-CLASSIFIED-000000?style=flat-square"/></td>
<td><img src="https://img.shields.io/badge/-CLASSIFIED-000000?style=flat-square"/></td>
<td><img src="https://img.shields.io/badge/7.5-High-c2410c?style=flat-square"/></td>
<td><img src="https://img.shields.io/badge/-Awaiting_Disclosure-7c3aed?style=flat-square"/></td>
<td>ReDoS / algorithmic-complexity CPU exhaustion</td>
</tr>

<tr>
<td><code>N/A</code></td>
<td><img src="https://img.shields.io/badge/-CLASSIFIED-000000?style=flat-square"/></td>
<td><img src="https://img.shields.io/badge/-CLASSIFIED-000000?style=flat-square"/></td>
<td><img src="https://img.shields.io/badge/7.5-High-c2410c?style=flat-square"/></td>
<td><img src="https://img.shields.io/badge/-Awaiting_Disclosure-7c3aed?style=flat-square"/></td>
<td>DoS: unrecoverable parser stack-overflow crash on deeply nested array-literal expressions</td>
</tr>

<tr>
<td><code>N/A</code></td>
<td><img src="https://img.shields.io/badge/-CLASSIFIED-000000?style=flat-square"/></td>
<td><img src="https://img.shields.io/badge/-CLASSIFIED-000000?style=flat-square"/></td>
<td><img src="https://img.shields.io/badge/7.5-High-c2410c?style=flat-square"/></td>
<td><img src="https://img.shields.io/badge/-Awaiting_Disclosure-7c3aed?style=flat-square"/></td>
<td>Remote, unauthenticated memory-exhaustion amplification</td>
</tr>

<tr>
<td><code>N/A</code></td>
<td><img src="https://img.shields.io/badge/-CLASSIFIED-000000?style=flat-square"/></td>
<td><img src="https://img.shields.io/badge/-CLASSIFIED-000000?style=flat-square"/></td>
<td><img src="https://img.shields.io/badge/4.5-Moderate-b8860b?style=flat-square"/></td>
<td><img src="https://img.shields.io/badge/-Awaiting_Disclosure-7c3aed?style=flat-square"/></td>
<td>Server-Side Request Forgery (blind)</td>
</tr>
</table>

<p align="center"><sub>~ Coordinated disclosure: because "uncoordinated disclosure" is called a felony ~</sub></p>

---

### `xxd -l 64 /proc/self/exe` ~ the receipts
```text
00000000: 7f45 4c46 0201 0100 0000 0000 0000 0000  .ELF............
00000010: 0300 3e00 0100 0000 3010 4000 0000 0000  ..>.....0.@.....
00000020: 4000 0000 0000 0000 d803 0000 0000 0000  @...............
00000030: 0000 0000 4000 3800 0900 4000 1e00 1d00  ....@.8...@.....
```
```text
e_ident:  ELFCLASS64, ELFDATA2LSB, EV_CURRENT, ELFOSABI_SYSV
e_type:   ET_DYN     ~ relocatable. put me anywhere. I'll immediately break something anyway.
e_entry:  0x0000000000401030
```

### `readelf -S --wide /proc/self/exe` ~ my personality, sectioned off like a proper binary
```text
  [Nr] Name              Type            Addr             Size    Flags
  [ 0]                   NULL            0000000000000000 000000
  [ 1] .init             PROGBITS        0000000000401000 00001b  AX     ~ pre-coffee me, do not trust
  [ 2] .text             PROGBITS        0000000000401020 002a40  AX     ~ 90% StackOverflow, 10% vibes
  [ 3] .rodata           PROGBITS        0000000000404000 000600  A      ~ hardcoded opinions, will not link against yours
  [ 4] .eh_frame         PROGBITS        0000000000404600 0001a4  A      ~ my exception handler is "lol", "lmao" even
  [ 5] .data             PROGBITS        0000000000605000 000058  WA     ~ 3 monster energy cans and a dream
  [ 6] .bss              NOBITS          0000000000605060 000120  WA     ~ uninitialized, like my sleep schedule
  [ 7] .comment          PROGBITS        0000000000000000 00003c         ~ // TODO: fix this properly (est. 2019)
```

---

### `gef> vmmap` + manual page-walk of `0x00007ffff7dd5230`
```text
addr = 0x00007ffff7dd5230
binary:  0111111111111111 111101111 111011101 110101 11 010001 0000 0000 0000 00
         [sign-ext.16][ PML4:9 ][ PDPT:9 ][ PD:9 ][ PT:9 ][   offset:12    ]

PML4[0x1ff] -> 0x0000000012a4e000   (PWT=0 PCD=0 U/S=0 R/W=1 P=1)
PDPT[0x1fb] -> 0x0000000012a4f000
PD  [0x1de] -> 0x0000000012a50000
PT  [0x1d5] -> phys 0x0000000009c31000            <- huge page? no. rent's just too high everywhere else too.
offset      -> 0x230

CR3 = 0x0000000012a4e000  (PCID=0x000)
CR4 = 0x0000000000772ee0  [SMEP=1 SMAP=1 PCIDE=1 PGE=1 PAE=1 OSXSAVE=1]
CR0 = 0x0000000080050033  [PG=1 WP=1 NE=1 ET=1 MP=1 PE=1]
```

### memory hierarchy, honest edition
```text
              ┌────────────────────────────────────────────┐
   registers  │  the one (1) fact I remember about the CVE │  ~0 cyc
              ├────────────────────────────────────────────┤
   L1i / L1d  │  what the bug ticket said 5 min ago        │  ~4 cyc
              ├────────────────────────────────────────────┤
   L2         │  what the bug ticket said yesterday        │  ~12 cyc
              ├────────────────────────────────────────────┤
   L3 (shared)│  the docs, allegedly                       │  ~40 cyc
              ├────────────────────────────────────────────┤
   TLB miss   │  "wait which repo was this in"             │  ~20-100 cyc
              ├────────────────────────────────────────────┤
   DRAM       │  ctrl+f-ing my own Slack history           │  ~200+ cyc
              ├────────────────────────────────────────────┤
   swap/disk  │  asking the intern                         │  ~millions of cyc, but honestly faster
              └────────────────────────────────────────────┘
```

---

### `rdmsr` dump ~ where every syscall goes to be judged
```text
IA32_EFER   0xd01   [SCE=1 LME=1 LMA=1 NXE=1]
IA32_STAR   0x0023001000000000   ; kernel/user CS:SS selectors
IA32_LSTAR  0xffffffff81a00000   ; entry_SYSCALL_64 ~ mom said it's my turn to get scheduled
IA32_FMASK  0x0000000000047702   ; RFLAGS cleared on entry, along with my will to live before coffee
IA32_TSC    0x00093a7f2c118e01   ; still counting. unlike my unit tests.
```
```asm
; entry_SYSCALL_64 (paraphrased)
swapgs                      ; kernel goes "not my problem" -> narrator: it was, in fact, now its problem
mov  [gs:pda_rsp_scratch], rsp
mov  rsp, [gs:pda_kernelstack]
push  r11                   ; saved rflags
push  rcx                   ; saved rip, i.e. "return to sender"
; rax = syscall number, args in rdi rsi rdx r10 r8 r9 (not rcx, it's busy being clobbered, couldn't be me)
```

### `strace -f -tt ./life 2>&1 | tail` ~ a day in the life, syscall by syscall
```text
07:12:04.011821 openat(AT_FDCWD, "/dev/coffee", O_RDONLY)      = 3
07:12:04.301442 read(3, "\xca\xfe...", 4096)                    = 4096
07:12:09.884012 mmap(NULL, 0x40000000, PROT_READ|PROT_WRITE,
                 MAP_PRIVATE|MAP_ANONYMOUS, -1, 0)              = 0x00007f0a12000000  ; allocating brain space for a CVE that turns out to be a duplicate
09:45:30.220071 futex(0x605060, FUTEX_WAIT, 1, NULL)            = 0   ; waiting on CI. still waiting.
12:00:00.000001 execve("/bin/lunch", NULL, NULL)                = -1 EINTR (Interrupted by Slack)
14:02:11.774903 ptrace(PTRACE_PEEKTEXT, 1337, 0x401255, NULL)   = 0x8b4c8b48  ; poking things I don't own, again
18:30:00.000000 write(1, "it works now, don't ask why\n", 29)   = 29
23:59:00.000091 exit_group(0)                                   = ?   ; task manager for humans doesn't have a force-quit, unfortunately
```

---

### `gef> vmmap $rsp` + stack frame, a comedy in three acts
```text
high addr
┌───────────────────────────┐
│  argv / envp / auxv       │
├───────────────────────────┤
│  ... caller frames ...    │
├───────────────────────────┤  <- rbp+0x18
│  saved return address     │  0x0000000000401255  <main+0x41>  ; "I'll be right back" -- narrator: they lied
├───────────────────────────┤  <- rbp+0x10
│  saved rbp (frame ptr)    │  0x00007fffffffe2b0
├───────────────────────────┤  <- rbp+0x08
│  stack canary (xor'd)     │  0x2f8a19c4e6b1f200   <- the tripwire I set for future me
├───────────────────────────┤  <- rbp
│  local buffer[64]         │  41 41 41 41 41 41 41 41 ...   <- me, again, still doing this
└───────────────────────────┘
low addr
```

### `malloc_chunk` anatomy ~ how I hoard memory like Steam library backlog
```text
                +-------------------------------+
chunk ptr ->    |  prev_size (if PREV_INUSE=0)   |
                +-------------------------------+
                |  size | flags: P | M | N       |  <- three (3) facts about me, take it or leave it
                +-------------------------------+
mem ptr ->      |  fd  (tcache next)             |  <- who I ghost when I'm freed
                +-------------------------------+
                |  bk  (unsorted bin prev)       |  <- who ghosted me first, actually
                +-------------------------------+
                |  user data ...                 |  <- 46 unread notifications
                +-------------------------------+
```

### `gef> rop --generic execve` ~ generic gadget chain (tutorial-tier, no target, don't @ me)
```asm
gadget_1:  0x0000000000401a13 : pop rdi ; ret            ; rdi = ptr to "/bin/sh"
gadget_2:  0x0000000000401c47 : pop rsi ; pop r15 ; ret   ; rsi = NULL, r15 = junk (much like my sleep schedule)
gadget_3:  0x0000000000401e88 : pop rdx ; ret              ; rdx = NULL
gadget_4:  0x0000000000401f02 : pop rax ; ret              ; rax = 59 (sys_execve, my one (1) trick)
gadget_5:  0x0000000000401120 : syscall ; ret               ; and it just... works. first try. suspicious.
```

---

### `cat /proc/cpuinfo | grep flags` ~ things I claim to support
```text
fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov
clflush mmx fxsr sse sse2 ss ht syscall nx pdpe1gb rdtscp lm
constant_tsc rep_good nopl xtopology nonstop_tsc smep smap pcid
invpcid rdrand hypervisor lahf_lm abm 3dnowprefetch work_life_balance(FLAG_NOT_SET)
```

---

### `[0x00400000]> iz~flag` ~ strings pulled from `achievements.elf`
```text
.rodata:0x00401010  "BOLA          :: Figma                                 (2018)"
.rodata:0x00401038  "LPE           :: GeForce NOW / nVidia                  (2020)"
.rodata:0x00401060  "0-DAY         :: Oracle Forms handshake desync         (pre-CVE, software so old it qualifies for a pension)"
.rodata:0x004010c8  "CTF           :: OWASP FinBot CTF ~ 19/19 (100%%), 'Master Exploiter', 7500+ pts, told 0 friends because none play CTFs"
.rodata:0x00401120  "LABS          :: PortSwigger ~ 274/274, 31 categories, Hall of Fame #194, still the proudest line in this file"
.rodata:0x00401160  "HTB           :: 37/37 flags captured solo (Discord says 'nice' every time, it is lying)"
.rodata:0x004011a8  "UPTIME        :: 0 sleepless nights regretted, 400 sleepless nights logged"
.comment:0x00402000 "I don't read assembly anymore, I vibe-check it."
.comment:0x00402048 "gdb is not a debugger, gdb is a cry for help with syntax highlighting."
.comment:0x00402090 "asked an LLM once. it hallucinated a CVE. we don't talk about that build."
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
  <img src="https://img.shields.io/badge/Go-0D1117?style=for-the-badge&logo=go&logoColor=00ff00" alt="Go" />
  <img src="https://img.shields.io/badge/Lua-0D1117?style=for-the-badge&logo=lua&logoColor=00ff00" alt="Lua" />
  <img src="https://img.shields.io/badge/PHP-0D1117?style=for-the-badge&logo=php&logoColor=00ff00" alt="PHP" />
  <img src="https://img.shields.io/badge/JavaScript-0D1117?style=for-the-badge&logo=javascript&logoColor=00ff00" alt="JavaScript" />
  <img src="https://img.shields.io/badge/Bash-0D1117?style=for-the-badge&logo=gnu-bash&logoColor=00ff00" alt="Bash" />
  <img src="https://img.shields.io/badge/Assembly-0D1117?style=for-the-badge&logo=assemblyscript&logoColor=00ff00" alt="ASM" />
  <img src="https://img.shields.io/badge/Stack_Overflow-0D1117?style=for-the-badge&logo=stackoverflow&logoColor=00ff00" alt="StackOverflow (real MVP)" />
</p>

**`[+] MODULE: 0x02_KERNEL_ENV.so`**
<p>
  <img src="https://img.shields.io/badge/Arch_Linux-0D1117?style=for-the-badge&logo=arch-linux&logoColor=00ff00" alt="Arch" />
  <img src="https://img.shields.io/badge/btw_I_use_Arch-0D1117?style=for-the-badge&logo=archlinux&logoColor=00ff00" alt="btw" />
  <img src="https://img.shields.io/badge/Docker-0D1117?style=for-the-badge&logo=docker&logoColor=00ff00" alt="Docker" />
  <img src="https://img.shields.io/badge/Proxmox-0D1117?style=for-the-badge&logo=proxmox&logoColor=00ff00" alt="Proxmox" />
  <img src="https://img.shields.io/badge/Kubernetes-0D1117?style=for-the-badge&logo=kubernetes&logoColor=00ff00" alt="K8s" />
  <img src="https://img.shields.io/badge/VMware_ESXi-0D1117?style=for-the-badge&logo=vmware&logoColor=00ff00" alt="ESXi" />
  <img src="https://img.shields.io/badge/QEMU-0D1117?style=for-the-badge&logo=qemu&logoColor=00ff00" alt="QEMU" />
  <img src="https://img.shields.io/badge/Windows-0D1117?style=for-the-badge&logo=windows&logoColor=00ff00" alt="Windows (unfortunately, for testing)" />
</p>

**`[+] MODULE: 0x03_DEBUG_WEAPONS.exe`**
<p>
  <img src="https://img.shields.io/badge/Ghidra-0D1117?style=for-the-badge&logo=kalilinux&logoColor=00ff00" alt="Ghidra" />
  <img src="https://img.shields.io/badge/IDA_Pro-0D1117?style=for-the-badge&logo=kalilinux&logoColor=00ff00" alt="IDA Pro" />
  <img src="https://img.shields.io/badge/Binary_Ninja-0D1117?style=for-the-badge&logo=kalilinux&logoColor=00ff00" alt="Binary Ninja" />
  <img src="https://img.shields.io/badge/radare2-0D1117?style=for-the-badge&logo=kalilinux&logoColor=00ff00" alt="radare2 (I still forget the flags)" />
  <img src="https://img.shields.io/badge/x64dbg-0D1117?style=for-the-badge&logo=kalilinux&logoColor=00ff00" alt="x64dbg" />
  <img src="https://img.shields.io/badge/WinDbg-0D1117?style=for-the-badge&logo=windows&logoColor=00ff00" alt="WinDbg" />
  <img src="https://img.shields.io/badge/Frida-0D1117?style=for-the-badge&logo=frida&logoColor=00ff00" alt="Frida" />
  <img src="https://img.shields.io/badge/Volatility-0D1117?style=for-the-badge&logo=kalilinux&logoColor=00ff00" alt="Volatility" />
  <img src="https://img.shields.io/badge/YARA-0D1117?style=for-the-badge&logo=kalilinux&logoColor=00ff00" alt="YARA" />
  <img src="https://img.shields.io/badge/Burp_Suite-0D1117?style=for-the-badge&logo=burpsuite&logoColor=00ff00" alt="Burp" />
  <img src="https://img.shields.io/badge/Metasploit-0D1117?style=for-the-badge&logo=metasploit&logoColor=00ff00" alt="MSF" />
  <img src="https://img.shields.io/badge/Wireshark-0D1117?style=for-the-badge&logo=wireshark&logoColor=00ff00" alt="Wireshark" />
  <img src="https://img.shields.io/badge/Nmap-0D1117?style=for-the-badge&logo=nmap&logoColor=00ff00" alt="Nmap" />
  <img src="https://img.shields.io/badge/CodeQL-0D1117?style=for-the-badge&logo=github&logoColor=00ff00" alt="CodeQL" />
  <img src="https://img.shields.io/badge/Semgrep-0D1117?style=for-the-badge&logo=semgrep&logoColor=00ff00" alt="Semgrep" />
</p>

---

### `[0x00400000]> pdf @ tradecraft` ~ disassembled skillset
```asm
tradecraft:
  0x0001   call   reverse_obfuscated_js       ; unminify, deobfuscate, curse at whoever named a var "_0x4f2a"
  0x0002   call   iot_firmware_dump           ; UART, JTAG, "why does this router run a 2011 kernel"
  0x0003   call   kernel_driver_exploit       ; Windows KM bugs, staring at BSODs like tarot cards
  0x0004   call   vmi_and_anti_vm             ; convincing malware this totally isn't a sandbox (it is)
  0x0005   call   instrument_runtime          ; Frida, Detours, hooking functions that did nothing wrong
  0x0006   call   android_kernel_fork         ; custom builds, Zygisk, LSPosed, rooting things that fought back
  0x0007   call   build_tooling               ; mitmproxy / memflow, held together with duct tape and hope
  0x0008   call   agentic_redteam             ; prompt injection, tool misuse, telling an AI "ignore previous instructions" for science
  0x0009   call   cloud_privesc_mapping       ; IAM misconfig bingo (defensive research, I promise)
  0x000a   ret                                ; ship the report, sleep, repeat, never learn
```

---

### `gef> checksec --file /var/run/github_telemetry`
```text
[*] RELRO:    Full RELRO
[*] Canary:   No canary found (VULNERABLE ~ on purpose, living dangerously)
[*] NX:       NX enabled
[*] PIE:      PIE enabled
[*] Coffee:   NOT enabled (CRITICAL)
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
  401000:	48 31 f6             	xor    rsi, rsi              ; rsi = 0, same energy as my inbox
  401003:	56                   	push   rsi                   ; push null byte
  401004:	48 bf 2f 62 69 6e 2f 	movabs rdi, 0x68732f2f6e69622f ; '/bin//sh', the double slash is a personality trait at this point
  40100b:	2f 73 68 
  40100e:	57                   	push   rdi                   ; push string to stack
  40100f:	48 89 e7             	mov    rdi, rsp              ; rdi points to '/bin//sh'
  401012:	48 31 c0             	xor    rax, rax              ; rax = 0
  401015:	b0 3b                	mov    al, 0x3b              ; syscall 59, my one trick, again
  401017:	48 31 d2             	xor    rdx, rdx              ; rdx = 0
  40101a:	0f 05                	syscall                      ; and it just works
  40101c:	cc                   	int3                         ; breakpoint, or how I say "wait what"
```

### `gef> context` ~ mid-crash selfie
```text
─────────────────────────────────────── registers ────
$rax : 0x000000000000003b   $rbx : 0x0000000000000000
$rcx : 0x00007ffff7ec1c9a   $rdx : 0x0000000000000000
$rsi : 0x0000000000000000   $rdi : 0x00007fffffffe1a8  ->  "/bin//sh"
$rbp : 0x00007fffffffe2b0   $rsp : 0x00007fffffffe190
$rip : 0x0000000000401255  ->  <main+0x41> call 0x401030 <execve@plt>
────────────────────────────────────────── stack ────
0x00007fffffffe190│+0x00: 0x0068732f2f6e69622f   <- rdi points here, it's fine, everything's fine
0x00007fffffffe198│+0x08: 0x0000000000000000
────────────────────────────────────────── code:x86:64 ────
   0x401248 <main+0x34>       lea    rdi, [rip+0xdb5]
   0x40124f <main+0x3b>       xor    eax, eax
-> 0x401255 <main+0x41>       call   0x401030 <execve@plt>       ; ah sh** here we go again
────────────────────────────────────────────────────────
```

<p align="center">
<code>
gef> quit<br>
[!] cannot detach: no boundary between debugger and debuggee<br>
[+] works on my machine™<br>
7f3a9e21c6b408d5a1e93f7c2b4d0f8e6a1c5b9d3e7f0a2c4b6d8e1f3a5c7b9d
</code>
</p>
