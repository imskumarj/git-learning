# Linux Commands Cheatsheet

# 🐧 Linux Commands Cheatsheet

> Your complete reference for essential Linux commands — organized by operation type for quick navigation!
> 

---

## 📁 CRUD Operations (Files & Directories)

### Creating Files & Directories

**`touch`** — Create empty file or update timestamp

```
touch file.txt
touch file1.txt file2.txt
```

💡 Quick way to create empty files. Can create multiple at once.

**`mkdir`** — Create new directory

```
mkdir my_folder
mkdir -p folder1/folder2/folder3
```

💡 Use `-p` flag to create nested directories in one command

---

### Reading Files & Directories

**`pwd`** — Print working directory (shows current location)

```
pwd
```

💡 Essential for navigation. Always know where you are!

**`ls`** — List files and directories

```
ls              # basic list
ls -l           # detailed view
ls -a           # show hidden files
ls -lh          # human-readable sizes
```

💡 `-l` = detailed list | `-a` = show hidden files | `-h` = human-readable sizes

**`cat`** — Display file contents

```
cat file.txt
cat file1.txt file2.txt
```

💡 Best for small files. Can concatenate multiple files.

**`less`** — Display file contents one page at a time

```
less file.txt
```

💡 More advanced than cat for viewing larger files. Navigate with arrow keys, press 'q' to exit.

**`grep`** — Search text patterns in files

```
grep 'pattern' file.txt
ps aux | grep nginx
```

💡 Essential for filtering output. Often used with pipes |

**`find`** — Search for files and directories

```
find / -perm -4000          # find SUID files (security audit!)
find . -name '*.txt'        # find all .txt files
```

💡 Powerful search tool for locating files by name, permissions, size, etc.

**`man`** — Display manual pages for commands

```
man ls
man chmod
```

💡 Your built-in documentation. Press 'q' to quit. Essential for learning!

---

### Updating Files & Directories

**`mv`** — Move or rename files and directories

```
mv file.txt newname.txt
mv file.txt /path/to/destination/
```

💡 Used for both moving AND renaming files

**`cp`** — Copy files and directories

```
cp file.txt copy.txt
cp -r directory new_directory
```

💡 The `-r` option copies directories recursively.

**`cd`** — Change directory (navigate)

```
cd /home/user       # go to specific directory
cd ..               # go up one level
cd ~                # go to home directory
cd -                # go back to previous directory
```

💡 Master of navigation!

---

### Deleting Files & Directories

**`rm`** — Remove files or directories

```
rm file.txt
rm -r folder
rm -rf folder
```

⚠️ **DANGER**: `-rf` forces deletion without confirmation. Be careful!

---

## 🔐 Permissions & Ownership

### Understanding Permission Numbers

**The RWX-4-2-1 System:**

- **Read (r)** = 4
- **Write (w)** = 2
- **eXecute (x)** = 1

**Common Permission Patterns:**

- `755` = `rwxr-xr-x` — Standard for executables/directories
- `644` = `rw-r--r--` — Standard for regular files
- `777` = `rwxrwxrwx` — ⚠️ **AVOID!** Everyone can do everything
- `700` = `rwx------` — Owner only (sensitive files)
- `600` = `rw-------` — Owner read/write only (private files)

---

### Basic Permission Commands

**`chmod`** — Change file/directory permissions

```
# Numeric (Octal) Method
chmod 755 [script.sh](http://script.sh)         # rwxr-xr-x
chmod 644 file.txt          # rw-r--r--

# Symbolic Method
chmod u+x file              # give owner execute
chmod g-w file              # remove group write
chmod o=r file              # set others to read-only
```

💡 Numeric for speed, symbolic for precision!

**`chown`** — Change file owner and group

```
chown user file
chown user:group file       # ⭐ Change both at once
```

💡 Use `user:group` format to change both at once. Requires sudo.

**`chgrp`** — Change group ownership

```
chgrp groupname file
```

💡 Better to use `chown user:group` instead

**`umask`** — Set default permissions for newly created files

