# Day 04 — Linux Learning Journey
**Date:** June 26, 2026

---

## ✅ What I Accomplished Today

- Learned how Linux file permissions work
- Learned to read permission output from ls -la
- Learned chmod with both symbol and number method
- Learned chown to change file ownership
- Understood real cybersecurity use cases of permissions
- Discovered why chmod 777 is dangerous
- Tested Permission denied by locking files with chmod 000

---

## 💻 Commands Learned

| Command | What it does |
|---------|--------------|
| `ls -la` | Show all files with permissions and owner |
| `chmod +x file` | Add execute permission |
| `chmod -w file` | Remove write permission |
| `chmod 600 file` | Owner read+write only, nobody else |
| `chmod 644 file` | Owner read+write, everyone read only |
| `chmod 755 file` | Owner full, everyone read+execute |
| `chmod 777 file` | Everyone full permission (dangerous!) |
| `chmod 000 file` | Nobody can do anything |
| `chown root file` | Change owner to root |
| `chown asadullah file` | Change owner back to yourself |
| `sudo chown root file` | Change owner with admin power |
| `echo "text" > file` | Write text into a file instantly |
| `echo "text" >> file` | Add text to file without deleting old content |

---

## 🧠 Concepts Learned

- **Permission Groups** = 3 types: owner (u), group (g), others (o)
- **Permission Types** = r (read=4), w (write=2), x (execute=1)
- **Dash `-`** = always holds position of missing permission
- **chmod numbers** = add r+w+x values together for each group
- **chown** = changes WHO owns the file, chmod changes WHAT they can do
- **sudo** = run command as administrator (root)
- **File owner vs Folder owner** = owning folder lets you delete files inside even if file belongs to root
- **echo** = print text on screen or write text into file instantly

---

## 🔢 chmod Number System

| Number | Permission | Calculation |
|--------|------------|-------------|
| 7 | rwx | 4+2+1 |
| 6 | rw- | 4+2 |
| 5 | r-x | 4+1 |
| 4 | r-- | 4 |
| 2 | -w- | 2 |
| 0 | --- | 0 |

---

## 🔐 Real World Permission Uses

| Permission | Where Used | Why |
|------------|------------|-----|
| `600` | SSH private keys | Only you can read — hackers cannot steal |
| `644` | Normal files | Everyone reads, only owner edits |
| `755` | Scripts and programs | Everyone runs, only owner modifies |
| `700` | Private folders | Only owner can open the folder |
| `000` | Fully locked files | Nobody can touch it at all |
| `777` | NEVER use this | Everyone can modify — extremely dangerous |

---

## 💡 Big Insight

> *"chmod controls WHAT can be done, chown controls WHO does it"*
> In Linux I am the boss of my own files.
> I decide who can read, write, and execute — nobody else.
> This is exactly how system administrators protect servers
> and exactly what hackers look for when attacking systems.

---

## ❓ What Confused Me

- Thought chown root alone would block deletion — but folder ownership still allows it
- chmod and chown must be used TOGETHER for full protection
- `sudo chown` needs admin password but sudo remembers it for a few minutes

---

## 🎯 Tomorrow's Goal

- Learn process management (ps, kill, top)
- Learn SSH basics
- Understand how Linux manages running programs
