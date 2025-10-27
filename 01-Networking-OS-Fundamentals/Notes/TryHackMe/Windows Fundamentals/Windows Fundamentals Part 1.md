### Windows Editions

- **History & Dominance:**
    - First released in **1985**.
    - Remains the **leading OS** for home and corporate use.
    - A frequent **target for hackers and malware** due to its popularity.

### 📌 Key Versions

- **Windows XP:**
    - Extremely popular, long lifespan.
    - End-of-life caused panic; organizations rushed to migrate.
- **Windows Vista:**
    - Major overhaul but plagued with issues.
    - Poor reception → quickly phased out.
- **Windows 7:**
    - Successor to XP, widely adopted.
    - Vendors scrambled to ensure compatibility.
    - Marked with a clear **end-of-support date**.
- **Windows 8.x:**
    - Short-lived, similar fate to Vista.
- **Windows 10:**
    - Stable successor, widely deployed.
    - Support continues until **October 14, 2025** (at least one Semi-Annual Channel).
- **Windows 11 (current desktop OS):**
    - Released **October 5, 2021**.
    - Editions: **Home** and **Pro**.

### 🖧 Server Editions

- Current: **Windows Server 2025**.
- Example VM noted: **Windows Server 2019 Standard**.

### 🔒 General Notes

- Microsoft has steadily improved **usability** and **security** with each release.
- Critics remain, but progress is evident across versions.

### The Desktop (GUI)

The **Windows Desktop** is the main graphical interface you see after logging into Windows 10. It provides access to applications, files, and system tools.

## 🔑 Login Screen

- Requires valid credentials (username & password).
- Can authenticate against a local account or Active Directory (if domain-joined).

## 🗂️ Desktop

- Holds shortcuts to programs, files, and folders for quick access.
- Customizable via right-click menu:
    - Change icon size, arrangement, or create new items.
    - Adjust **Display settings** (resolution, orientation, multi-monitor setup).
    - Personalize wallpaper, themes, fonts, and colors.
- Note: Some display options are limited in Remote Desktop sessions.

## 🪟 Start Menu

- Accessed via the **Windows logo** (bottom-left).
- Purpose: Central hub for apps, files, and utilities.
- **Sections**:
    1. **User & System Controls**: Account settings, lock, sign out, Documents, Pictures, Settings, Power options.
    2. **App List**: Recently added apps at the top; all installed apps listed alphabetically.
        - Alphabet grid allows quick navigation.
    3. **Tiles (Right Side)**: Pinned apps/utilities with customizable size and layout.
        - Right-click tiles to resize, unpin, or view properties.

## 📌 Taskbar

- Displays open apps, files, and folders.
- Features:
    - Hovering shows preview thumbnails and tooltips.
    - Items disappear when closed unless pinned.
    - Right-click for customization (enable/disable components like toolbars).

## 🔔 Notification Area

- Located at bottom-right of the screen.
- Shows **date/time**, **volume**, **network**, and other system icons.
- Icons can be added/removed via Taskbar settings.

## 💡 Tip

Right-clicking on most items (files, folders, apps, icons) opens a context menu with additional actions.

✅ **In essence**:

The Windows Desktop is a customizable workspace made up of the **Desktop, Start Menu, Taskbar, and Notification Area**, each designed to provide quick access to applications, settings, and system information.

### The File System

Modern Windows systems primarily use **NTFS**, which replaced older file systems like **FAT16/FAT32** and **HPFS**.

FAT is still common on removable media (USB drives, SD cards), but not typically on Windows installations.

## 🛠️ Key Features of NTFS

- **Journaling file system**: Uses a log file to automatically repair files/folders after failures (unlike FAT).
- **Large file support**: Handles files larger than 4GB (FAT32 limit).
- **Permissions**: Fine-grained access control on files/folders.
- **Compression**: Built-in file and folder compression.
- **Encryption**: Supports **EFS (Encrypting File System)** for data protection.

## 🔑 NTFS Permissions

Permissions can be set per file/folder to control access:

- **Full Control** – all actions allowed
- **Modify** – read, write, delete, and change
- **Read & Execute** – run programs and read data
- **List Folder Contents** – view folder structure
- **Read** – view contents only
- **Write** – add or modify content

📌 To view/edit permissions:

Right-click file/folder → **Properties** → **Security tab** → Select user/group.

## 🧩 Alternate Data Streams (ADS)

- Every file has at least one data stream (`$DATA`).
- ADS allows multiple streams of data in a single file.
- **Not visible in File Explorer**; can be viewed with PowerShell or third-party tools.
- **Uses**:
    - Malware can hide data in ADS (security risk).
    - Legitimate use: Windows tags downloaded files with Internet origin info.

✅ **In summary**:

NTFS is the default Windows file system, offering **reliability (journaling), scalability (large files), security (permissions & encryption), and flexibility (compression & ADS)**—making it far more advanced than FAT.

### The Windows\System32 Folders

- The **Windows folder** contains the **core operating system files**.
- By default, it resides on the **C drive**, but it can technically be located on another drive or in a different folder.
- The system environment variable **`%windir%`** always points to the Windows directory, regardless of its actual location.

## 🌍 Environment Variables

