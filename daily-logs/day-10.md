# Day 10 - Return to DevOps Mastery | Linux Networking & Security

## Why the Gap?

Development was temporarily paused due to my **4th Semester B.Tech End Semester Examinations**.

During this period, I intentionally shifted my complete focus toward academics to perform well in university assessments. Rather than trying to split attention between multiple demanding goals, I prioritized finishing the semester strongly before returning to my long-term DevOps mastery roadmap.

With the examinations completed, I have resumed full-time learning and will continue progressing consistently toward becoming a highly skilled DevOps Engineer.

---

## Topics Covered

### 🌐 Advanced Networking
- Firewalls (iptables, nftables, UFW)
- Defense in Depth
- NAT (Network Address Translation)

### 🔐 Linux Security
- umask
- SUID (Set User ID)
- SGID (Set Group ID)
- Sticky Bit
- ACL (Access Control Lists)
- sudo Internals

---

## Key Concepts Learned

### Firewalls
- Learned how Linux filters incoming and outgoing traffic.
- Understood the differences between ACCEPT, DROP and REJECT.
- Learned why traditional firewalls cannot detect application-layer attacks.

### Defense in Depth
- Studied layered enterprise security architecture.
- Understood that each security layer exists assuming previous layers may eventually fail.

### NAT
- Learned how private networks communicate with the Internet using address translation.
- Understood that NAT primarily performs address translation while providing only a minor security benefit through address hiding.

### umask
- Learned how Linux determines default permissions for newly created files and directories.
- Understood why executable permissions are intentionally excluded for newly created files.

### SUID
- Learned how programs temporarily execute with the owner's privileges.
- Studied why privileged programs such as `passwd` work without permanently elevating user permissions.

### SGID
- Learned how shared project directories maintain consistent group ownership.
- Understood its importance for collaborative development environments.

### Sticky Bit
- Learned how Linux prevents users from deleting each other's files inside shared directories.
- Studied the `/tmp` directory as a real-world example.

### ACL
- Learned how Access Control Lists extend the traditional Owner / Group / Others permission model.
- Practiced assigning permissions to individual users and groups.

### sudo Internals
- Learned how `sudo` authenticates users, verifies permissions using the sudoers policy, executes authorized commands with elevated privileges, logs the action, and returns to normal user privileges.

---

## Commands Practiced

```bash
# Firewall
sudo ufw status
sudo ufw allow 80
sudo iptables -L
sudo nft list ruleset

# umask
umask
umask 077

# SUID
chmod u+s
chmod u-s
find / -perm -4000

# SGID
chmod g+s
chmod g-s

# Sticky Bit
chmod +t
chmod -t

# ACL
getfacl file
setfacl -m u:user:rw file
setfacl -x u:user file
setfacl -b file

# sudo
sudo command
sudo visudo
su -
```

---

## Personal Reflection

Returning after the semester break reminded me that consistency is measured over months and years—not by avoiding every interruption.

This break was a planned academic commitment rather than a loss of momentum. Completing my semester examinations allows me to dedicate my full attention to my long-term roadmap without divided focus.

Today's learning reinforced an important realization: Linux security is built on small, focused mechanisms that each solve one specific problem. Understanding *why* these mechanisms exist has been far more valuable than simply memorizing commands.

With the semester completed, my focus now shifts entirely back to mastering Linux, Bash scripting, Docker, Kubernetes, Cloud, and eventually Cloud Security Architecture.

---

## Progress

✅ Advanced Networking Completed

✅ Linux Security Completed

➡️ Next: Bash Scripting Engineering