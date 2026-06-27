# Day 06 — Linux Learning Journey
**Date:** June 27, 2026

---

## ✅ What I Accomplished Today

- Understood what SSH is and the problem it solves
- Installed and started OpenSSH server
- Made my first SSH connection to localhost
- Understood SSH port 22 and why admins change it
- Learned difference between password and key authentication
- Generated ED25519 SSH key pair
- Understood private vs public key concept
- Read SSH logs like a forensics analyst
- Explored SSH config file and security settings
- Understood SSH hardening for real servers

---

## 💻 Commands Learned

| Command | What it does |
|---------|--------------|
| ssh -V | Check SSH version installed |
| sudo apt install openssh-server -y | Install SSH server |
| sudo service ssh start | Start SSH server |
| sudo service ssh stop | Stop SSH server |
| sudo service ssh status | Check if SSH is running |
| ssh username@ip-address | Connect to remote server |
| ssh username@localhost | Connect to your own machine |
| ssh username@ip -p 2220 | Connect on specific port |
| ssh-keygen -t ed25519 -C label | Generate SSH key pair |
| cat ~/.ssh/id_ed25519.pub | View your public key |
| ls -la ~/.ssh/ | View SSH files and permissions |
| sudo cat /etc/ssh/sshd_config | View SSH server config |
| sudo cat /var/log/auth.log | grep ssh | View SSH login logs |
| exit | Disconnect from SSH session |
| whoami | Show current logged in user |
| hostname | Show computer name |

---

## 🧠 Concepts Learned

- SSH = Secure Shell — encrypted remote terminal access to computers
- Encrypted = all traffic scrambled — nobody can intercept and read it
- Port 22 = default SSH door — hackers scan for this automatically
- Client = computer YOU are sitting at
- Host/Server = computer YOU connected TO
- localhost = your own machine — IP always 127.0.0.1
- Password auth = login with password — can be brute forced
- Key auth = login with SSH key — mathematically impossible to guess
- Private key = stays on YOUR computer only — NEVER share!
- Public key = goes on server — safe to share
- known_hosts = file that remembers servers you connected to before
- Passphrase = extra password protecting your private key
- sshd_config = SSH server configuration file — controls all SSH settings
- RandomArt = visual fingerprint of your SSH key

---

## 🔑 SSH Key Types

| Key Type | Age | Security | Recommendation |
|----------|-----|----------|----------------|
| RSA | 1977 Old | Good but aging | Being phased out |
| ECDSA | Medium age | Better | Acceptable |
| ED25519 | 2011 New | Best | Always use this! |

---

## 🔐 SSH Key Permissions

private key id_ed25519 = chmod 600 = only owner reads — CORRECT
public key id_ed25519.pub = chmod 644 = everyone reads — CORRECT

If private key has wrong permissions SSH refuses to connect:
WARNING: UNPROTECTED PRIVATE KEY FILE!
Permissions 0644 are too open — Connection rejected!

---

## 🔒 SSH Config File — /etc/ssh/sshd_config

| Setting | Default | Secure Value | Why |
|---------|---------|--------------|-----|
| Port | 22 | Random e.g 47832 | Hides from automated scanners |
| PermitRootLogin | prohibit-password | no | Root login = full system access if hacked |
| PasswordAuthentication | yes | no | Eliminates brute force attacks completely |
| PermitEmptyPasswords | no | no | Never allow blank passwords |

Warning — Change these settings only on real servers not practice machine!

---

## 📊 MY SSH Files

~/.ssh/id_ed25519 = private key chmod 600 — NEVER SHARE
~/.ssh/id_ed25519.pub = public key chmod 644 — safe to share
~/.ssh/known_hosts = servers I connected to before

---

## 🔐 Cybersecurity Connections

Brute Force Attack Detection:
sudo cat /var/log/auth.log | grep "Failed"
Multiple failed logins from same IP = brute force attack!

SSH Hardening Real Server Checklist:
- Change port from 22 to random number
- Disable root login completely
- Disable password authentication — keys only
- Use ED25519 keys with passphrase
- Monitor /var/log/auth.log regularly

Man in the Middle Attack Warning:
If server fingerprint changes unexpectedly you will see:
WARNING: REMOTE HOST IDENTIFICATION HAS CHANGED!
This means someone may be intercepting your connection!
Never ignore this warning!

Private Key Theft:
If private key has chmod 644 other users on same system can read it
They can copy and use it to impersonate you
Always keep private key at chmod 600!

---

## 💡 Big Insight

SSH keys are not just convenience — they are security
Passwords can be guessed, stolen, and brute forced
SSH keys are mathematically generated randomness
A hacker would need millions of years to guess your ED25519 key
This is why every serious server uses key authentication only
In Year 2 when I set up AWS — SSH keys will be my first security step!

---

## ❓ Interview Questions I Can Now Answer

Q: What is SSH and why is it used?
A: SSH Secure Shell is a protocol for secure encrypted remote access to computers through terminal. It encrypts all traffic between client and server making it impossible for anyone to intercept commands or data. It is the standard way administrators and developers manage remote servers.

Q: What is the difference between SSH password and key authentication?
A: Password authentication requires typing a password which can be guessed stolen or brute forced. Key authentication uses a mathematically generated key pair — private key stays on your computer public key goes on server. Keys are impossible to guess and eliminate brute force attacks completely.

Q: Why should you change SSH default port 22?
A: Hackers use automated robots that scan the entire internet for open port 22. Changing to a random port like 47832 means these robots skip your server completely — stopping 90% of automated attacks without any other changes.

Q: What happens if SSH private key permissions are wrong?
A: SSH refuses to connect and shows WARNING UNPROTECTED PRIVATE KEY FILE. If permissions are too open other users on the same system could read and steal the private key to impersonate you. Private key must always be chmod 600.

Q: What is known_hosts file?
A: known_hosts stores fingerprints of servers you have connected to before. When you reconnect SSH verifies the fingerprint matches. If it changed unexpectedly SSH warns you — this could indicate a Man in the Middle attack where someone is intercepting your connection.

Q: What does PermitRootLogin no mean in sshd_config?
A: It prevents the root user from logging in via SSH directly. This is critical because if a hacker logs in as root they have complete unrestricted control over the entire system immediately.

---

## 🎯 Tomorrow's Goal

- Learn UFW firewall basics
- Understand what a firewall does
- Allow and deny specific ports
- Check firewall status
- Connect firewall rules to SSH port knowledge