```
umask 022                   # Files get 644, dirs get 755
umask                       # view current umask
```

💡 umask 022 → Files get 644, directories get 755. Add to `.bashrc` for persistence.

---

### Special Permission Bits

**`chmod u+s`** — Set SUID (Set User ID) bit

```
chmod u+s file
chmod 4755 file
```

⚠️ **POWERFUL**: File runs with owner's permissions. Example: `passwd` command runs as root!

**`chmod g+s`** — Set SGID (Set Group ID) bit

```
chmod g+s directory
chmod 2755 directory
```

💡 On directories: new files inherit group. Perfect for team collaboration!

**`chmod +t`** — Set sticky bit

```
chmod +t directory
chmod 1777 directory
```

💡 Only file owner can delete their files. Example: `/tmp` directory

---

## 🌐 Networking & Remote Access

### SSH (Secure Shell)

**`ssh-keygen`** — Generate SSH key pairs for secure authentication

```
ssh-keygen -t rsa -b 4096
```

💡 Creates private key (`id_rsa`) and public key (`id_[rsa.pub](http://rsa.pub)`) in `~/.ssh/`

🔒 **Never share your private key!**

**`ssh`** — Connect to remote systems securely

```
ssh user@hostname
ssh user@192.168.1.100
```

💡 Encrypted tunnel for remote access. Use SSH keys for better security!

**SSH Key Workflow:**

1. Generate keys: `ssh-keygen -t rsa -b 4096`
2. View public key: `cat ~/.ssh/id_[rsa.pub](http://rsa.pub)`
3. Copy public key to remote server's `~/.ssh/authorized_keys`
4. Connect: `ssh user@hostname` (no password needed!)

**SSH Security Best Practices:**

- 🔒 Private key permissions: `chmod 600 ~/.ssh/id_rsa`
- 🔒 SSH directory permissions: `chmod 700 ~/.ssh`
- 🔒 Never share your private key
- 🔒 Use passphrases for extra security

---

## 📦 Package Management

### APT (Debian/Ubuntu)

**`sudo apt update`** — Refresh package list

```
sudo apt update
```

💡 Always run before installing new packages. Updates package database.

**`sudo apt upgrade`** — Update installed packages

```
sudo apt upgrade
```

💡 Upgrades all installed packages to latest versions

**`sudo apt install`** — Install new software

```
sudo apt install package_name
sudo apt install nginx
```

💡 Main way to install software on Ubuntu/Debian systems

**`sudo apt remove`** — Uninstall software

```
sudo apt remove package_name
```

💡 Removes package but keeps configuration files

**`apt search`** — Search for packages

```
apt search keyword
```

💡 Find available packages. No sudo needed.

---

### YUM/DNF (Red Hat/Fedora/CentOS)

**`sudo yum update`** — Update packages (older systems)

```
sudo yum update
```

💡 Being replaced by DNF. Used on Red Hat based systems.

**`sudo dnf update`** — Update packages (modern)

```
sudo dnf update
```

💡 Modern replacement for YUM with better performance

**Common pattern:**

- YUM/DNF commands mirror APT: `install`, `remove`, `search`
- Just replace `apt` with `yum` or `dnf`

---

## ⚙️ Process & Service Control

### systemctl — Service Management

**Key Concept: Enable vs Start**

