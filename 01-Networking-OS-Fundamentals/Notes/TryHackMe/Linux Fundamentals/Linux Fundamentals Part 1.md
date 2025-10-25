### Introduction

## 💻 What is an Operating System?

An **operating system** is the software layer that:

- Manages hardware (CPU, memory, storage, devices)
- Provides a user interface (graphical or command-line)
- Runs applications and services

Examples you may already know:

- **Windows** (by Microsoft)
- **MacOS** (by Apple)
- **iOS** (for iPhones and iPads)
- **Android** (built on Linux)

## 🐧 Why Linux?

Linux is one of the most widely used operating systems in the world. It powers:

- 🚗 **Smart cars**
- 📱 **Android devices**
- 🖥️ **Supercomputers**
- 🏠 **Home appliances**
- 🏢 **Enterprise servers**
- ☁️ **Cloud infrastructure**

Its popularity comes from being:

- **Open-source** (free to use and modify)
- **Flexible** (runs on everything from tiny devices to massive servers)
- **Stable & secure** (trusted by enterprises and developers worldwide)

### A Bit of Background on Linux

- **Linux vs. Windows**: Linux may seem more intimidating than Windows, but it’s lightweight and widely used in everyday life.
- **Common Uses**:
    - Websites and web servers
    - Car infotainment/control systems
    - Point of Sale (PoS) systems in shops
    - Critical infrastructure (traffic lights, industrial sensors)
- **Flavours of Linux**:
    - “Linux” refers to many distributions (distros) built on UNIX.
    - Being open-source, it comes in different forms tailored to specific needs.
    - Popular examples: **Ubuntu** and **Debian**, which can run as servers or desktops.
- **Efficiency**: Ubuntu Server can run on as little as **512MB RAM**.
- **Versions**: Just like Windows has versions (7, 8, 10), Linux has multiple distributions.

👉 In short: **Linux is everywhere—from servers to cars—and its many open-source distributions make it flexible, lightweight, and powerful.**

### Running Your First few Commands

- **Lightweight OS trade-off**: Systems like Ubuntu are efficient but often lack a GUI (desktop environment). Instead, users interact through the **Terminal**.
- **Terminal basics**:
    - Text-based interface, intimidating at first but becomes familiar with practice.
    - Essential for tasks like navigating files, viewing contents, and creating files.
- **Introductory commands**:
    - `echo` → Outputs text (quotes needed if spaces are included).
    - `whoami` → Displays the current logged-in user.

👉 In short: **Ubuntu’s lightweight design often relies on the Terminal, where simple commands like `echo` and `whoami` form the foundation for interacting with the system.**

### Interacting With the Filesystem!

- **Beyond Basics**: After learning `echo` and `whoami`, the next step is navigating and interacting with the filesystem.

### Key Commands

| Command | Full Name | Purpose |
| --- | --- | --- |
| `ls` | listing | Shows files/folders in a directory |
| `cd` | change directory | Moves into a different directory |
| `cat` | concatenate | Outputs the contents of a file |
| `pwd` | print working directory | Displays the full path of the current directory |

### How They’re Used

- **`ls`** → Lists contents of the current (or specified) directory.
- **`cd`** → Changes into a chosen directory (e.g., `cd Pictures`).
- **`cat`** → Displays file contents (e.g., `cat todo.txt`). Can also be used with full paths.
- **`pwd`** → Prints the absolute path of the current working directory (e.g., `/home/ubuntu/Documents`).

### Why It Matters

- These commands allow you to **navigate without a GUI**, view files, and understand where you are in the filesystem.
- They form the foundation for working effectively in Linux environments.

👉 In short: **`ls`, `cd`, `cat`, and `pwd` are essential commands for navigating, locating, and reading files in Linux when working without a desktop environment.**

### Searching for Files

### Efficiency in Linux

- Linux becomes powerful once you’re familiar with its commands.
- Efficiency comes from using tools like `find` and `grep` instead of manually browsing directories or files.

### 🗂 Using `find`

- **Purpose:** Locate files across directories without manually using `cd` and `ls`.
- **Basic usage:**
    - Search by filename:
    
    → Finds `passwords.txt` in the directory tree.
        
        ```bash
        find -name passwords.txt
        ```
        
    - Search by extension (wildcards):
    
    → Lists all `.txt` files (e.g., `passwords.txt`, `todo.txt`).
        
        ```bash
        find -name *.txt
        ```
        
- **Benefit:** Saves time when searching through nested directories.

### 📑 Using `grep`

- **Purpose:** Search inside files for specific text or patterns.
- **Example scenario:** Searching a web server’s `access.log` with 244 entries.
- **Basic usage:**
    - Count lines in a file:
        
        ```bash
        wc -l access.log
        ```
        
    - Search for entries containing a specific IP:
    
    → Displays all log entries related to that IP.
        
        ```bash
        grep "81.143.211.90" access.log
        ```
        
- **Benefit:** Quickly extracts relevant information from large files.

### ✅ Key Takeaways

- `find` = locate files by name or pattern.
- `grep` = search file contents for specific values.
- Together, they make Linux workflows far more efficient than manual searching.

### An Introduction to Shell Operators

Linux operators enhance efficiency by controlling how commands run and how their outputs are handled. Four key operators are:

| Operator | Function | Example | Notes |
| --- | --- | --- | --- |
| `&` | Runs a command in the **background** | `cp largefile.txt backup/ &` | Lets you continue using the terminal while the process runs. |
| `&&` | Runs multiple commands **sequentially**; the second runs **only if** the first succeeds | `mkdir test && cd test` | Useful for chaining dependent commands. |
| `>` | **Redirects output** to a file (overwrites existing content) | `echo hey > welcome` | Creates/overwrites `welcome` with "hey". |
| `>>` | **Appends output** to a file (does not overwrite) | `echo hello >> welcome` | Adds "hello" to the end of `welcome`. |

### ✅ Key Takeaways

- `&` = multitasking (background processes).
- `&&` = conditional chaining of commands.
- `>` = redirect and overwrite file contents.
- `>>` = redirect and append to file contents.

### Conclusions & Summaries

This stage introduced the **core skills** you’ll use frequently when working with Linux:

- 🌍 **Why Linux is so common** → its widespread use and importance.
- 💻 **First interaction** → getting hands-on with a Linux machine.
- ⚡ **Fundamental commands** → practicing the basics of command-line usage.
- 📂 **Filesystem navigation** → moving around directories efficiently.
- 🔎 **Searching tools** → using `find` and `grep` to quickly locate files and data.
- 🔧 **Shell operators** → enhancing commands with operators like `&`, `&&`, `>`, and `>>`.

✅ **Key takeaway:** These are the building blocks of Linux. With frequent use, they’ll quickly become second nature.
