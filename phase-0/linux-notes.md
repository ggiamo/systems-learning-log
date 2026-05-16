# Linux notes

## Virtual Machine Observation
The Ubuntu VM behaves like a separate computer despite running inside my host operating system. Ubuntu inside the VM has its own filesystem, processes, memory space, and virtual hardware. The VM exists in an isolated environment that can be reset using snapshots if something breaks.
---
## NAT Networking Observation
The VM network adapter is configured to use NAT. NAT allows the VM to access the internet while remaining hidden behind the host machine. The VM is not directly exposed on the local netwowrk like a bridged adapter would be. This reduces accidental exposure and creates a safer beginner environment.
---
## Linux Filesystem Observation
Linux organizes files beginning at the root directory '/'. Unlike Windows drive letters, Linux presents the filesystem as one unified hierarchy. Directories such as '/home', '/bin', and '/etc' each serve different system purposes.
---
## Terminal Observation
Commands typed into the terminal are executable programs. The shell interprets input, locates executables using the PATH environment variable, and launches processes. I initially assumed commands were built directly into Linux itself, but many commands are separate executable files stored in directories such as '/bin'.
---
## Git Observation
Git is a local version-control system. It tracks changes to files by storing repository history and metadata inside the hidden '.git' directory. GitHub is a separate online hosting platform that can store remote copies of Git repositories. A repository does not become public automatically. Files are only uploaded when commits are pushed to a remote repository.
---
## .gitignore Observation
A '.gitignore' file tells Git which files should not be tracked. This helps prevent temporary files, compiled binaries, cache files, and sensitive information from being committed into repository history. The file does not delete anything. It only tells Git to ignore matching files unless explicitly added.
---
## GCC Observation
GCC complies C source code into native machine code executables. The compilation process transforms human-readable source code into binaries that the CPU can execute directly. Compiled executables are different from scripts because the operating system can load and run them directly. 
---
## VS Code Observation
VS Code is a development environment and text editor. It edits files stored on disk but does not replace the Linux terminal or operating system. Git tracks changes made to files edited inside VS Code. 
---
## Current Understanding
At this stage I am learning: 
- Linux filesystem structure
- terminal navigation
- virtual machine isolation
- Git repositories
- local vs remote repositories
- compilation basics
- development environment workflow

The focus is becoming comfortable operating inside a Linux development environment rather than building advanced software yet.


## Git Workflow Concept

The standard Git workflow is:

Edit -> Stage -> Commit -> Push

---

### 1. Check repository status

git status

Shows what files have been modified, added, or are untracked

---

### 2. Stage changes

git add .

Adds all current changes in the directory to the staging area.

(You can also stage specific files:)
git add filename.md

### 3. Commit changes

git commit -m "your message here"

Creates a snapshot of the staged changes in local Git history.

Example:
git commit -m "add Phase 0 Linux notes"

### 4. Push to GitHub

git push

Uploads committed changes to the remote repository on GitHub.

---

### Key idea

Edit -> git add -> git commit -> git push

This separates:
- working changes (edit)
- selected snapshot (stage)
- saved history (commit)
- remote sync (push)

---

## Bash

Bash is a shell used to interact with Linux through terminal commands.

The shell:
- accepts user commands
- located executables
- starts programs
- displays output

Markdown code blocks labeled with `bash` are only for syntax highling and do not execute commands themselves.

---

## Python Execution Test

Command:
python3 hello.py

Output:
hello world

Observation:
- Python executes scripts directly without compilation.
- The interpreter reads and executes code line-by-line.

---

## C Compilation Test

Command:
gcc hello.c -o hello

Run:
./hello

Output:
hello world

Observation:
- C is a compiled language.
- GCC converts source code into a binary executable.
- The executable must be explicitly run from the current directory.

---

## Interpretation vs Compilation

### Interpretation (Python example)
- Code is executed directly by an interpreter (e.g., `python3`)
- No separate build step is required
- Each line is read and executed at runtime

Example:
```bash
python 3 hello.py
```

Observation: The interpreter processes the source code directly and runs it immediately.

### Compilation (C example)
- Source code is translated into machine code before execution
- Requires a compiler (e.g., gcc)
- Produces an executable file that runs independently

Example:
```bash
gcc hello.c -o hello
./hello
```

Observation:
- The compiler converts the source code into a binary executable first.
- The resulting program runs as a standalone file.

Key Difference:
- Interpretation: execution happens during reading of source code
- Compilation: execution happens after translation into machine code