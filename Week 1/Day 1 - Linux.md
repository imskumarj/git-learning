# Notes - Day 1

## Linux: From UNIX to Modern Distributions

### The Story Begins: UNIX (1969)

- Ken Thompson and Dennis Ritchie created UNIX at Bell Labs  
- Revolutionary move: rewrote it in C → made it portable across different systems

### The Freedom Movement: GNU Project (1980s)

- Richard Stallman wanted a **free**, open-source alternative to UNIX  
- Created GNU tools and the GPL license for software freedom  
- Problem: GNU had everything *except* a working kernel

### The Missing Piece: Linux Kernel (1991)

- Linus Torvalds (Finnish student) created the Linux kernel as a hobby project  
- Perfect timing: Linux kernel + GNU tools = complete operating system  
- Birth of modern Linux: free, open-source, and powerful

### Understanding the System Structure

Linux systems work in three layers:

- **Hardware** → physical components  
- **Linux Kernel** → bridge managing hardware and software  
- **User Space** → where apps and user programs run

### What Makes a Distribution?

A Linux distro packages together:

- Linux kernel  
- System utilities & applications  
- Package manager  
- Desktop environment (GUI)

### Choosing Your Distribution

- **New to Linux?** Ubuntu, Linux Mint  
- **Want full control?** Arch Linux, Gentoo  
- **Desktop matters:** GNOME, KDE Plasma, XFCE  
- **Gaming / Modern features?** Look for Wayland support  
- **Package systems:** Debian-based (apt) vs Red Hat-based (dnf/yum)

### Bottom Line

There is no universal “best” Linux distro — choose based on your use-case.  
Try a Live USB before installing.

---

## Why Linux Matters for Cloud Computing

- **Industry standard:** Most cloud servers run Linux (AWS, Azure, GCP)  
- **Cost-effective:** No licensing fees  
- **Stable & lightweight:** Ideal for servers  
- **Automation-friendly:** Great for scripting, Docker, Kubernetes  
- **Secure:** Frequent updates, strong community support

---

## Linux File System Structure

Everything starts from `/` — the root of the filesystem tree.

### Key Directories

- **`/`** — root directory  
- **`/home`** — user directories  
- **`/etc`** — system & app configuration files  
- **`/var`** — logs, databases, variable data  
- **`/bin`** — essential system commands  
- **`/usr`** — user programs & utilities  
- **`/tmp`** — temporary files, cleared on reboot

---

## Essential Linux Commands

### Navigation

- `pwd` — print current directory  
- `cd /home/user` — move to directory  
- `cd ..` — go up one level  
- `cd ~` — go to home  
- `cd -` — go to previous directory

### Listing Files

- `ls` — list files  
- `ls -l` — long format  
- `ls -a` — show hidden files  
- `ls -lh` — human-readable sizes

### File & Directory Operations

- `mkdir folder` — create directory  
- `mkdir -p a/b/c` — create nested folders  
- `cat file.txt` — view file  
- `rm file.txt` — delete file  
- `rm -r folder` — delete folder recursively  
- `rm -rf folder` — force delete (**dangerous**)  

---

## Package Managers: Installing Software

### APT (Debian/Ubuntu)

- `sudo apt update`  
- `sudo apt upgrade`  
- `sudo apt install package_name`  
- `sudo apt remove package_name`  
- `apt search keyword`

### YUM/DNF (Red Hat/Fedora/CentOS)

- `sudo yum update` / `sudo dnf update`  
- `sudo yum install package_name` / `sudo dnf install package_name`  
- `sudo yum remove package_name` / `sudo dnf remove package_name`  
- `yum search keyword` / `dnf search keyword`

### Key Differences

- **APT:** Debian family (Ubuntu, Linux Mint)  
- **YUM:** Older Red Hat manager  
- **DNF:** Modern replacement for YUM  

Both work similarly — just for different families of Linux.

