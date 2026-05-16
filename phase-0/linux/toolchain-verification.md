# Toolchain Verification

## What is a Toolchain?

A development toolchain is the collection of tools used to:

- write code
- compile programs
- debug software
- manage source code

Current installed tools:

- Python 3
- GCC
- Git
- GDB

These tools form the foundation for later systems programming and reverse engineering work.

---

## Python

Python is an interpreter. It runs code line-by-line at runtime instead of producing a compiled binary. This allows faster testing but hides some low-level execution details.

---

## GCC (C Compiler)

GCC converts C source code into machine code. 

Process:
1. Source code (human readable)
2. Compilation
3. Machine code executable

The output is a file the CPU can run directly.

---

## Git

Git is a version control system. It tracks changes over time using commits. Each commit is a snapshot of the project state, not just a file backup.

---

## GDB

GDB is a debugger. 

It allows inspection of a program while it is running: 
- memory
- variables
- execution flow
- stack frames

This is essential for understanding program behavior and crashes.

---

## Key insight

Each tool in the toolchain operates at a different level:

- Python -> high-level execution
- GCC -> translation to machine code
- Git -> history tracking
- GDB -> runtime inspection

Together they form the workflow for systems-level development.

---

## Python Verfication

Command:
```bash
python3 --version
```

Output:
```bash
Python 3.14.4
```

What I Observed:
- Python is already installed on the system.
- Running `python3` from the termial works because the executable is in the PATH environment variable.
- The shell searches system directories to find the executable automatically.

---

## GCC

Command:
```bash
gcc --version
```

Output:
```bash
gcc (Ubuntu 15.2.0-16ubuntu1) 15.2.0
```

What I Observed:
- GCC is the C compiled installed on the system.
- The compiled converts C source code into machine code executables.
- The command line can access GCC globally through PATH.

---

## Git

Command:
```bash
git --version
```

Output:
```bash
git version 2.53.0
```

What I Observed:
- Git is installed and functioning correctly.
- Git tracks file changes and commmit history.
- Commit history can document conceptual progess over time.

---

## GDB

Command:
```bash
gdb --version
```

Output:
```bash
GNU gdb (Ubuntu 17.1-2ubuntu1) 17.1
```

What I Observed:
- GDB is installed successfully.
- GDB allows inspection of running programs.
- This tool will later help analyze crashed, memory, and execution flow.

---

## PATH

Command:
```bash
echo $PATH
```

Output: 
```bash
/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/local/games:/snap/bin:/snap/bin
```

What I Observed:
- PATH contains directories searched by the shell.
- Commands work without full paths because the shell searches these directories automatically.