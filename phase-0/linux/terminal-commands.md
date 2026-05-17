# Terminal Commands (Conceptual Understanding)

## What a terminal is

The terminal is not the operating system itself. It is a program (shell) that interprets text input and runs other programs. When I type a command, I am not interacting directly with Linux. I am interacting with a shell that finds and launches programs.

---

## How commands work

When I type something like:

```bash
ls
```

The shell:
1. Reads the input
2. Searches for an executable file named "ls"
3. Looks in directories listed in the PATH environment variable
4. Runs the program as a separate process

---

## Key observation

Commands are not built into Linux as a single system. They are separate programs stored in the filesystem (often in /bin or /usr/bin).

---

## PATH concept

PATH is a list of directories the shell searches when I type a command. Without PATH, the shell would not know where to find programs unless I gave full file paths. 

---

## Important realization

The terminal is a command interpreter, not a system interface. It converts text into process execution.

---

### Commands

echo - displays back the text entered as a command in the terminal.

Command:
```bash
echo hello world
```
Output:
```bash
hello world
```

---

