## Working context
- all commands are executed inside:

```bash
~/projects/systems-learning-log/phase-0
```

---

**`pwd` - current location**

Input:
```bash
pwd
```

Output:
```bash
/home/user/projects/systems-learning-log/phase-0
```

Observation:

- Displays the absolute path of the current working directory

---

**`cd` - directory navigation**

Input:
```bash 
cd linux
pwd
```

Output:
```bash
/home/user/projects/systems-learning-log/phase-0/linux
```

Observation:

- Changes process working directory; does not modify filesystem structure

---

**`ls` - directory listing**

Input:
```bash
ls
```

Output:
```bash
c
linux
python
```

Observation:

- Shows visible entries in the current directory


**`ls -l` - detailed listing ("long")**

Input:
```bash
ls -l linux
```

Output:
```bash
-rw-r--r-- linux-notes.md
-rw-r--r-- terminal-commands.md
-rw-r--r-- toolchain-verification.md
-rw-r--r-- vm-setup.md
```

Observation:

- Displays file metadata including permissions and file names


**`ls -a` - include hidden files ("all")**

Input:
```bash
ls -a linux
```

Output:
```bash
.
..
linux-notes.md
terminal-commmands.md
toolchain-verification.md
vm-setup.md
```

Observation:

- Include hidden directory entries:
`.` current directory
`..` parent directory


**`ls -la` - combined view**

Input:
```bash
ls -la linux
```

Output:
```bash
drwxr-xr-x .
drwxr-xr-x ..
-rw-r--r-- linux-notes.md
-rw-r--r-- terminal-commands.md
-rw-r--r-- toolchain-verification.md
-rw-r--r-- vm-setup.md
```

Observation:

- Combines:
detailed metadata (`-l`)
hidden entries (`a`)

---

**`echo` - output to stdout**

Input:
```bash
echo "hello world"
```

Output:
```bash
hello world
```

Observation:
- Writes text to standard output stream

---

PATH resolution check (conceptual command behavior)

Input:
```bash
ls
```

Observation:

- Shell behavior:
resolves `ls` using PATH
executes external binary
runs as a separate process

---

**Git Status**

Input:
```bash
git status
```

Output:
```bash
On branch main
nothing to commit, working tree clean
```

Observation:

- Displays repository state and uncommitted changes

---

**Git staging and commit**

Input:
```bash
git add .
git commit -m "phase 0 update"
```

Output:
```bash
[main abc123] phase 0 update
```

Observation:

- `git add` stages commit
- `git commit` records snapshot in history

---

**`touch` - create empty files / update timestamps**

Input:
```bash
touch sample.txt
```

Output:
(no terminal output)

Observation:

- Creates an empty file if it does not already exist. If the file already exists, updates file timestamps instead of replacing file contents.

Verification:
```bash
ls -l
```

Output:
```bash
-rw-r--r-- sample.txt
```

Observation:

- File now exists in current working directory.

**`touch` - create multiple files**

Input:
```bash
touch notes.txt trace.log output.data
```

Output:
(no terminal output)

Verification:
```bash
ls
```

Output:
```bash
c
linux
notes.txt
output.data
python
sample.txt
trace.log
```

Observation:

- `touch` accepts multiple file arguments and creates each file if missing

**`touch` on existing file - timestamp update**

Input:
```bash
ls -l sample.txt
touch sample-txt
ls -l sample.txt
```

Output:
```bash
-rw-r--r-- sample.txt
-rw-r--r-- sample.txt
```

Observation:

- Modification timestamp changes after runnign touch. File content remain unchanged.

**`touch -r` - reference timestamp copy**

Input:
```bash
touch -r sample.txt notes.txt
ls -l sample.txt notes.txt
```

Output:
```bash
-rw-r--r-- sample.txt
-rw-r--r-- notes.txt
```

Observation:

- Copies timestamp metadata from reference file to target file.

**touch -d - explicit timestamp assignment**

Input: 
```bash
touch -d "2023-01-01 12:30:00" trace.log
ls -l trace.log
```

Output: 
```bash
-rw-r--r-- trace.log
```

Observation:

- Assigns a specific modificatin timestamp instead of current system time.

---

**`mkdir` - create directories**

Input:
```bash
mkdir experiments
```

Output:
(no terminal output)

Verification:
```bash
ls
```

Output:
```bash
c
experiments
linux
notes.txt
output.data
python
sample.txt
trace.log
```

Observation:

- Creates a new directory entry in the current working directory.

**`mkdir -p` - nested path creation**

Input:
```bash
mkdir -p experiments/runtime/traces
```

Output:
(no terminal output)

Verification:
```bash
find experiments
```

Output:
```bash
experiments
experiments/runtime
experiments/runtime/traces
```

Observation:

- -p creates intermediate directories if they do not already exist

---

**`rm` - remove files**

Input:
```bash
rm sample.txt trace.log output.data notes.txt
```

Output:
(no terminal output)

Verification:
```bash
ls
```

Output:
```bash
c
experiments
linux
python
```

Observation:

- Removes directory entries from filesystem. Deleted file is no longer accesible through its previous path.

**`rm -r` - recursive directory removal**

Input:
```bash
rm -r experiments
```

Output:
(no terminal output)

Verification:
```bash
ls
```

Output:
```bash
c
linux
python
```

Observation:

- Recursively removes directory contents and directory entries.

---

**`cp` - copy files**

Input:
```bash
cp linux/linux-notes.md linux/linux-notes-copy.md
```

Output:
(no terminal output)

Verification:
```bash
ls linux
```

Output:
```bash
linux-notes-copy.md
linux-notes.md
terminal-commands.md
toolchian-verification.md
vm-setup.md
```

Observation:

- Creates a separate file with duplicated contents. Source file remains unchanged.

**`cp -r` - recursive directory copy**

Input:
```bash
cp -r python python-backup
```

Output:
(no terminal output)

Verification:
```bash
ls
```

Output:
```bash
c
linux
python
python-backup
```

Observation:

- Recursively copies directories and their contents.

---

**`mv` - move or rename files**

Input:
```bash
mv linux/linux-notes-copy.md linux/linux-notes-archive.md
```

Output:
(no terminal output)

Verification:
```bash
ls linux
```

Output:
```bash
linux-notes-archive.md
linux-notes.md
terminal-commands.md
toolchain-verification.md
vm-setup.md
```

Observation:

- Changes file path or file name without modifying file contents.

**`mv` - directory relocation**

Input:
```bash
mv python-backup backups
```

Output:
(no terminal output)

Verification:
```bash
ls
```

Output:
```bash
backups
c
linux
python
```

Observation:

- Directory entry location changes within filesystem hierarchy

---

**`cat` - display file contents**

Input:
```bash
cat linux/vm-setup.md
```

Output:
[contents of vm-setup.md displayed]

Observation:

- Reads file content and writes data to stdout.

**`cat` multiple files**

Input:
```bash
cat linux/linux-notes.md linux/toolchain-verification.md
```

Output:
[combined contents displayed sequentially]

Observation:

`cat` outputs file contents in the order provided.

---

**`clear` - clear terminal display**

Input:
```bash
clear
```

Output:
(terminal screen cleared)

Observation:

- Removes visible terminal output from display buffer view. Does not terminate running processes or delete command history.

---

**`grep` - pattern search**

Input:
```bash
grep "process" linux/linux-notes.md
```

Output:
