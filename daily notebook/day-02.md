# Day 02 — Linux Learning Journey
**Date:** June 22, 2026

---

## ✅ What I Accomplished Today

- Learned navigation commands
- Mounted Windows D: and E: drives from Linux
- Navigated Windows folders through Linux terminal
- Opened VS Code from Linux terminal
- Explored $RECYCLE.BIN through Linux (intro to Digital Forensics!)
- Recovered a deleted file using Linux cp command

---

## 🖥️ Commands Learned

| Command | What it does |
|---------|-------------|
| `cd foldername` | Go inside a folder |
| `cd ..` | Go back one folder |
| `cd ~` | Go home instantly |
| `cd /` | Go to root of system |
| `ls /mnt/d` | See contents of D: drive |
| `sudo mount -t drvfs D: /mnt/d` | Mount Windows D: drive in Linux |
| `sudo umount /mnt/d` | Unmount a drive |
| `cp file destination` | Copy a file to another location |
| `code .` | Open VS Code in current folder |
| `file filename` | Check what type a file is |

---

## 🧠 Concepts Learned

### Linux Filesystem
- `/mnt` = where Windows drives connect to Linux (mnt = mount)
- `/mnt/c` = Windows C: drive
- `/mnt/d` = Windows D: drive
- `/mnt/e` = Windows E: drive
- Everything in Linux is a folder — even hard drives!

### Quotes in Linux
| Type | When to use |
|------|------------|
| `"double quotes"` | Normal use — but `$` becomes a variable |
| `'single quotes'` | When path contains `$` sign |
| `backslash\ space` | Alternative for spaces in names |

### Digital Forensics (Year 2 Preview!)
- `$RECYCLE.BIN` = Windows Recycle Bin folder visible in Linux
- `$I` files = metadata of deleted files (name, size, original location)
- `$R` files = actual content of deleted files
- **SID** = Windows Security Identifier (unique ID for each user)
- Deleted files are recoverable until overwritten!
- Tool for secure deletion: `shred -u filename`

---

## 💡 Big Insights

> *"Windows is the roof, Linux is the basement"*
> Windows hides system files. Linux exposes EVERYTHING.
> Cybersecurity professionals need to see the basement — because attackers hide there!

> *"Deleted doesn't mean gone!"*
> Files remain on disk until overwritten by new data.
> This is why Digital Forensics is a real career skill!

---

## ❓ What Confused Me

- `sudo umount` not `sudo umnount` — easy spelling mistake!
- Can't unmount a drive you are currently inside — go home first with `cd ~`
- `$` sign needs single quotes in Linux paths
- `target is busy` error = you're still inside the folder you're trying to unmount

---

## 🔗 How Linux and Windows Connect

```
Linux Terminal
      ↓
   code .
      ↓
VS Code opens on Windows
but reads Linux files!
```

This is how real developers work — Linux terminal + VS Code together!

---

## 🎯 Tomorrow's Goal

- Learn `touch` — create files
- Learn `cat` — read files
- Learn `nano` — edit files
- Learn `rm` — delete files
- Practice creating and editing files from terminal
