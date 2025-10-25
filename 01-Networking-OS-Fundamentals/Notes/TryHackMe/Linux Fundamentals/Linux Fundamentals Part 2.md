### Introduction

Part 2 of the **Linux Fundamentals** series builds on the basics from Part 1 and introduces more advanced, practical skills:

- 🌐 **Remote access** → Learn how to log in to and control remote machine terminals (moving beyond in-browser practice).
- ⚙️ **Flags & arguments** → Enhance commands by adding options for more powerful usage.
- 📂 **Filesystem operations** → Practice copying and moving files for better file management.
- 🔒 **Permissions** → Understand how access to files and folders is controlled and how to check your own access rights.
- 📜 **Scripts & executables** → Run your first scripts and executable files.

✅ **Key takeaway:** Part 2 transitions from basic Linux interaction to **real-world system management skills**, focusing on remote access, command flexibility, file operations, permissions, and automation.

### Accessing Your Linux Machine Using SSH (Deploy)

### 🌐 What is SSH?

- **SSH (Secure Shell):** A protocol for securely connecting to and controlling remote machines via the command line.
- **How it works:**
    - Encrypts human-readable input before sending it over the network.
    - Decrypts it on the remote machine.
- **Key benefits:**
    - Remote command execution.
    - Encrypted communication over the internet.

### 🖥️ Machines Used

1. **Your Linux Machine** – deployed for practice.
2. **TryHackMe AttackBox** – a cloud-hosted Ubuntu machine accessible in-browser, used to connect to your Linux machine.

### ⚙️ Deployment Steps

1. **Start Linux Machine** → Click **Start Machine** → Note the **IP address** shown.
2. **Start AttackBox** → Click **Start AttackBox** at the top of the page → Opens a browser-based Ubuntu environment.

### 🔐 Using SSH to Connect

- **Requirements:**
    1. IP address of the target machine.
    2. Valid credentials (username + password).
- **Credentials for this task:**
    - Username: `tryhackme`
    - Password: `tryhackme`
- **Command syntax:**
    
    ```bash
    ssh username@IP_address
    ```
    
    Example:
    
    ```bash
    ssh tryhackme@10.201.62.222
    ```
    
- **Login process:**
    - Open the **Terminal** on the AttackBox.
    - Run the SSH command with the given IP.
    - Accept the host trust prompt.
    - Enter the password (note: no visible feedback while typing).

### ✅ Once Connected

- All commands entered will execute **on the remote Linux machine**, not the AttackBox.

### Introduction to Flags and Switches

- **Arguments (Flags/Switches)**
    - Most commands accept arguments, identified with a **hyphen (-)** or **double hyphen (--)**.
    - These modify or extend the default behavior of commands.
- **Default Behavior Example**
    - `ls` → lists contents of the current directory.
    - By default, hidden files (those starting with `.`) are not shown.
- **Using Flags**
    - `ls -a` (or `ls --all`) → shows all files, including hidden ones.
    - Flags can drastically change or extend command output.
- **Help Option**
    - `command --help` → lists available options, descriptions, and usage examples.
    - Example: `ls --help` shows options like `a`, `A`, `-author`, etc.
- **Manual Pages (man pages)**
    - Provide detailed documentation for commands and applications.
    - Access with: `man <command>` (e.g., `man ls`).
    - Includes sections like **NAME, SYNOPSIS, DESCRIPTION, OPTIONS**.
    - More comprehensive than `-help`.

### 📌 Quick Reference

| Command | Purpose |
| --- | --- |
| `ls` | List directory contents |
| `ls -a` | Show all files, including hidden ones |
| `ls --help` | Show available options and usage examples |
| `man ls` | Open manual page for `ls` |

### Filesystem Interaction Continued

### 🔧 Core Commands

| Command | Full Name | Purpose |
| --- | --- | --- |
| `touch` | touch | Create a blank file |
| `mkdir` | make directory | Create a folder |
| `cp` | copy | Copy a file or folder |
| `mv` | move | Move or rename a file/folder |
| `rm` | remove | Delete a file/folder (`-R` for dirs) |
| `file` | file | Identify the type of a file |

### 📝 Creating Files & Folders

- **File**: `touch filename` → creates an empty file.
    - Add content later with `echo`, `nano`, etc.
- **Folder**: `mkdir foldername` → creates a new directory.

### 🗑 Removing Files & Folders

