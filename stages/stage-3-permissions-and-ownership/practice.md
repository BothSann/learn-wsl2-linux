# Stage 3 — Permissions & Ownership

Work inside a throwaway folder again:

```
cd ~
mkdir sandbox
cd sandbox
```

---

## 1. Reading `-rwxr-xr-x` from `ls -l`

**What:** Every file/folder has a permission string like `-rwxr-xr-x`. It tells you who can read, write, or execute it.
**Why:** Before you *change* permissions, you need to be able to *read* them. This is the single most useful skill in this stage.
**When:** Every time `ls -l` output confuses you, or a command says "permission denied."
**How it breaks down:**

```
-rwxr-xr-x
```

| Position | Meaning |
|---|---|
| `-` (1st char) | Type: `-` = file, `d` = directory, `l` = symlink |
| `rwx` (2-4) | **Owner's** permissions: read, write, execute |
| `r-x` (5-7) | **Group's** permissions |
| `r-x` (8-10) | **Everyone else's** permissions |

`r` = read, `w` = write, `x` = execute (run it, or enter it if it's a folder). A `-` means that permission is missing.

**Task:**
- Run `touch myfile.txt` then `ls -l myfile.txt`.
- Write down what the permission string is, and translate it: who can read it? Who can write it? Who can execute it?

---

## 2. `chmod` — changing permissions

**What:** Changes read/write/execute permissions on a file or folder.
**Why:** Sometimes a file needs to be executable (a script) or locked down (no writing) to protect it.
**When:** Making a script runnable, or restricting access to a file.
**How (two styles — learn both):**

```
chmod +x script.sh        # add execute permission for everyone
chmod u+w myfile.txt       # add write permission for the owner (u) only
chmod 755 script.sh        # numeric: owner=rwx(7), group=r-x(5), other=r-x(5)
```

Numeric cheat sheet: `r=4, w=2, x=1` — add them up per group. `7 = rwx`, `5 = r-x`, `6 = rw-`, `0 = ---`.

**Task:**
- Create a fake script: `touch script.sh`. Run `ls -l script.sh` — notice it's **not** executable yet.
- Run `chmod +x script.sh`. Run `ls -l script.sh` again — see the `x` appear.
- Run `chmod 644 myfile.txt`. Run `ls -l myfile.txt` and translate the new permission string out loud.

---

## 3. `chown` — changing ownership

**What:** Changes who **owns** a file (and optionally, what group owns it).
**Why:** Permissions (`rwx`) only matter relative to *who* owns the file. Ownership is the other half of the picture.
**When:** Rare for a beginner day-to-day — mostly needed when a file was created by `root` (or another user) and you need to take it over. Requires `sudo` on most systems.
**How:**
```
sudo chown bs myfile.txt          # change owner to user "bs"
sudo chown bs:bs myfile.txt       # change owner AND group to "bs"
```

**Task:**
- Run `ls -l myfile.txt` and note the current owner (should already be you).
- Run `whoami` to confirm your username.
- Run `sudo chown $(whoami) myfile.txt` — should succeed with no visible change (you already own it). This is just to practice the syntax safely.

---

## 4. `sudo` — what it does, why be careful

**What:** "Superuser do" — runs a single command with admin (root) privileges, bypassing normal permission limits.
**Why:** Some actions (installing software, editing system files, changing ownership of files you don't own) require admin rights on purpose, as a safety gate.
**When:** Only when a command fails with "permission denied" AND you understand exactly what the command does. Never `sudo` a command you don't understand, and never `sudo rm -r` without triple-checking the path.
**How:**
```
sudo apt update       # example: needs admin rights to update package lists
```
It will ask for your password. Typing is invisible on purpose (no dots, nothing shown) — that's normal, keep typing.

**Task:**
- Run `sudo whoami` — it should print `root`, proving the command ran with admin rights (even though your actual user didn't change).
- ⚠️ Do **not** practice `sudo rm` on anything in this stage. Just understand the concept for now — you'll use `sudo` for real in Stage 7 (package management).

---

## Done?

1. Clean up: `cd ~ && rm -r sandbox` (check `pwd` first).
2. Check off Stage 3 items in the GitHub issue.
3. Add a `journal/` entry: what confused you, what clicked. Permissions trip up almost everyone at first — that's normal.
4. Close the issue.
