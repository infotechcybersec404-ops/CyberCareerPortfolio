### Introduction

Part three, the final section of the Linux Fundamentals module, introduces practical utilities and applications for everyday use. It builds on earlier lessons by advancing skills in **automation, package management, and service/application logging**.

### Terminal Text Editors

- **Problem:** Using `echo` with `>` or `>>` is inefficient for editing multi‑line files.
- **Solution:** Use terminal text editors like **Nano** or **VIM**.

### **Nano**

- Beginner‑friendly, easy to start: `nano filename`
- Basic features:
    - Search text
    - Copy & paste
    - Jump to line numbers
    - Show current line number
- Common shortcut example: `Ctrl + X` to exit.
- Navigation with arrow keys, Enter for new lines.

### **VIM**

- More advanced, steeper learning curve.
- Benefits:
    - Highly customizable (shortcuts, configs)
    - Syntax highlighting (great for coding)
    - Available on all terminals (where Nano may not be)
    - Large community resources (cheatsheets, tutorials).

👉 In short: **Nano = simple and practical for everyday use. VIM = powerful, customizable, and favored by developers.**

### General/Useful Utilities

### **1. Downloading Files – `wget`**

- Retrieves files from the web via HTTP/HTTPS.
- Syntax: `wget <URL>`
- Example:
    
    ```bash
    wget https://example.com/myfile.txt
    ```
    

### **2. Transferring Files – `scp` (Secure Copy via SSH)**

- Securely copies files/directories between local and remote systems.
- Requires username, password, and IP of the remote system.
- **Local → Remote:**
    
    ```bash
    scp important.txt ubuntu@192.168.1.30:/home/ubuntu/transferred.txt
    ```
    
- **Remote → Local:**
    
    ```bash
    scp ubuntu@192.168.1.30:/home/ubuntu/documents.txt notes.txt
    ```
    

### **3. Serving Files – Python3 HTTP Server**

- Quickly share files by turning a directory into a web server.
- Start server in current directory:
    
    ```bash
    python3 -m http.server
    ```
    
- Accessible at `http://<IP>:8000/`
- Download from another machine with `wget`:
    
    ```bash
    wget http://<IP>:8000/filename
    ```
    
- Limitation: No indexing—must know exact filename.
- Alternative: **Updog** (more advanced lightweight web server).

👉 In short:

- **`wget`** = download from web.
- **`scp`** = secure file transfer between systems.
- **`python3 -m http.server`** = serve files locally for others to download.

### Processes 101

### What Are Processes?

- Processes = programs running on your machine.
- Managed by the **kernel**.
- Each process has a **PID (Process ID)**.
- PIDs increment in order of process creation (e.g., 60th process → PID 60).

### 🔍 Viewing Processes

- **`ps`** → shows processes for the current user session (PID, status, CPU time, command).
- **`ps aux`** → shows all processes (system + other users).
- **`top`** → real-time, auto-refreshing process statistics (updates every 10s or when navigating).

### ⚙️ Managing Processes

- Processes can be controlled with **signals** via the `kill` command:
    - `kill <PID>` → terminate a process.
    - **SIGTERM** → terminate, allow cleanup.
    - **SIGKILL** → force kill, no cleanup.
    - **SIGSTOP** → suspend/stop a process.

### 🖥️ How Processes Start

- **Namespaces** → isolate resources (CPU, RAM, etc.) for processes; improve security.
- **PID 0** → created at system boot (init/systemd).
- **systemd** → parent of most processes; manages user/system processes.
- New processes = **child processes** of systemd.

### 🚀 Starting Services on Boot

- Some apps (e.g., web servers, DBs) need to auto-start at boot.
- Managed with **systemctl** (systemd’s control tool):
    - `systemctl start <service>` → start service.
    - `systemctl stop <service>` → stop service.
    - `systemctl enable <service>` → auto-start on boot.
    - `systemctl disable <service>` → prevent auto-start.

### ⏯️ Foreground vs Background Processes