- **File**: `rm filename` → deletes a file.
- **Folder**: `rm -R foldername` → deletes a directory recursively.

### 📑 Copying & Moving

- **Copy**: `cp source target`
    - Example: `cp note note2` → duplicates `note` into `note2`.
- **Move/Rename**: `mv source target`
    - Example: `mv note2 note3` → renames `note2` to `note3`.
    - Can also move files into directories.

### 🔍 Determining File Type

- **Command**: `file filename`
- Identifies actual file type (e.g., ASCII text), regardless of extension.
- Useful since Linux files don’t require extensions.

👉 This section builds on basics (`ls`, `cd`, `find`) by teaching how to **create, organize, remove, copy, move, and inspect files/folders**.

### Permissions 101

### 📂 File Permissions

- Use `ls -l` (or `ls -lh`) to view file details.
- First **three columns** are key:
    - **Permissions** → what actions are allowed (read `r`, write `w`, execute `x`).
    - **Owner** → the user who owns the file.
    - **Group** → group of users who may also have permissions.
- Permissions can differ for **owner, group, and others**.
- Example:
    
    ```
    -rw-r--r-- 1 cmnatic cmnatic ...
    ```
    
    - Owner: read/write
    - Group: read
    - Others: read

### 👥 Users vs. Groups

- **Owner**: individual user who created/owns the file.
- **Group**: collection of users with shared permissions.
- Linux allows **granular control** → groups can have different permissions than the owner.
- Example: web servers need access to files, but hosting companies allow customers to upload files without giving them server-level access.

### 🔄 Switching Between Users

- Command: `su <username>`
    - Requires **target username** + **password**.
- Variants:
    - `su user2` → switches user but keeps current environment (e.g., stays in old home directory).
    - `su -l user2` (or `su --login user2`) → full login shell, loads new user’s environment, starts in their home directory.
- Useful for testing permissions or working as different system users.

👉 This section introduces **permissions (r, w, x)**, explains **users vs. groups**, and shows how to **switch accounts with `su`** for proper access control.

### Common Directories

### 🔧 `/etc` (Configuration Files)

- Stores **system configuration files** used by the OS.
- Key files:
    - `sudoers` → defines which users/groups can run commands as root.
    - `passwd` & `shadow` → store user account info and encrypted passwords (SHA512).

### 📊 `/var` (Variable Data)

- Holds **frequently changing data** used by services/apps.
- Common contents:
    - `/var/log` → system & application logs.
    - `/var/backups`, `/var/tmp`, `/var/opt` → backups, temporary data, optional app data.
- Often used for **databases, caches, and logs**.

### 👑 `/root` (Root User Home)

- Home directory for the **root (superuser)** account.
- Equivalent to `/home/<username>` for normal users, but dedicated to root.
- Stores root’s personal files and configs.

### ⚡ `/tmp` (Temporary Files)

- Used for **short-lived, temporary data**.
- Cleared automatically on reboot.
- **Writable by all users** → useful for testing, scripts, or pentesting tasks.

👉 Together, these directories handle **system configs (`/etc`)**, **dynamic data (`/var`)**, **root’s environment (`/root`)**, and **temporary storage (`/tmp`)**.

### Conclusions and Summaries

### 🔑 Key Concepts Learned

- **Remote Access**
    - Connect to a Linux machine using **SSH** for secure remote management.
- **Command Mastery**
    - Extend commands with **flags/switches** (e.g., `ls -a`, `ls -l`).
    - Learn more about commands via **`-help`** and **man pages**.
- **Filesystem Interaction**
    - Create: `touch`, `mkdir`
    - Remove: `rm`, `rm -R`
    - Copy/Move: `cp`, `mv`
    - Inspect: `file`
    - Navigate: `cd`, `ls`, `find`
- **Permissions & Users**
    - Understand **read (r), write (w), execute (x)** permissions.
    - Distinguish between **user, group, others**.
    - Switch users with `su` (and `su -l` for full login shell).
- **Important Directories**
    - `/etc` → system configs (e.g., `sudoers`, `passwd`, `shadow`).
    - `/var` → variable data (logs, databases, caches).
    - `/root` → home directory of the root user.
    - `/tmp` → temporary, auto-cleared storage (writable by all).

### 📌 Takeaway

This room built a **foundation in Linux essentials**:

- Remote access
- Command usage with options
- Filesystem management
- Permissions & user control
- Core system directories

👉 Repetition and practice will make these commands second nature.
