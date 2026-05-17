## Working context
- all commands are executed inside:

```bash
~/projects/systems-learning-log/phase-0
```

---

`pwd` - current location

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

`cd` - directory navigation

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

`ls` - directory listing

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

---

`ls -l` - detailed listing ("long")

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

---

`ls -a` - include hidden files ("all")

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

---

`ls -la` - combined view

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

`echo` - output to stdout

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

Git status

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

Git staging and commit

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