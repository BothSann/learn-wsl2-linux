# Stage 4 — Finding Things

Work inside a throwaway folder again:

```
cd ~
mkdir sandbox
cd sandbox
```

---

## 1. `find` — search by filename/type/location

**What:** Searches a folder tree for files/folders matching a name, type, or other property.
**Why:** You often know roughly what a file is called but not exactly where it lives.
**When:** "Where is that file?" questions — searching by name, extension, or type.
**How:**
```
find . -name "*.txt"          # find .txt files, starting from current folder (.)
find . -type d                 # find only directories
find . -type f -name "notes*"  # find files starting with "notes"
```

**Task:**
- Make some test files: `mkdir -p a/b/c && touch a/notes.txt a/b/notes2.txt a/b/c/other.log`.
- Run `find . -name "*.txt"` — should find both `.txt` files, even nested ones.
- Run `find . -type d` — should list only folders (`a`, `a/b`, `a/b/c`).

---

## 2. `grep` — search *inside* file contents

**What:** Searches the **contents** of files for a text pattern (not the filename — that's `find`'s job).
**Why:** `find` locates files by name. `grep` locates text *inside* files. Different jobs, both essential.
**When:** "Which file has the word 'error' in it?" or "does this config contain X?"
**How:**
```
grep "hello" notes.txt        # search one file
grep -i "hello" notes.txt      # -i = case-insensitive
grep -n "hello" notes.txt      # -n = show line numbers
```

**Task:**
- Put some text in a file: `echo "Hello World" > notes.txt` then `echo "another line" >> notes.txt`.
- Run `grep "Hello" notes.txt` — should find the line.
- Run `grep "hello" notes.txt` (lowercase h) — should find **nothing** (case matters by default).
- Run `grep -i "hello" notes.txt` — now it matches, ignoring case.

---

## 3. `grep -r` — search recursively across many files

**What:** `-r` makes `grep` search every file inside a folder, and its subfolders, not just one file.
**Why:** Real searches usually span many files — a whole project, not one file you already know.
**When:** "Which file(s), anywhere in this folder tree, mention X?"
**How:**
```
grep -r "notes2" .             # search every file under current folder
grep -rn "notes2" .            # same, with line numbers
```

**Task:**
- Add the word `banana` to two different nested files: `echo "banana" >> a/notes.txt` and `echo "banana split" >> a/b/c/other.log`.
- Run `grep -r "banana" .` — it should show matches from both files, with the filename prefixed.

---

## 4. `which` and `whereis`

**What:** `which` shows the full path of the program that runs when you type a command. `whereis` shows the binary, source, and man page locations.
**Why:** Confirms exactly which program you're running (useful when multiple versions exist) and whether a command even exists on your system.
**When:** "Is this command installed?" / "Which exact program am I running?"
**How:**
```
which ls
which python3
whereis ls
```

**Task:**
- Run `which ls` — note the path it prints (probably `/usr/bin/ls` or `/bin/ls`).
- Run `which some-fake-command-xyz` — see it print nothing (command doesn't exist).
- Run `whereis ls` — compare to `which`, notice it shows more locations (binary + man page).

---

## 5. Pipes: `command1 | command2`

**What:** The `|` (pipe) takes the **output** of one command and feeds it as **input** to the next command, chaining them together.
**Why:** This is the real power of the terminal — small commands combine into exactly what you need, instead of hunting for one giant command that does everything.
**When:** Whenever you want to filter, count, or transform another command's output.
**How:**
```
ls -la | grep ".txt"           # list files, then filter for .txt only
history | grep "cd"             # search your command history for past "cd" commands
cat notes.txt | grep "banana"   # search file contents (same as grep "banana" notes.txt)
```

**Task:**
- Run `ls -la` alone in your sandbox folder, look at the full output.
- Now run `ls -la | grep "notes"` — see only lines matching "notes."
- Run `history | grep "grep"` — find every `grep` command you've typed so far in this session.

---

## Done?

1. Clean up: `cd ~ && rm -r sandbox` (check `pwd` first).
2. Check off Stage 4 items in the GitHub issue.
3. Add a `journal/` entry: what confused you, what clicked.
4. Close the issue.
