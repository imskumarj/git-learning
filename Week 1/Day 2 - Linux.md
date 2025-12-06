# Notes - Day 2

## 🎯 Day 2 Master Revision: Permissions & Secure Remote Access

---

<aside>

**Your Linux Security Journey** 🚀

Today you're mastering two pillars of Linux security — file permissions that control local access, and SSH that enables secure remote connections. Here's your complete knowledge map.

</aside>

### 📚 What You're Learning Today

<aside>

**Core Topics:**

- Linux permissions: `chmod`, `chown`
- Understanding rwx (read, write, execute)
- User and group concepts
- SSH basics and key generation
- Secure remote access fundamentals
</aside>

### 📖 Learning Resources (90 mins total)

- **Linux Journey — "Permissions" section**
    
    🔗 https://linuxjourney.com/lesson/permissions *(50 mins)*
    
- **SSH Basics – TechWorld with Nana**
    
    🔗 [SSH Tutorial](https://www.youtube.com/watch?v=vpk_1gldOAE) *(10 mins)*
    
- **Corey Schafer SSH Keys** (Optional deep dive)
    
    🔗 [SSH Without Password](https://www.youtube.com/watch?v=vpk_1gldOAE) *(15 mins)*
    

---

## Part 1: The Linux Permission System

### 🏗️ The Foundation: Understanding Permissions

**Every file in Linux tells a story through 10 characters:** `drwxr-xr-x`

Think of it as a **security badge** with four sections:

1. **Type** (1 char): What am I? (`d`=directory, `-`=file, `l`=link)
2. **Owner Powers** (3 chars): What can the file owner do?
3. **Group Powers** (3 chars): What can group members do?
4. **World Powers** (3 chars): What can everyone else do?

**The three magic letters:** `r`(read), `w`(write), `x`(execute) — your keys to the kingdom!

---

### 🛠️ The Two Languages of Permission Control

<aside>

**📝 Symbolic: Human-Friendly**

`chmod u+x file` → Give owner execute

`chmod g-w file` → Remove group write

`chmod o=r file` → Set others to read-only

**Perfect for:** Quick, specific changes

</aside>

<aside>

**🔢 Numeric: Power User**

`chmod 755 file` → `rwxr-xr-x`

**The math:** r(4) + w(2) + x(1) = 7

`644` = Standard files

`755` = Executables

**Perfect for:** Setting all at once

</aside>

---

### 👥 The Ownership Trio

<aside>

**Who Owns What? Three Essential Commands:**

1. `chown user file` → Change the owner
2. `chgrp group file` → Change the group
3. `chown user:group file` → **Change both** (the winner! ⭐)

**Remember:** You usually need `sudo` to change ownership you don't have!

</aside>

---

### 🎭 The Special Powers: SUID, SGID, and Sticky Bit

This is where Linux gets **superpowers**. Three special bits that bend the rules:

<aside>

**4️⃣ SUID (Set User ID)**

**Symbol:** `s` in user position

**Magic:** Run as file owner

**Example:** `passwd` → You run as root temporarily!

`chmod u+s` or `chmod 4755`

</aside>

<aside>

**2️⃣ SGID (Set Group ID)**

**Symbol:** `s` in group position

**Magic:** Run as file group

**Bonus:** Directories inherit group!

`chmod g+s` or `chmod 2755`

</aside>

<aside>

**1️⃣ Sticky Bit**

**Symbol:** `t` in others position

**Magic:** Only owner can delete

**Example:** `/tmp` — everyone creates, none interfere!

`chmod +t` or `chmod 1777`

</aside>

---

### 🔐 The Permission Defense System

**Think of Linux permissions like a security checkpoint with three layers:**

1. **Default Security (umask):** Sets baseline for NEW files
    - `umask 022` → Files get `644`, directories get `755`
    - **Subtracts** permissions (opposite of chmod!)
    - Add to `.bashrc` to make permanent
2. **Process Identity (The Three UIDs):** Who's really running this?
    - **Real UID:** Who you actually are (your identity)
    - **Effective UID:** What permissions you're using right now (your power level)
    - **Saved UID:** Lets you switch between the two (your flexibility)
    
    **The passwd Story:** You're user 500, but `passwd` makes you temporarily root (UID 0) to edit `/etc/shadow`. Your Real UID stays 500, so you can only change YOUR password, not Sally's!
    
3. **Directory Protection (Sticky Bit):** The ultimate shared space guardian
    - Set on `/tmp`: `drwxrwxrwt`
    - Alice creates a file → Only Alice (or root) can delete it
    - Bob can create his own files but can't touch Alice's
    - **Perfect for team directories!**

---

### 🎯 The Quick Reference Matrix

| **What I Want** | **Command** | **Result** |
| --- | --- | --- |
| Standard file | `chmod 644 file` | `rw-r--r--` (owner edits, others read) |
| Executable script | `chmod 755 script` | `rwxr-xr-x` (owner edits, all run) |
| Private file | `chmod 600 file` | `rw-------` (owner only) |
| Shared team dir | `chmod 2775 dir` | `rwxrwsr-x` (group collaborates) |
| Public shared dir | `chmod 1777 dir` | `rwxrwxrwt` (all create, none interfere) |

---

## Part 2: SSH — Secure Remote Access

### 🔑 What is SSH?

**SSH (Secure Shell)** is your encrypted tunnel to remote systems. It replaces insecure protocols like Telnet and FTP with military-grade security.

**Why SSH matters:**

- **Encrypted communication** — No one can snoop on your session
- **Secure file transfers** — Using SCP and SFTP
- **Remote command execution** — Control servers from anywhere
- **Port forwarding** — Tunnel other services securely

---

### 🗝️ SSH Authentication: Two Methods

<aside>

**🔐 Password Authentication**

**Pros:** Simple, no setup

**Cons:** Vulnerable to brute force, typing passwords is tedious

**Usage:** `ssh user@hostname`

</aside>

<aside>

**🔑 Key-Based Authentication**

**Pros:** More secure, no passwords needed, automation-friendly

**Cons:** Initial setup required

**Usage:** Set up once, connect forever!

</aside>

---

### 🎯 SSH Key Generation — Your Digital Identity

**SSH keys work in pairs:**

- **Private Key** (`id_rsa`) — Your secret, never share! Stays on YOUR machine
- **Public Key** (`id_[rsa.pub](http://rsa.pub)`) — Your identity, share freely! Goes on remote servers

**The Magic:** Public key encrypts, only private key can decrypt. Mathematics ensures security!

**Generate your SSH key pair:**

```bash
ssh-keygen -t rsa -b 4096
```

**What this does:**

- `-t rsa` → Use RSA algorithm (industry standard)
- `-b 4096` → Use 4096-bit key (stronger than default 2048)
- Creates `~/.ssh/id_rsa` (private) and `~/.ssh/id_[rsa.pub](http://rsa.pub)` (public)

**View your public key:**

```bash
cat ~/.ssh/id_[rsa.pub](http://rsa.pub)
```

---

### 🚀 SSH Connection Flow

1. **Generate keys** on your local machine (one-time setup)
2. **Copy public key** to remote server's `~/.ssh/authorized_keys`
3. **Connect** with `ssh user@hostname`
4. **Server challenges** you with encrypted message
5. **Your private key** decrypts it, proving your identity
6. **Access granted** — no password needed!

---

### 🛡️ SSH Security Best Practices

<aside>

**🚨 Protect Your Private Key:**

- Never share your private key (`id_rsa`)
- Set strict permissions: `chmod 600 ~/.ssh/id_rsa`
- Use a passphrase for extra security (optional but recommended)
- Keep backups in secure locations
</aside>

<aside>

**✅ SSH Configuration Tips:**

- Store host configurations in `~/.ssh/config`
- Use meaningful key names for different servers
- Disable password authentication on servers (keys only)
- Use SSH agent to avoid typing passphrases repeatedly
</aside>

---

## ✅ Hands-On Practice (30 mins)

### Permission Exercises:

```bash
# Create a test folder
mkdir test-permissions

# Change permissions
chmod 755 test-permissions

# Create a file and set permissions
touch file.txt
chmod 644 file.txt

# View permissions
ls -la
```

![image.png](attachment:aa11bf39-b376-4879-9312-b2c6890ae61c:image.png)

### SSH Exercises:

```bash
# Generate SSH keys
ssh-keygen -t rsa -b 4096

# View your public key
cat ~/.ssh/id_[rsa.pub](http://rsa.pub)

# Check SSH directory permissions
ls -la ~/.ssh/
```

**Expected output structure:**

- `~/.ssh/` directory: `700` (drwx------)
- Private key `id_rsa`: `600` (-rw-------)
- Public key `id_[rsa.pub](http://rsa.pub)`: `644` (-rw-r--r--)

![image.png](attachment:7e584146-556b-45b3-a5f9-5684ad9b5667:image.png)

---

## 🧠 Memory Hooks for Quick Recall

**Remember "RWX-4-2-1":**

- **R**ead = **4** (like a square, stable base)
- **W**rite = **2** (two hands to write)
- e**X**ecute = **1** (one action to run)

**Remember "4-2-1" for special bits too:**

- **S**UID = **4** (Sudo power for user)
- s**G**id = **2** (Group gets the power)
- s**T**icky = **1** (The last line of defense)

**The `passwd` Mental Model:** Your all-time reference for understanding SUID and UIDs!

- You want to change password → run `passwd`
- Your Real UID: 500 (who you are)
- Your Effective UID: 0 (root power via SUID)
- Result: Can access root files BUT only modify your own password
- **This is Linux security perfection!**

**SSH Memory Hook — "Lock and Key":**

- **Private key** = Your house key (never give away!)
- **Public key** = Your lock (install everywhere you want access)
- Anyone can see the lock, but only YOUR key opens it!