- **Foreground** → runs directly in terminal (e.g., `echo "Hi"`).
- **Background** → run with `&` or suspend with `Ctrl + Z`.
    - Background frees the terminal for other commands.
    - Useful for long-running tasks (e.g., file copy, scripts).
- **`fg`** → bring a backgrounded process back to the foreground.

✅ **In short:**

Processes are kernel-managed programs identified by PIDs. You can view them with `ps`/`top`, manage them with `kill` signals, and control services with `systemctl`. Processes can run in the foreground or background, giving flexibility in multitasking.

### Maintaining Your System: Automation

# ⏰ Linux Crontab & Scheduling Tasks

### 🔹 What is Cron/Crontab?

- **Cron** = background process that runs scheduled tasks.
- **Crontab** = special file with instructions for cron jobs.
- Crontab starts at boot and manages scheduled commands.

### 📑 Crontab Format

Each line in a crontab has **6 fields**:

| Field | Meaning |
| --- | --- |
| MIN | Minute to execute |
| HOUR | Hour to execute |
| DOM | Day of month |
| MON | Month of year |
| DOW | Day of week |
| CMD | Command to run |

### 🛠 Example

Backup user "cmnatic"’s Documents folder every 12 hours:

```
0 */12 * * * cp -R /home/cmnatic/Documents /var/backups/
```

- `/12` → every 12 hours.
- (wildcard) → "any value" (e.g., any day, any month).

### ✨ Key Features

- **Wildcard**  → run regardless of that field’s value.
- **Resources** → tools like *Crontab Generator* or *Cron Guru* help build schedules.
- **Editing** → use `crontab -e` to open and modify crontabs (choose editor like Nano).

✅ **In short:** Crontabs let you automate tasks (backups, app launches, commands) by defining when and how often they run, using a simple 6-field schedule format.

### Maintaining Your System: Package Management

### 🔹 What Are Repositories?

- Developers submit software to **apt repositories**.
- Once approved, tools become available to the community.
- Benefits: **user accessibility** + **open-source collaboration**.
- OS vendors maintain official repos, but users can also add **community/third-party repos** for more software.

### ⚙️ Managing Repositories

- **`apt`** = package management tool for installing, updating, and removing software.
- Repositories can be added via:
    - **`add-apt-repository`** (simpler method).
    - **Manual method** (editing sources list).

### 🔑 Security with GPG Keys

- **GPG keys** verify the authenticity of software.
- If the key doesn’t match trusted sources, the package won’t install.

### 📝 Example: Adding Sublime Text Repository

1. Add GPG key:
    
    ```bash
    wget -qO - https://download.sublimetext.com/sublimehq-pub.gpg | sudo apt-key add -
    ```
    
2. Create a new repo file:`/etc/apt/sources.list.d/sublime-text.list`
3. Add Sublime Text repo info inside the file.
4. Update apt:
    
    ```bash
    sudo apt update
    ```
    
5. Install software:
    
    ```bash
    sudo apt install sublime-text
    ```
    

### 🗑️ Removing Repositories & Packages

- Remove repo:

or delete the repo file manually.
    
    ```bash
    add-apt-repository --remove ppa:PPA_Name/ppa
    ```
    
- Remove package:
    
    ```bash
    sudo apt remove <package-name>
    ```
    

✅ **In short:**

Linux uses repositories to manage software. With `apt`, you can add trusted repos (secured by GPG keys), install software, and easily remove it later. This ensures both flexibility and security in managing applications.

### Maintaining Your System: Logs

- **Location:** `/var/log` directory stores logs for applications, services, and the OS.
- **Management:** Logs are automatically handled by the OS through **log rotation**.

### 🔹 Example Services & Their Logs

- **Apache2 (web server):**
    - `access.log` → records every request
    - `error.log` → records issues and failures
- **fail2ban:** tracks brute‑force attempts.
- **UFW (firewall):** logs firewall activity.

### 🔹 Purpose & Importance

- Monitor **system health** and **security**.
- Diagnose **performance issues**.
- Investigate **suspicious or malicious activity**.
- Track **OS operations** and **user actions** (e.g., authentication attempts).
