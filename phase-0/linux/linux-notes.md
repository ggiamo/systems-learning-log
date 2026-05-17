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

---


## Git Workflow Concept

The standard Git workflow is:

Edit -> Stage -> Commit -> Push

---

### 1. Check repository status

```bash
git status
```

Shows what files have been modified, added, or are untracked

---

### 2. Stage changes

```bash
git add .
```

Adds all current changes in the directory to the staging area.

(You can also stage specific files:)
git add filename.md

### 3. Commit changes

```bash
git commit -m "your message here"
```

Creates a snapshot of the staged changes in local Git history.

Example:
git commit -m "add Phase 0 Linux notes"

### 4. Push to GitHub

```bash
git push
```

Uploads committed changes to the remote repository on GitHub.


### Key idea

Edit -> git add -> git commit -> git push

This separates:
- working changes (edit)
- selected snapshot (stage)
- saved history (commit)
- remote sync (push)

---

## Bash

A shell is a program that accepts commands and passes them to the operating system to execute. Bash is the default shell used to interact with most Linux distributions through terminal commands. Other shells such as ksh, zsh, and tsch exist.

The shell:
- accepts user commands
- locates executables
- starts programs
- displays output

Markdown code blocks labeled with `bash` are only for syntax highlighting and do not execute commands themselves.

---

## The Shell Prompt

When a terminal is opened, the shell prompt will appear. It will usually follow this format: 
```bash
username@hostname:current_directory$
```
The $ symbol indicates that the terminal is ready to accept commands. 

---

## The Directory Tree in Linux

Everything in Linux is treated like a file. These files are organized into a logical, branching hierarchy known as the Filesystem Hierarchy Standard (FHS).

The structure begins at a single point of origin called the root directory, represented by a forward slash (/). Every other folder and file branches out from this room, creating a tree-like architecture.

Common top-level directories include:
- `/bin`: Essential command binaries (short for "binary"; contains the fundamental executable programs like ls, cp, and bash that all users need).

- `/etc`: System-wide configuration files (et cetera; the central hub for system configuration files that dictate how the OS and applications behave).

- `/home`: Personal folders for users (the personal storage space where individual users keep their private documents, settings, and media).

- `/var`: Variable data like logs and temporary files (variable data; a location for files that change constantly during system operation, such has system logs and print spools).

---

A path is the specific "address" of a file or folder. It maps the sequence of directories you must traverse to reach a destination.

Example:
```bash
/home/user/Documents
```

- Starts at root (/)
- Moves into `home`
- Moves into `user`
- Ends at `Documents`

Path types:

Absolute path
- Starts at root `/`
- Independent of current location
- Example:
```bash
/home/user/systems-learning-log/phase-0/linux
```

Relative path
- Interpreted from current directory
- Depends on shell state
- Example:
```bash
linux/
```


---





## References

- Linux Journey -- https://labex.io/linuxjourney

- The Linux Command Line -- William Shotts

