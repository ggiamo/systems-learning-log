## Virtual Machine Model

A virtual machine behaves like a complete computer running inside another operating system.

Key properties:
- Separate filesystem
- Separate process table
- Isolated memory space
- Virtualized hardware devices

This isolation means:
- crashes are contained inside the VM
- snapshots allow full system rollback
- host system is unaffected by internal VM state

---

## Networking Model (NAT)

The VM uses NAT (Network Address Translation).

Behavior:
- VM shares host's network connection
- VM is not directly visible on the local network
- outbound connections are allowed
- inbound connections are restricted unless explicitly configured

Implication:
- safer default for experimentation
- reduced exposure compared to bridged networking

---

## Linux Filesystem Model

Linux uses a single hierarchical filesystem rooted at `/`.

Core principle:
- everything is part of one tree structure

Important clarification:
- directories are not "containers" in a physical sense
- they are mappings from names -> filesystem metadata (inodes)

Common system directories:
- `/bin` -> essential executable programs
- `/etc` -> system configuration files
- `/home` -> user-specific files and workspaces
- `/var` -> variable runtime data (logs, caches, system state)

---

## Path System

A path describes how to locate a file in the filesystem tree. 

Types:
- Absolute path -> starts at `/`, independent of location
- Relative path -> depends on current working directory

Example
- `/home/user/projects` -> absolute
- `projects/phase-0` -> relative

---

## Processes and Execution Model

A process is a running instance of a program.

When a program executes:

- it becomes a process
- it is assigned a PID (process ID)
- it receives its own memory space

Key property:
- processes are isolated from each other unless explicitly connected

Parent-child relationship:
- a shell creates child processes when launching commands

---

## Shell Model (Bash)

A shell is a user-space program that interprets commands.

Execution flow:
1. reads user input
2. determines command type (bultin or external binary)
3. resolves external commands using `PATH`
4. launches processes
5. returns output to terminal

Important distinction:
- a shell is not the same as an operating system
- a shell is an interface to OS process management

---

## PATH Resolution

PATH is an ordered list of directories.

When a command is typed:
- shell searches each directory PATH
- first matching executable is executed
- if none found -> "command not found"

---

## Build and Execution Pipeline (C)

C programs follow a compilation pipelie:

source code ->
preprocessing ->
compilation ->
assembly ->
linking ->
ELF binary ->
OS loader ->
process execution

Key idea:
- GCC is not execuring code; it produces an executable file

---

## Python Execution Model

Python is executed through an interpreter.

Pipeline:
source code ->
interpret parsing ->
bytecode generation ->
virtual machine execution

Key idea:
- code is executed at runtime, not precompiled into a standalone binary

---


## Git Model

Git is a distributed version control system.

Core states:
- working directory -> current files
- staging area -> selected changes
- commit history -> saved snapshots

Concept:
- commits represent snapshots of state, not just file saves

---

## .gitignore Behavior

A `.gitignore` file patterns for files Git should ignore.

Key properties:
- does not delete files
- only prevents tracking
- can be overriden by explicit git add





## References

- Linux Journey -- https://labex.io/linuxjourney

- The Linux Command Line -- William Shotts

