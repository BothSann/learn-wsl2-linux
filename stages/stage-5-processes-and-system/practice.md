# Stage 5 — Processes & System

No sandbox folder needed this time — everything here is about running programs and system info, not files.

---

## 1. `ps` — snapshot of running processes

**What:** Lists processes (running programs) at this exact moment. A "process" is any running program — your shell, a script, a server, anything.
**Why:** Before you can manage a process (stop it, check it), you need to see it exists and get its PID (process ID).
**When:** "What's running right now?" / "What's the PID of this program so I can kill it?"
**How:**
```
ps                 # processes in THIS terminal session only
ps aux              # every process on the system, all users, full detail
```

**Task:**
- Run `ps` — note how short the list is (just your shell and `ps` itself).
- Run `ps aux` — much longer. Find the `PID` and `COMMAND` columns.
- Run `ps aux | grep bash` (using the pipe from Stage 4) — filter down to just bash processes.

---

## 2. `top` (or `htop`) — live process viewer

**What:** A live, auto-refreshing dashboard of processes, sorted by CPU/memory usage.
**Why:** `ps` is a snapshot (one moment, frozen). `top` is a movie — you watch things change in real time.
**When:** "What's eating my CPU/memory right now?"
**How:**
```
top                 # press q to quit
htop                # nicer version, may need: sudo apt install htop
```

**Task:**
- Run `top`. Watch it for 10 seconds. Find the process using the most CPU (`%CPU` column, usually top-sorted).
- Press `q` to quit.
- If you have `htop` installed, try it too — compare readability to `top`.

---

## 3. `kill`, `Ctrl+C`, `Ctrl+Z`, `&`, `jobs`

**What:**
- `Ctrl+C` — stop the currently running foreground command immediately.
- `Ctrl+Z` — pause (suspend) it, don't stop it, just freeze it in the background.
- `&` at the end of a command — run it in the background from the start, so your terminal stays free.
- `jobs` — list what's paused/running in the background of this terminal.
- `kill <PID>` — stop a process by its process ID (from `ps`).

**Why:** You need to control programs that are misbehaving, stuck, or just need to run in the background while you keep working.
**When:** A command hangs → `Ctrl+C`. Want it paused, not killed → `Ctrl+Z`. Want it running without blocking your terminal → `&`.
**How:**
```
sleep 100            # a command that just waits 100 seconds, doing nothing
# press Ctrl+C — it stops immediately

sleep 100
# press Ctrl+Z — it pauses, terminal is free again
jobs                 # shows: [1]+ Stopped   sleep 100

sleep 100 &          # runs in the background right away
jobs                 # shows it running

ps aux | grep sleep   # find its PID
kill <PID>            # stop it by PID
```

**Task:**
- Run `sleep 100`, then press `Ctrl+C`. Confirm you get your prompt back immediately.
- Run `sleep 100` again, then press `Ctrl+Z`. Run `jobs` — see it listed as "Stopped."
- Run `kill %1` (kills job number 1 from the `jobs` list) to clean it up.
- Run `sleep 100 &`. Run `ps aux | grep sleep` to find its PID. Run `kill <that PID>` to stop it.

---

## 4. `df -h`, `du -sh`, `free -h`

**What:** `df -h` = disk space free/used per drive ("disk free," human-readable). `du -sh` = size of a specific folder ("disk usage," summarized, human-readable). `free -h` = RAM used/free.
**Why:** Basic system health checks — "am I running out of space?" and "am I running out of memory?"
**When:** Before installing something big, or when things feel slow.
**How:**
```
df -h
du -sh ~/learn-wsl2-linux
free -h
```

**Task:**
- Run `df -h`. Find the line for your main drive (`/` or similar) — note how full it is.
- Run `du -sh ~/learn-wsl2-linux` — see the total size of this repo.
- Run `free -h` — note total vs. available memory.

---

## Done?

1. Make sure no `sleep` processes are still running: `ps aux | grep sleep`, `kill` any leftovers.
2. Check off Stage 5 items in the GitHub issue.
3. Add a `journal/` entry: what confused you, what clicked.
4. Close the issue.
