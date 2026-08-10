# Learn WSL2 & Linux — Terminal Mastery

Goal: go from beginner to confident with the Linux command line, using WSL2.

## How this works

1. Go through the stages below, in order.
2. Each stage = things to try in your terminal, right now, for real.
3. After each session, write a few lines in `journal/` (see template).
4. When stuck, ask Claude Code in this folder — it knows this is your learning repo.

Don't rush. Typing the command yourself beats reading about it.

## Stages

### Stage 1 — Get oriented
- `pwd`, `ls`, `ls -la`, `cd`
- Absolute vs relative paths (`/home/bs` vs `../`)
- `man <command>` and `<command> --help`
- `clear`, `history`, up-arrow to reuse commands
- 📄 Practice tasks: [`stages/stage-1-get-oriented/practice.md`](stages/stage-1-get-oriented/practice.md)

### Stage 2 — Files & folders
- `mkdir`, `touch`, `cp`, `mv`, `rm`, `rm -r`
- `cat`, `less`, `head`, `tail`
- Wildcards: `*`, `?`
- Tab-completion (press Tab, always)
- 📄 Practice tasks: [`stages/stage-2-files-and-folders/practice.md`](stages/stage-2-files-and-folders/practice.md)

### Stage 3 — Permissions & ownership
- `chmod`, `chown`
- Reading `-rwxr-xr-x` output from `ls -l`
- `sudo` — what it does, why be careful with it
- 📄 Practice tasks: [`stages/stage-3-permissions-and-ownership/practice.md`](stages/stage-3-permissions-and-ownership/practice.md)

### Stage 4 — Finding things
- `find`, `grep`, `grep -r`
- `which`, `whereis`
- Pipes: `command1 | command2`
- 📄 Practice tasks: [`stages/stage-4-finding-things/practice.md`](stages/stage-4-finding-things/practice.md)

### Stage 5 — Processes & system
- `ps`, `top` or `htop`
- `kill`, `Ctrl+C`, `Ctrl+Z`, `&`, `jobs`
- `df -h`, `du -sh`, `free -h`
- 📄 Practice tasks: [`stages/stage-5-processes-and-system/practice.md`](stages/stage-5-processes-and-system/practice.md)

### Stage 6 — Text processing
- `grep`, `sed`, `awk` (basics only)
- `sort`, `uniq`, `wc`
- Redirects: `>`, `>>`, `<`

### Stage 7 — Package management
- `apt update`, `apt install`, `apt search`
- Installing and removing software safely

### Stage 8 — Shell basics
- `.bashrc` / `.zshrc` — what it's for
- Environment variables: `export`, `echo $PATH`
- Aliases: `alias ll='ls -la'`

### Stage 9 — Git & WSL2 specifics
- Basic `git` (clone, status, add, commit)
- WSL2 <-> Windows file access (`/mnt/c/...`)
- `wsl.exe` commands from Windows side (if needed)

### Stage 10 — Simple scripting
- Writing a `.sh` file, `chmod +x`, running it
- Variables, `if`, `for` loops — just enough to automate small tasks

## Rules for practice

- Type commands yourself. Don't copy-paste every time.
- Break things in a throwaway folder (`mkdir sandbox`) — best way to learn.
- If a command output confuses you, ask "what does this mean" before moving on.