- Store information about the OS environment.
- Examples: OS path, number of processors, location of temp folders.
- `%windir%` specifically refers to the Windows installation directory.

## 📂 Key Subfolder: System32

- Located inside the Windows folder.
- Contains **critical system files and tools** required for Windows to function.
- **Caution**: Deleting or modifying files here can make Windows inoperable.
- Many **administrative tools** are stored in System32 (used in Windows Fundamentals learning).

✅ **In summary**:

The **Windows folder** is the backbone of the OS, with **System32** being its most critical subfolder. Environment variables like **`%windir%`** ensure the system can always locate it, no matter where it’s installed.

### User Accounts, Profiles, and Permissions

## 🔑 Account Types

- **Administrator**
    - Full control over the system.
    - Can add/remove users, modify groups, change system settings, and install programs.
- **Standard User**
    - Limited to managing their own files/folders.
    - Cannot perform system-level changes (e.g., install software).

## ⚙️ Managing Accounts

- Access via **Start Menu → Other Users** (System Settings).
- **Administrators** see the option to *Add someone else to this PC*; Standard Users do not.
- Options for each account:
    - **Change account type**
    - **Remove account**

## 📂 User Profiles

- Created automatically at first login.
- Stored under **C:\Users\Username** (e.g., `C:\Users\Max`).
- Profile creation is handled by the **User Profile Service** during first login.
- Each profile includes standard folders:
    - Desktop
    - Documents
    - Downloads
    - Music
    - Pictures

## 👥 Local Users and Groups (lusrmgr.msc)

- Open via **Run → lusrmgr.msc**.
- Contains two main folders:
    - **Users** – list of all local accounts.
    - **Groups** – predefined groups with specific permissions.
- Users inherit permissions from groups they are assigned to.
- A user can belong to multiple groups.

✅ **In summary**:

Windows systems have two main account types: **Administrators** (full control) and **Standard Users** (limited). Each account has a **profile under C:\Users**, and permissions can be managed through **Local Users and Groups**. Group membership determines what actions a user can perform beyond their base account type.

### User Account Control (UAC)

## ⚠️ Problem

- Most home users log in as **local administrators**.
- Admin accounts can make **system-level changes** (install software, modify settings, add/remove users).
- Running daily tasks (e.g., browsing, editing documents) with elevated privileges is unnecessary and risky.
- Malware executed under an admin account can **inherit those privileges**, making infections more severe.

## 🛡️ Microsoft’s Solution: UAC

- **Introduced in Windows Vista** and continued in later versions.
- **Purpose**: Prevent unauthorized system changes by requiring explicit user approval.
- **Exception**: UAC does **not apply** to the built-in Administrator account (by default).

## ⚙️ How UAC Works

1. When an **administrator logs in**, the session runs with **standard user privileges** by default.
2. If an action requires elevated rights (e.g., installing software, changing system settings):
    - A **UAC prompt** appears.
    - The user must **approve** (and sometimes enter credentials) before the action executes.
3. If no approval is given, the action is blocked.

## 🖼️ Indicators

- Programs requiring elevation display a **shield icon** on their executable.
- When launched, UAC prompts for confirmation:
    - If logged in as a standard user → must provide admin credentials.
    - If logged in as an admin → must confirm the action.

## ✅ Benefits

- Reduces the chance of malware silently making system changes.
- Ensures **user awareness** before critical operations run.
- Adds a **layer of defense** without removing admin capabilities.

**In summary**:

UAC balances usability and security by ensuring that even administrators run as **standard users by default**, only elevating privileges when explicitly approved. This helps protect Windows systems from accidental or malicious changes.

### Settings and the Control Panel

## 🖥️ Control Panel

- Traditional tool for system management (e.g., add printers, uninstall programs).
- Provides **advanced and complex settings**.
- Still present in Windows 10, though less emphasized.

## 📱 Settings Menu

- Introduced in **Windows 8** (touchscreen-focused).
- Now the **primary interface** for most system changes in Windows 10.
- Modern, simplified design compared to Control Panel.
- Icons and layout may vary by Windows version.

## 🔄 Relationship Between the Two

- Both accessible via the **Start Menu**.
- Some actions in **Settings** redirect to **Control Panel** (e.g., *Network & Internet → Change adapter options*).
- If unsure where a setting is located, use the **Start Menu search** (e.g., searching "wallpaper" opens the relevant Settings page).

✅ **In summary**:

- **Settings** = modern, user-friendly, primary hub for most changes.
- **Control Panel** = legacy tool for deeper, advanced configurations.
- They coexist, and sometimes navigating through Settings leads you into Control Panel for more detailed options.

### Task Manager

## 📌 Purpose

- Monitors **applications and processes** currently running.
- Provides **system performance data** (CPU, RAM usage, etc.).

## 🔑 Access

- Open by **right-clicking the taskbar**.

## 👀 Views

- **Simple View**: Minimal information.
- **More details**: Expanded view with detailed process and performance info.

## 📚 Further Learning

- Blog posts provide deeper insights into Task Manager.
- For detailed explanations of **core Windows processes**, refer to the *Core Windows Processes* learning module.

✅ **In summary**:

The **Task Manager** is a built-in Windows tool for monitoring running processes and system performance. It starts in a simplified view but can be expanded for detailed management and troubleshooting.
