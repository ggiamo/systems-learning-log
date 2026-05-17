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

## Filesystem Operations Model

Linux filesystem behavior is driven by operations on directory entries and metadata rather than "files as objects".

Core operations:

- mkdir -> creates a directory entry mapping a name to inode metadata
- rm -> removes directory entry (data may persist until overwritten)
- cp -> creates a new inode with duplicated data
- mv -> changes directory entry reference (same inode, new path)

Most filesystem commands do not "modify files directly". They manipulate references (names -> inodes) or create new inodes.

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

## Standard Streams Model

Every process is connected to three defaul data streams:

- stdin -> input stream (keyboard / piped input)
- stdout -> output stream (terminal display / pipe output)
- stderr -> error output stream

Commands like:
cat, grep, find

operate primarily by reading from stdin or files and writing to stdout

Linux tools are designed to be chained using pipes rather than used in isolation.

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

## Command-Line Tool Behavior Model

Most Linux utilities follow a consistent behavioral pattern:

1. Accept input from:
- files
- stdin
- arguments

2. Process data in memory (stream-based or buffered)

3. Output results to stdout

Examples:

- cat -> streams file content
- grep -> filters lines matching patterns
- find -> traverses filesystem tree
- clear -> modifies terminal display buffer only

Linux commands are small composable programs designed for pipelines, not monolithic applications.

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

## Filesystem vs Git State Distinctin

Filesystem state and Git state are independent layers:

Filesystem:
- actual files and directories
- changes immediately reflect in disk state

Git:
- tracks snapshots of filesystem state
- only records changes when explicitly staged and committed

Creating, modifying, or deleting files does not affect Git history unless staged.

---

## .gitignore Behavior

A `.gitignore` file patterns for files Git should ignore.

Key properties:
- does not delete files
- only prevents tracking
- can be overridden by explicit git add


## File Timestamp Metadata

Linux filesystems track metadata associated with files.

Common timestamp categories:

access time (atime) -> last file read
modification time (mtime) -> last content modification
change time (ctime) -> last metadata change

touch primarily modifies timestamp metadata.

Important distinction:

updating timestamps does not necessarily modify file contents

---

## Core Behavioral Model of Linux

Linux can be understood as three interacting layers:

1. Filesystem layer
- directory entries
- inodes
- metadata (timestamps, permissions)

2. Process layer
- execution instances
- memory space
- PID-based isolation

3. Tool layer
- small programs operating on streams and files
- composable via pipes and redirection

Most "commands" are not system features--they are user-space programs interacting with these layers.

---


## References

- Linux Journey -- https://labex.io/linuxjourney

- The Linux Command Line -- William Shotts

