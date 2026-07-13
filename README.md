# Data and Network Security Homework Archive

Course homework archive for **Data and Network Security, Spring 2026**. This
repository contains the selected implementation and write-up files for HW1 and
HW2, focused on binary exploitation, web security, side-channel attacks, and
cryptographic challenge analysis.

> Repository description: Data and Network Security homework solutions covering
> binary exploitation, web attacks, side-channel analysis, and cryptographic
> challenge exploitation.

## Contents

```text
.
├── HW1/
│   ├── exploits/      # C and Python exploit code for binary exploitation tasks
│   ├── scripts/       # QEMU helper scripts
│   └── report/        # HW1 theory/report PDF
├── HW2/
│   ├── web-security/  # XSS, CSRF, timing, websocket, and challenge exploits
│   └── reports/       # HW2 report PDF
└── docs/              # Original HW1/HW2 assignment PDFs
```

## HW1: Binary Exploitation

HW1 studies low-level exploitation techniques against vulnerable native
programs. The included exploit files demonstrate:

- Stack smashing with shellcode injection
- NOP sled construction
- Return-address overwrite
- Integer overflow assisted exploitation
- Frame-pointer and pointer manipulation
- ROP-style control-flow redirection
- Remote exploitation with `pwntools`

Relevant files:

- `HW1/exploits/xploit1.c` through `xploit5.c`
- `HW1/exploits/exploit2.py`
- `HW1/exploits/shellcode.h`
- `HW1/exploits/write_xploit.h`
- `HW1/scripts/run_qemu.sh`
- `HW1/scripts/ssh_to_qemu.sh`

## HW2: Web and Challenge Security

HW2 focuses on web vulnerabilities and challenge-style exploitation. The
included deliverables cover:

- Reflected XSS
- CSRF-based state-changing requests
- Timing side-channel password inference
- WebSocket/admin-bot exploitation
- Client-side payload delivery
- Recipe/job pipeline exploitation with a Python solver

Relevant files:

- `HW2/web-security/a.txt`
- `HW2/web-security/b.html`
- `HW2/web-security/g.txt`
- `HW2/web-security/exploit.html`
- `HW2/web-security/exploit.txt`
- `HW2/web-security/exploit.py`

## Running the Code

### HW1 C exploits

The C exploit files are designed for the original course VM and target binaries.
From `HW1/exploits`:

```sh
make
```

The generated exploit programs expect the vulnerable target binaries to be
installed in `/tmp` as in the course handout. `shellcode.S` is x86-64 Linux
assembly, so build it inside the course VM or another compatible x86-64 Linux
environment.

### HW1 QEMU helpers

From `HW1/scripts`:

```sh
./run_qemu.sh
./ssh_to_qemu.sh
```

The original VM disk image is intentionally not included in this repository
because it is too large for normal GitHub usage.

### HW2 web payloads

The HTML, JavaScript, and Python payloads are intended for the controlled
course/lab environment. Public endpoint URLs have been replaced with placeholder
domains in the GitHub version.

## Improvements Made Before Publishing

- Removed bulky generated artifacts and VM files.
- Removed `.DS_Store`, archives, virtual environments, and bundled dependencies.
- Replaced live/private exfiltration URLs with placeholder endpoints.
- Replaced a local hard-coded password in the public copy with an example value.
- Fixed undefined behavior in HW1 C code:
  - `xploit5.c` now uses `memset()` for the NOP sled instead of copying 512
    bytes from a one-byte string.
  - `xploit1.c` now writes the return address from a `uint64_t` value instead
    of copying eight bytes from a short byte string.
  - `xploit3.c` now includes the standard headers required for `malloc`,
    `sprintf`, `perror`, `fprintf`, and `stderr`.

## Known Limitations

- The exploit offsets and addresses are environment-specific and may need to be
  recalculated on a different VM, libc, binary build, or ASLR setting.
- The HW1 native exploits require the original target binaries and course VM.
- HW2 payloads are educational and should only be run in an authorized lab
  environment.
- The original VM image, virtualenv, generated LaTeX intermediates, and
  submission archives are not included.

## Ethics and Scope

This repository is for coursework and educational review only. The payloads and
exploits are meant for systems provided by the course staff or local controlled
test environments. Do not use them against systems without explicit permission.

## Course Context

Implemented for the **Data and Network Security** course at Sharif University
of Technology, Spring 2026.
