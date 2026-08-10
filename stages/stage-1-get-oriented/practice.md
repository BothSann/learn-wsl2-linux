# Stage 1 — Get Oriented

Six commands. Do them in order, in your real terminal. Don't skip typing them.

---

## 1. `pwd`

**What:** Prints the folder you're standing in right now (full path).
**Why:** Before you touch anything, you need to know where you are. Like checking a map pin.
**When:** Anytime you're not sure "where am I in this filesystem."
**How:**
```
pwd
```
That's it, no options needed.

**Task:**
- Open your terminal. Run `pwd`. Write down what it prints.

---

## 2. `ls` and `ls -la`

**What:** Lists what's inside the current folder. `-l` = long format (details), `-a` = show hidden files too.
**Why:** You can't work with files you can't see. Hidden files (dotfiles like `.bashrc`) hold real config.
**When:** Every time you enter a new folder, basically a reflex.
**How:**
```
ls
ls -la
```

**Task:**
- Run `ls` in your home folder. Then run `ls -la`. Compare the two outputs — what showed up that wasn't there before?
- Pick one line from the `ls -la` output. Try to read it: what's the permission string, who owns it, how big is it?

---

## 3. `cd` — absolute vs relative paths

**What:** Changes your current folder. Absolute path = full path from `/`. Relative path = from where you are now.
**Why:** Absolute paths always work no matter where you are. Relative paths are shorter but depend on your current location.
**When:** Absolute when you want to be 100% sure (scripts, jumping far away). Relative when moving nearby.
**How:**
```
cd /home/bs/learn-wsl2-linux    # absolute — starts with /
cd ..                            # relative — one folder up
cd stages                        # relative — into a subfolder from here
cd ~                             # shortcut — your home folder
```

**Task:**
- From your home folder, `cd` into `learn-wsl2-linux` using the **absolute** path.
- Run `pwd` to confirm.
- Now `cd ..` to go back up one level. Run `pwd` again.
- Now `cd` back into `learn-wsl2-linux` using a **relative** path (just the folder name, no leading `/`).

---

## 4. `man` and `--help`

**What:** `man <command>` opens the full manual page. `<command> --help` prints a quick summary.
**Why:** You will forget flags. Don't memorize — look them up. This is normal, not a failure.
**When:** Whenever you see a flag you don't recognize, or want to know what a command can do.
**How:**
```
man ls
ls --help
```
(Press `q` to exit `man`.)

**Task:**
- Run `man ls`. Scroll down (arrow keys or spacebar) until you find what `-a` and `-l` actually mean in the manual's own words. Press `q` to quit.
- Run `ls --help` and compare — shorter, right?

---

## 5. `clear`

**What:** Wipes your terminal screen clean. Doesn't undo anything, just visual.
**Why:** A messy screen makes it hard to see new output. Reset it whenever it gets noisy.
**When:** Whenever your terminal feels cluttered.
**How:**
```
clear
```
Shortcut: `Ctrl + L` does the same thing without typing.

**Task:**
- Run a few commands to make some clutter, then run `clear`. Try `Ctrl+L` too.

---

## 6. `history` and the up-arrow

**What:** `history` lists every command you've typed recently. The up-arrow key recalls the previous command, one at a time.
**Why:** You will retype the same commands constantly. Don't retype — recall.
**When:** Any time you want to reuse or check a past command.
**How:**
```
history
```
Then press the **up arrow** a few times in your terminal and watch old commands reappear.

**Task:**
- Run `history` and find the `pwd` command you ran in Task 1.
- Press the up-arrow key 5 times, watch your last 5 commands cycle by, then press Enter on one to rerun it.

---

## Done?

1. Check off Stage 1 items in [Issue #1](https://github.com/BothSann/learn-wsl2-linux/issues/1).
2. Copy `journal/TEMPLATE.md` to `journal/2026-08-10.md` (or today's date) and write a few lines: what confused you, what clicked.
3. Close the issue.
