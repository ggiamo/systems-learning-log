# Toolchain Verification

## Purpose of toolchain

A toolchain is a set of programs used to build, run, and debug software.

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