# 🧭 CNO Track: Four-Course Learning Roadmap

**Goal:**  
Move from “barely write C” → “can write, exploit, and analyze real-world CNO tooling and malware”  
**Approach:**  
Logical sequencing, clear prerequisites, and practical overlap where it *accelerates* skill-building (not just adding workload).

---

## 🚦 Phase 1: C Programming Fundamentals (Weeks 1–12)
**Purpose:** Build strong language fundamentals and mental models for memory, pointers, and bugs.

- **Weeks 1–12:**  
  - Data types, variables, and scope  
  - Pointers and arrays  
  - Control flow, functions, recursion  
  - Memory management (`malloc`, `free`), stack vs heap  
  - Structs, arrays, enums  
  - File I/O basics  
  - Intro to function pointers and callbacks  
  - Debugging: `gdb`, `valgrind`, `objdump`  
  - Safe coding and C “gotchas”  
  - Weekly labs: bugs, buffer overflows, walkthroughs of binary/disassembly

**🏁 Deliverable:**  
A small C app with both intended bugs (buffer overflow, etc.) and a write-up mapping source to binary.

---

## 🚦 Phase 2: Systems Programming (Weeks 13–24)
**Purpose:** Use C to interact with the operating system directly — processes, memory, files, signals, threads, and *intro to sockets*.

- **Weeks 13–24:**  
  - System calls: `fork`, `exec`, `wait`, `open`, `read`, `write`, `mmap`, `signal`, etc.  
  - File descriptors, pipes, `/proc`  
  - Memory management at syscall level  
  - Process creation and management  
  - Signals and signal handling  
  - Threads (`pthread` basics), mutexes, race conditions  
  - **Sockets — Intro only:** 1–2 weeks on basics (`socket()`, TCP/UDP overview, simple client/server)  
  - Syscall tracing (`strace`), ELF basics, privilege escalation basics  
  - Weekly labs: mini shell, process tree, vulnerable syscall-based apps

**🏁 Deliverable:**  
A mini shell (with basic job control) or a syscall-heavy tool, with binary analysis (Ghidra/objdump).

---

## 🚦 Phase 3: Network Programming (Weeks 21–30) *(CAN OVERLAP with late Systems Prog!)*
**Purpose:** Specialize in writing secure, robust, and CNO-relevant network code.

- **Weeks 21–30:**  
  - Deep dive: `socket()`, `bind()`, `listen()`, `accept()`, `connect()`, `send()`, `recv()`  
  - Protocol engineering: TCP vs UDP, custom protocols  
  - Multi-client servers: `select()`, threads, non-blocking I/O  
  - Protocol fuzzing, bug finding, writing and patching exploits  
  - Traffic analysis (`tcpdump`, Wireshark), protocol documentation  
  - Security: buffer overflows in network code, info leaks, protocol confusion  
  - Capstone: full-featured chat server, RAT, or CNO tool with custom protocol

**🏁 Deliverable:**  
CNO-grade server/client pair (robust, well-documented, tested with traffic capture and vulnerability analysis).

---

## 🚦 Phase 4: Operating Systems (Weeks 31–44)
**Purpose:** Learn the **internals**: how the OS works, memory is managed, scheduling, filesystems, kernel security.

- **Weeks 31–44:**  
  - Kernel vs userland, system call flow  
  - Virtual memory, page tables, process isolation  
  - Scheduling, synchronization, semaphores  
  - Filesystem implementation (inode, ext4, FAT, journaling)  
  - Bootstrapping and OS initialization  
  - OS-level security mitigations (ASLR, SMEP, KASLR, stack guards)  
  - Kernel data structures, device drivers  
  - Build/modify a toy kernel (xv6 or similar), or write a basic kernel module

**🏁 Deliverable:**  
Trace and document a privilege escalation exploit, or add a syscall to a toy OS (and exploit/use it).

---

## 🏗️ Overlap and Integration Guide

### What can/should overlap?

- **C Programming → Systems Programming:**  
  - *No overlap at first* — finish C through pointers, memory, and structs before starting Systems Programming.
  - Start Systems Programming in **week 13**, once you’re comfortable writing non-trivial C code.

- **Systems Programming ↔ Network Programming:**  
  - *YES, overlap is recommended (not required):*  
    - **Weeks 21–24:** You’re finishing Systems Programming, and Network Programming starts.  
    - You should be comfortable with threads, signals, and syscalls before deep-diving into multiplexed or secure network code.
    - *Do both if you want to accelerate learning; otherwise, back-to-back is fine.*

- **Operating Systems:**  
  - *Should come last* (after Systems/Network), as it relies on you understanding how to *use* system features first.
  - Can begin capstone OS readings/projects during late Network Programming if you want a head start.

---

## 📅 Visual Sequence

| Weeks      | C Programming | Systems Programming | Network Programming | Operating Systems |
|------------|---------------|---------------------|--------------------|------------------|
| 1–12       | 🟩 Core       |                     |                    |                  |
| 13–20      | (review/adv)  | 🟩 Core             |                    |                  |
| 21–24      |               | 🟩 Final Labs       | 🟨 Start           |                  |
| 25–30      |               |                     | 🟩 Core            |                  |
| 31–44      |               |                     |                    | 🟩 Core          |

🟩 = Primary focus  
🟨 = Optional overlap (if workload manageable)

---

## 🗂️ Roadmap Summary Table

| Phase             | Weeks    | Pre-reqs         | Focus                | Can Overlap With      |
|-------------------|----------|------------------|----------------------|-----------------------|
| C Programming     | 1–12     | None             | Language, memory     | —                     |
| Systems Prog.     | 13–24    | C basics         | Syscalls, OS API     | Network Prog. (21–24) |
| Network Prog.     | 21–30    | C, basic syscalls| Sockets, protocols   | Late Systems Prog.    |
| Operating Systems | 31–44    | All above        | OS internals         | Late Network Prog.    |

---

## 🎯 Final Advice

- **Do NOT try to learn all four in parallel.**  
  - *C Programming* must come first (don’t start systems/networking without pointer confidence).
  - *Systems Programming* is a must before deep socket work — but a light socket intro there is fine.
  - *Network Programming* can start as you finish threads/signals/syscalls in Systems Programming.
  - *Operating Systems* is the capstone: do it last, as it synthesizes everything and lets you dive into kernel-level RE, exploit dev, and analysis.

- **Write-ups, labs, and code from each phase should “build into” the next.**  
  - E.g., your C chat server → syscalls and signals → network-enabled version → analyze with Ghidra → understand kernel interaction.

---

*Stick to the order and integration plan above for maximum real-world value in CNO/RE, exploit dev, and advanced security roles.*
