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

echo - one of the most basic and frequently used tools in the Linux terminal. Its primary function is to print text or variables to the standard output (usually your screen). 

Basic Usage: To display a simple string of text.

Command:
```bash
echo hello world
```
Output:
```bash
hello world
```

Printing Variables: It is often used to check the value of environment variables.

Command:
```bash
echo $USER
```
Output:
```bash
user
```

Creating Files: You can combine `echo` with redirection operators (>) to quickly create or overwrite a file with text.

Command:
```bash
echo "New log entry" > note.txt
```
Output:
- Nothing is printed to the terminal.
- 'echo "New log entry"' prints the text 'New log entry' to standard output.
- stdout = default output stream of a program; programs write output to stdout, not directly to the screen; terminal reads stdout and displays it
Normal data flow: program -> stdout -> terminal -> screen
With redirection: program -> stdout -> file
- `>` (redirection operator) redirects that output into a file instead of the terminal.
- `note.txt` is the target file (if `note.txt` does not exist then it is created; if `note.txt` already exists then it is overwritten completely which means that its previous contents are erased)

---

pwd ("print working directory") - outputs the absolute path (the full path starting from `/`) of your current location. It is a vital tool for ensuring you are running commands in the correct place.

Command:
```bash
pwd
```
Output:
```bash
/home/user/projects/systems-learning-log
```

---

cd ("change directory") - changes your current working directory.

Absolute path navigation:

Input:
```bash
cd ~/projects/systems-learning-log/phase-0/linux
pwd
```
Output:
```bash
/home/user/projects/systems-learning-log/phase-0/linux
```

Relative path navigation:

Input:
```bash
cd python/hello-world
pwd
cd ..
cd ..
cd linux/
pwd
```
Output:
```bash
/home/user/projects/systems-learning-log/phase-0/linux
```

