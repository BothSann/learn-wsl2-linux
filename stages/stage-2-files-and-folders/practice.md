# Stage 2 — Files & Folders

Work inside a throwaway folder so you can't break anything real.

```
cd ~
mkdir sandbox
cd sandbox
```

Do everything below inside `sandbox`.

---

## 1. `mkdir` and `touch`

**What:** `mkdir` makes a new folder. `touch` makes a new empty file (or updates its timestamp if it exists).
**Why:** These are how you create things instead of just looking at them.
**When:** `mkdir` before you need a folder to organize files. `touch` for a quick empty file, or scripts.
**How:**
```
mkdir practice-files
touch notes.txt
```

**Task:**
- Make a folder called `practice-files`.
- Inside it, `touch` three files: `a.txt`, `b.txt`, `c.log`.
- Run `ls -la practice-files` to confirm all three exist.

---

## 2. `cp` and `mv`

**What:** `cp` copies a file (original stays). `mv` moves a file (original disappears) — also used to **rename** files.
**Why:** Copying preserves a backup. Moving reorganizes or renames without duplicating.
**When:** `cp` before you edit something risky. `mv` to rename or relocate.
**How:**
```
cp a.txt a-backup.txt
mv b.txt renamed-b.txt
mv c.log ../c.log        # moves it out of the folder
```

**Task:**
- Inside `practice-files`, copy `a.txt` to `a-copy.txt`.
- Rename `b.txt` to `b-renamed.txt` using `mv`.
- Confirm with `ls -la` — you should see `a.txt`, `a-copy.txt`, `b-renamed.txt`, `c.log`.

---

## 3. `rm` and `rm -r`

**What:** `rm` deletes a file. `rm -r` deletes a folder and everything inside it, recursively.
**Why:** Cleanup. But there's **no trash bin** — deleted means gone.
**When:** Only on things you're sure about. Never `rm -r` on a path you haven't double-checked with `pwd`/`ls` first.
**How:**
```
rm a-copy.txt
rm -r some-folder
```

**Task:**
- Delete `c.log` with `rm`.
- Make a throwaway folder `mkdir temp-junk`, put a file in it, then delete the whole folder with `rm -r temp-junk`.
- ⚠️ Before running any `rm -r`, run `pwd` first so you know exactly where you are.

---

## 4. `cat`, `less`, `head`, `tail`

**What:** All four *read* a file without editing it. `cat` dumps the whole thing. `less` opens it page-by-page (scrollable). `head` shows the first 10 lines. `tail` shows the last 10 lines.
**Why:** Files can be huge — you rarely want the whole thing dumped at once. Pick the right tool for the size.
**When:** `cat` for short files. `less` for long files. `head`/`tail` to peek at the start/end (e.g. log files).
**How:**
```
cat notes.txt
less notes.txt      # press q to quit
head notes.txt
tail notes.txt
```

**Task:**
- Add a few lines of text to `notes.txt` (use `nano notes.txt`, type something, `Ctrl+O` to save, `Ctrl+X` to exit).
- View it with `cat`, then `less` (press `q` to quit), then `head`, then `tail`.

---

## 5. Wildcards: `*` and `?`

**What:** `*` matches any number of characters. `?` matches exactly one character. Used to select multiple files at once.
**Why:** Instead of typing every filename, you describe a pattern.
**When:** Deleting, copying, or listing groups of similar files.
**How:**
```
ls *.txt        # every file ending in .txt
ls a?.txt       # a followed by exactly one character, then .txt
```

**Task:**
- Inside `practice-files`, create `x1.txt`, `x2.txt`, `x10.txt`.
- Run `ls x*.txt` — see all three.
- Run `ls x?.txt` — see only `x1.txt` and `x2.txt` (not `x10.txt`, that's two characters).

---

## 6. Tab-completion

**What:** Press `Tab` while typing a path/filename and the shell auto-completes it. Press `Tab` twice to see all options if there's more than one match.
**Why:** Faster, and it prevents typos in long paths — the #1 way experienced terminal users avoid mistakes.
**When:** Always. Make it a reflex, every single time you type a path.
**How:** Type part of a name, hit `Tab`.

**Task:**
- Type `cd prac` then press `Tab` — it should complete to `practice-files`.
- Type `cat n` then press `Tab` inside that folder — see it complete toward `notes.txt`.

---

## Done?

1. Clean up: `cd ~ && rm -r sandbox` (double-check `pwd` first).
2. Check off Stage 2 items in the GitHub issue.
3. Add a `journal/` entry: what confused you, what clicked.
4. Close the issue.