- **`enable`** = Auto-start on boot (doesn't start now)
- **`start`** = Start immediately (doesn't persist across reboot)
- **Best practice:** Use both! `sudo systemctl enable --now service_name`

---

### Service Status & Monitoring

**`systemctl status`** — Check service status

```
systemctl status service_name
systemctl status sshd
```

💡 Shows if service is running, stopped, or failed

**`systemctl is-enabled`** — Check if service auto-starts on boot

```
systemctl is-enabled service_name
```

💡 Returns enabled/disabled status

**`systemctl list-units`** — List active services

```
systemctl list-units --type=service
```

💡 Shows all currently active services on the system

**`systemctl list-sockets`** — List sockets for IPC

```
systemctl list-sockets
systemctl --show-types list-sockets --all
```

💡 Shows sockets available for interprocess communication

---

### Service Lifecycle Management

**`systemctl start`** — Start a service immediately

```
sudo systemctl start service_name
sudo systemctl start nginx
```

💡 Requires sudo. Starts service right now but won't persist across reboot.

**`systemctl stop`** — Stop a running service

```
sudo systemctl stop service_name
```

💡 Requires sudo. Stops service immediately.

**`systemctl restart`** — Restart a service

```
sudo systemctl restart service_name
```

💡 Essential after configuration changes. Requires sudo.

**`systemctl enable`** — Enable service to start on boot

```
sudo systemctl enable service_name
```

⚠️ **Does NOT start service now!** Only enables auto-start on boot. Requires sudo.

**`systemctl disable`** — Disable service from starting on boot

```
sudo systemctl disable service_name
```

💡 Prevents auto-start on boot. Requires sudo.

---

### Logging & Debugging

**`journalctl`** — View system logs

```
journalctl -u service_name          # logs for specific service
journalctl -u nginx -n 50           # last 50 entries
journalctl -u sshd --since today    # today's logs
```

💡 `-u` = specific service | `-n` = number of entries | Essential for debugging!

**`ps aux`** — Display running processes

```
ps aux
ps aux | grep service_name
```

💡 Shows all processes with details. Pipe to grep to filter specific processes.

---

### System Control

**`systemctl poweroff`** — Shut down the system

```
sudo systemctl poweroff
```

💡 Clean shutdown of the system. Requires sudo.

**`systemctl reboot`** — Reboot the system

```
sudo systemctl reboot
sudo systemctl -i reboot            # ignore logged-in users
```

💡 `-i` flag ignores logged-in users. Requires sudo.

---

## 🎯 Common Services to Practice With

- **`ssh`** / **`sshd`** — SSH server
- **`nginx`** — Web server
- **`apache2`** — Apache web server
- **`mysql`** — MySQL database
- **`postgresql`** — PostgreSQL database

---

## 🧠 Quick Reference: Memory Hooks

### Permission Numbers (RWX-4-2-1)

- **R**ead = **4** (like a square, stable base)
- **W**rite = **2** (two hands to write)
- e**X**ecute = **1** (one action to run)

### Special Bits (4-2-1)

- **S**UID = **4** (Sudo power for user)
- s**G**id = **2** (Group gets the power)
- s**T**icky = **1** (The last line of defense)

### SSH Keys (Lock and Key)

- **Private key** = Your house key (never give away!)
- **Public key** = Your lock (install everywhere you want access)
- Anyone can see the lock, but only YOUR key opens it!

### The `passwd` Mental Model

When you run `passwd`:

- Your Real UID: 500 (who you are)
- Your Effective UID: 0 (root power via SUID)
- Result: Can access root files BUT only modify your own password
- **This is Linux security perfection!**

---

## ✅ Golden Rules

### Security First 🚨

1. **Never** use `chmod 777` on important files
2. **Never** share your SSH private key
3. **Least Privilege Principle:** Give only what's needed
4. **Audit SUID files:** `find / -perm -4000`
5. **Protect SSH:** `chmod 700 ~/.ssh` and `chmod 600 ~/.ssh/id_rsa`

### Best Practices ✨

- Use `chmod 644` for regular files
- Use `chmod 755` for directories and executables
- Use `chmod 700` for sensitive data
- Use SSH keys instead of passwords
- Set SGID on team directories for automatic group inheritance
- Set sticky bit on shared temp directories
- Always use `chown user:group` to change both at once
- Run `systemctl enable --now` to enable AND start services

---

## 🎓 What You've Mastered

✅ CRUD operations for files and directories

✅ Permission management (symbolic + numeric)

✅ Special permission bits (SUID, SGID, sticky)

✅ SSH setup and secure authentication

✅ Package management (APT and YUM/DNF)

✅ Service lifecycle with systemctl

✅ System logging and debugging

✅ Process monitoring

**You're now equipped with Linux fundamentals!** 🏆