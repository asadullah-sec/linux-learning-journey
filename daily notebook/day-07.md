# Day 07 — Linux Learning Journey
**Date:** June 28, 2026

---

## ✅ What I Accomplished Today

- Understood what a firewall is and why it exists
- Installed UFW (Uncomplicated Firewall) on Linux
- Learned the golden rule — always allow SSH before enabling firewall
- Enabled UFW and configured real firewall rules
- Allowed and denied specific ports
- Learned IP whitelisting — allow specific IP only
- Understood rule ordering in firewall
- Understood difference between allow and deny
- Cleaned up firewall rules properly
- Connected firewall concepts to real cybersecurity scenarios
- Understood all 4 layers of defense in depth

---

## 💻 Commands Learned

| Command | What it does |
|---------|--------------|
| sudo apt install ufw -y | Install UFW firewall |
| sudo ufw status | Check firewall status and rules |
| sudo ufw enable | Turn firewall ON |
| sudo ufw disable | Turn firewall OFF |
| sudo ufw allow 22 | Allow SSH connections |
| sudo ufw allow 80 | Allow HTTP website traffic |
| sudo ufw allow 443 | Allow HTTPS secure website traffic |
| sudo ufw deny 3306 | Block MySQL database port |
| sudo ufw delete allow 80 | Delete an allow rule |
| sudo ufw delete deny 3306 | Delete a deny rule |
| sudo ufw allow from IP to any port 22 | Allow specific IP only for SSH |
| sudo ufw reset | Delete ALL rules and start fresh |
| echo $SSH_CONNECTION | Check if inside SSH session |

---

## 🧠 Concepts Learned

- Firewall = security guard that controls what traffic enters and exits your system
- Port = numbered door on your system — every service has its own port
- UFW = Uncomplicated Firewall — simplified version of complex iptables
- Allow = open a specific door for connections
- Deny = block a specific door completely
- Default behavior = UFW blocks ALL incoming when enabled — allow SSH first!
- IP Whitelisting = only specific trusted IPs allowed through a port
- Rule ordering = UFW reads rules top to bottom — first match wins!
- Delete rule = must specify exact rule — allow vs deny matters!
- localhost bypass = UFW does not block localhost connections — only external!
- IPv4 and IPv6 = every rule applies to both — that is why you see v6 duplicate

---

## 🔐 Important Ports to Remember

| Port | Service | Security Note |
|------|---------|---------------|
| 22 | SSH | Always allow — change default port on real servers |
| 80 | HTTP | Allow for web servers — blocks website if denied |
| 443 | HTTPS | Allow for secure web servers |
| 3306 | MySQL | Always deny from outside — database must be private |
| 21 | FTP | Very insecure — avoid using |
| 53 | DNS | Domain name resolution |
| 25 | SMTP | Email sending |

---

## ⚠️ Golden Rules of UFW

1. ALWAYS allow SSH port 22 BEFORE enabling UFW
2. ALWAYS specify allow or deny correctly when deleting rules
3. Rule order matters — first match wins — put specific rules before general ones
4. Database ports should ALWAYS be denied from outside
5. Build good habits now — these same rules apply on real AWS servers!

---

## 🔐 Cybersecurity Connections

Defense in Depth — All 4 Layers I Learned This Week:

Layer 1 = UFW Firewall
What it does: Blocks unwanted connections before they reach system
What I learned: Allow/deny ports, IP whitelisting, rule ordering
Real use: Block all ports except 22, 80, 443 on production server

Layer 2 = SSH Configuration
What it does: Controls who can authenticate and how
What I learned: sshd_config, PermitRootLogin, PasswordAuthentication
Real use: Disable root login, force key auth, change port 22

Layer 3 = File Permissions
What it does: Controls who can read, write, execute files
What I learned: chmod, chown, rwx numbers, private key protection
Real use: chmod 600 on SSH keys, chmod 644 on public files

Layer 4 = Process Monitoring
What it does: Detects suspicious activity on running system
What I learned: ps aux, top, kill, reading process output
Real use: Find malware processes, kill suspicious programs

All 4 layers together = real security professional thinking!
Missing even one layer = security gap hackers will find!

Database Protection:
Port 3306 denied = hackers cannot even reach database
Even with correct credentials — firewall stops them before connection!

IP Whitelisting:
Only trusted IP allowed for SSH
Hacker from different IP = blocked by firewall immediately!
Even knowing your password = useless if firewall blocks them!

Port 80 and 443 Explained:
Allowing these does NOT expose your browsing history!
It means your machine CAN act as a web server
Nobody sees what YOU browse — only what your server SERVES!
Deny port 80 = nobody can visit your website
Allow port 80 = visitors can reach your website

UFW vs iptables:
UFW translates simple commands into complex iptables rules behind scenes
sudo ufw allow 22 creates multiple iptables rules automatically
UFW = beginner friendly, iptables = expert level, same power!

---

## 💡 Big Insight

Firewall is not just a technical tool — it is a policy enforcement system
Every allow and deny rule is a security decision
Port 3306 denied = database hidden from world
Port 22 restricted to one IP = SSH locked to trusted source only
In Year 2 on AWS — first thing I do after launching server = configure UFW!
Firewall is the first line of defense — everything else builds on top of it!

Defense in depth means no single point of failure:
Firewall fails = SSH config saves you
SSH config fails = file permissions save you
File permissions fail = process monitoring alerts you
All 4 layers = a real secure system!

---

## ❓ Interview Questions I Can Now Answer

Q: What is a firewall and why is it important?
A: A firewall is a security system that controls incoming and outgoing network traffic based on rules. It is important because it acts as the first line of defense — blocking unauthorized access to sensitive ports and services before attackers can even attempt to exploit them.

Q: What is UFW and how is it different from iptables?
A: UFW (Uncomplicated Firewall) is a simplified interface for managing iptables — the powerful but complex Linux firewall. UFW translates simple commands like sudo ufw allow 22 into complex iptables rules automatically. UFW is beginner friendly while providing the same protection as iptables.

Q: Why should you allow SSH before enabling UFW?
A: UFW default behavior when enabled is to block ALL incoming connections. If you enable UFW before allowing SSH port 22, the firewall blocks your SSH connection and you lock yourself out of the server completely. Always add SSH rule first then enable firewall.

Q: What is IP whitelisting?
A: IP whitelisting means only allowing specific trusted IP addresses to connect to a sensitive port. For example allowing only your office IP to connect to SSH port 22. Even if a hacker knows your password they cannot reach SSH because the firewall blocks their IP before connection is established.

Q: Why should database port 3306 always be denied?
A: Database contains sensitive data — customer information, passwords, financial records. If port 3306 is open attackers can attempt direct database connections, brute force database passwords, or exploit database vulnerabilities. Denying port 3306 hides the database from internet completely — even knowing credentials is useless if firewall blocks access.

Q: What does rule ordering mean in UFW?
A: UFW processes rules from top to bottom and applies the first matching rule. If you have Allow port 22 from Anywhere above Allow port 22 from specific IP — the Anywhere rule matches first and everyone gets in. Specific rules must be placed before general rules to work correctly.

Q: What is defense in depth?
A: Defense in depth means using multiple layers of security so that if one layer fails others still protect the system. In Linux this means firewall blocks unwanted connections, SSH config controls authentication, file permissions protect sensitive files, and process monitoring detects suspicious activity. No single point of failure!

---

## 🎯 Tomorrow's Goal

- Deep revision of entire Week 1
- Create LinkedIn profile
- Register for ISC2 CC — free
- Review all day-01 to day-07 notes
- Identify weak areas and practice them
- Prepare for OverTheWire Bandit starting Day 9
