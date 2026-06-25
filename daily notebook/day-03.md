# Day 03 — Linux Learning Journey
**Date:** June 25, 2026

---

## ✅ What I Accomplished Today

- Learned file creation and editing commands (touch, nano)
- Learned file reading and copying commands (cat, cp, mv)
- Learned file deletion commands (rm)
- Learned text searching with grep and all its flags
- Learned how to chain commands together using pipes |
- Cloned my GitHub repository to Linux terminal for the first time
- Made my first Git commit and push from the terminal

---

## 💻 Commands Learned

| Command | What it does |
|---------|--------------|
| `touch filename` | Creates a new empty file |
| `cat filename` | Reads and displays file content |
| `nano filename` | Opens file in terminal text editor |
| `cp file destination` | Copies a file to another location |
| `mv file destination` | Moves or renames a file |
| `rm filename` | Deletes a file permanently |
| `grep "word" file` | Searches for a word inside a file |
| `grep -i "word" file` | Searches ignoring uppercase/lowercase |
| `grep -n "word" file` | Shows line numbers of matches |
| `grep -c "word" file` | Counts how many lines match |
| `grep -r "word" folder` | Searches inside all files in a folder |
| `cat file \| grep "word"` | Pipe — feeds output into next command |
| `cat file \| grep "word" \| wc -l` | Chain 3 commands together |
| `git clone <url>` | Downloads a GitHub repo to Linux |
| `git status` | Shows what files have changed |
| `git add .` | Stages all changes for commit |
| `git commit -m "message"` | Saves changes with a description |
| `git push` | Uploads commits to GitHub |

---

## 🧠 Concepts Learned

- **grep** = Global Regular Expression Print — searches text inside files
- **Flags** = extra options added to commands using `-` like `-i`, `-n`, `-c`
- **Pipe `|`** = takes output of one command and feeds it into the next
- **Chaining** = combining multiple commands to do powerful things in one line
- **git clone** = downloading an existing GitHub repo to your local Linux machine
- **Staging** = `git add` prepares files before committing — you choose what to save
- **Commit** = a permanent snapshot of your work with a message describing what changed
- **Push** = sends your local commits to GitHub so the world can see them

---

## 💡 Big Insight

> *"grep + pipes is how real analysts work"*
> Instead of reading thousands of log lines manually,
> you filter, search, and count in seconds.
> This is Digital Forensics and SOC work in its simplest form.

---

## ❓ What Confused Me

- `cat file | grep "word"` and `grep "word" file` give same result — pipe feels redundant at first but becomes essential when chaining 3+ commands
- `git add .` vs `git add filename` — the dot means "everything", specific name means just that file
- Cloning puts the repo in whatever folder you are currently in — always `cd ~` first

---

## 🎯 Tomorrow's Goal

- Learn file permissions (chmod, chown)
- Understand what rwx means
- Learn why permissions matter in cybersecurity
- Practice: `ls -la` to see hidden files and permissions
