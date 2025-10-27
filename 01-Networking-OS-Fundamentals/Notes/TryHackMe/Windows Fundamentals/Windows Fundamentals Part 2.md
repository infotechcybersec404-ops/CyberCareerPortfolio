### System Configuration

## 📌 Purpose

- A Windows utility for **advanced troubleshooting**.
- Main role: **diagnose startup issues**.
- Requires **administrator rights** to open.

## 🚀 Access

- Can be launched from the **Start Menu** (among other methods).

## 🗂️ Tabs Overview

1. **General**
    - Choose what loads at startup:
        - **Normal** – all drivers/services.
        - **Diagnostic** – basic drivers/services only.
        - **Selective** – customize what loads.
2. **Boot**
    - Configure **boot options** for the operating system.
3. **Services**
    - Lists **all services** (running or stopped).
    - Services = background applications.
4. **Startup**
    - Displays startup items.
    - Microsoft recommends using **Task Manager** (`taskmgr`) to enable/disable them.
    - Note: Some environments (like certain VMs) may not show the Startup tab in Task Manager.
5. **Tools**
    - Provides a list of **system utilities** with descriptions.
    - The **Selected command** box shows the command to launch each tool.
    - Tools can be run via Run prompt, Command Prompt, or the **Launch** button.

✅ **In summary**:

MSConfig is a **diagnostic tool** that helps control startup behavior, configure boot options, view/manage services, and access system utilities. It is **not a startup manager**—that role belongs to Task Manager.

### Change UAC Settings

- **UAC (User Account Control)** was previously explained in detail.
- Through the **System Configuration → Tools tab**, you can access UAC settings.
- The UAC level can be adjusted using a **slider**:
    - Higher = more prompts, stronger protection.
    - Lower = fewer prompts, weaker protection.
- **Turning UAC off entirely is possible but not recommended** by Microsoft.

✅ **In short**: MSConfig’s Tools tab provides access to UAC settings, where you can adjust the security level with a slider, though disabling it is discouraged.

### Computer Management

The **Computer Management** utility is accessible through the **System Configuration (MSConfig) → Tools tab**.

It has **three main sections**: **System Tools, Storage, and Services and Applications**.

## 🔧 System Tools

- **Task Scheduler**
    - Automates tasks (apps, scripts, etc.).
    - Can run at login, logoff, or on a schedule (e.g., every 5 minutes).
    - Create tasks via **Create Basic Task** in the Actions pane.
- **Event Viewer**
    - Provides an **audit trail** of system events.
    - Useful for diagnosing problems and investigating activity.
    - Layout:
        - Left pane → event log providers (tree view).
        - Middle pane → overview/summary of selected events.
        - Right pane → actions.
    - Logs include **five event types** and **standard Windows logs** (Application, Security, System, etc.).
- **Shared Folders**
    - Lists all shared folders and resources.
    - Default shares: **C$**, **ADMIN$**.
    - Subsections:
        - **Shares** → list of shared folders.
        - **Sessions** → users currently connected.
        - **Open Files** → files/folders in use by connected users.
- **Local Users and Groups**
    - Same as **lusrmgr.msc**.
    - Manage users, groups, and permissions.
- **Performance (Performance Monitor / perfmon)**
    - Displays performance data in real-time or from logs.
    - Useful for troubleshooting system performance locally or remotely.
- **Device Manager**
    - View and configure hardware.
    - Can disable/enable devices.

## 💾 Storage

- **Disk Management**
    - Perform advanced storage tasks:
        - Set up new drives.
        - Extend/shrink partitions.
        - Assign/change drive letters.
    - Note: Windows Server includes extra storage tools not typically found in Windows 10.

## ⚙️ Services and Applications

- **Services**
    - Manage background services.
    - Can start, stop, enable/disable, and view service properties.
- **WMI Control**
    - Configures **Windows Management Instrumentation (WMI)**.
    - WMI allows scripting (VBScript, PowerShell) to manage Windows locally/remotely.
    - **WMIC command-line tool is deprecated** (Windows 10, version 21H1).
    - PowerShell is the modern replacement.

✅ **In summary**:

**Computer Management** is a central console for managing system tasks, logs, shares, users, performance, hardware, storage, and services. It consolidates many administrative tools into one interface, making it a key utility for Windows troubleshooting and system administration.

### System Information

- **Purpose**: Collects and displays detailed information about a computer’s hardware, system components, and software environment.
- **Use Case**: Helpful for diagnosing computer issues and reviewing system specifications.

## 📂 Main Sections in System Summary

1. **Hardware Resources**
    - Displays low-level technical details (not typically useful for average users).
    - For deeper exploration, Microsoft’s official documentation is recommended.
2. **Components**
    - Shows information about installed hardware devices.
    - Some subsections may be empty, but others (e.g., **Display**, **Input**) provide useful details.
3. **Software Environment**
    - Lists OS-level and installed software details.
    - Includes **Environment Variables**, **Network Connections**, and other system data.

## 🌐 Environment Variables

- **Definition**: Store information about the OS environment (e.g., system paths, processor count, temp folder locations).
- **Example**: `WINDIR` variable points to the Windows installation directory.
- **Access Methods**:
    - **Control Panel** → System and Security → System → Advanced system settings → Environment Variables
    - **Settings** → System → About → System info → Advanced system settings → Environment Variables

## 🔎 Extra Feature in msinfo32

- **Search Bar** (bottom of the utility):
    - Allows quick lookups.
    - Example: Select **Components** and search for **IP address** to find network-related details.

✅ **In short**: *msinfo32* is a built-in Windows diagnostic tool that organizes system details into **Hardware Resources**, **Components**, and **Software Environment**, with a search function for quick queries like IP address.

### Resource Monitor

- **Purpose**: Displays detailed, real-time information about system performance and resource usage.
- **Scope**: Shows both **per-process** and **aggregate** usage for CPU, memory, disk, and network.
- **Audience**: Primarily for **advanced users** performing in-depth troubleshooting.

## 🔍 Key Features

- Monitors **CPU, Memory, Disk, and Network** activity.
- Identifies which processes are using **file handles** and **modules**.
- **Advanced filtering**: Isolate data for one or more processes.
- Manage services: **Start, stop, pause, resume** directly from the interface.
- Close **unresponsive applications**.
- **Process analysis**: Detects deadlocks and file-locking conflicts, helping resolve issues without data loss.

## 📊 Interface Layout

- **Overview tab**: Summarizes activity across four sections:
    - **CPU**
    - **Memory**
    - **Disk**
    - **Network**
- **Dedicated tabs**: Each section has its own tab with more detailed information.
- **Right-hand pane**: Real-time graphical view of resource usage for each category.

## ✅ In Short

Resource Monitor is a **powerful diagnostic tool** that provides **real-time insights** into system performance, helping advanced users troubleshoot issues with processes, services, and resource conflicts.

### Command Prompt

- **Background**:
    - Early operating systems relied solely on the command line.
    - GUIs simplified interaction, but the command prompt remains a powerful tool for system tasks and troubleshooting.

## 📝 Basic Commands

- **`hostname`** → Displays the computer’s name.
- **`whoami`** → Shows the currently logged-in user.
- **`cls`** → Clears the command prompt screen.

## 🌐 Networking & Troubleshooting Commands

- **`ipconfig`** → Displays network address settings.
    - Use **`ipconfig /?`** to view syntax and parameters.
- **`netstat`** → Shows protocol statistics and current TCP/IP connections.
    - Supports parameters like `a`, `b`, `e` for different outputs.
- **`net`** → Manages network resources.
    - Requires **sub-commands** (e.g., `net user`, `net localgroup`, `net use`, `net share`, `net session`).
    - Help syntax: **`net help <sub-command>`** (not `/ ?`).

## 📖 Command Help

- Most commands support **`/?`** to display usage and options.
- Exception: **`net`** uses **`net help`** instead.

## ✅ In Short

The **Command Prompt** is a versatile tool for system information and troubleshooting.

- Start with simple commands (`hostname`, `whoami`).
- Use networking commands (`ipconfig`, `netstat`, `net`) for diagnostics.
- Always check built-in help (`/?` or `net help`) to learn syntax and parameters.

### Registry Editor

- **Definition**: A central hierarchical database that stores configuration information for:
    - Users
    - Applications
    - Hardware devices
- **Purpose**: Continuously referenced by Windows during operation to ensure proper system functionality.

## 📋 Information Stored in the Registry

- User profiles
- Installed applications and associated file types
- Folder and application icon settings
- Hardware details
- Active ports

## ⚠️ Important Note

- The registry is intended for **advanced users**.
- Incorrect edits can disrupt normal system operations.

## 🔧 Accessing the Registry

- One common method: **Registry Editor (regedit)**.
- Other methods exist, but all require caution.

## ✅ In Short

The **Windows Registry** is the backbone of Windows configuration, storing critical system, user, and application settings. It’s powerful but risky—changes should only be made by experienced users.

### Conclusion

- The tasks covered were examples of tools that can be launched from **MSConfig**.
- **Commands and shortcuts** were provided, so you don’t need to open MSConfig to access these utilities.
- Many of these tools can also be launched directly from the **Start Menu**.
- Some MSConfig-listed tools were:
    - Already covered in **Windows Fundamentals 1**, or
    - Left for you to **explore independently**.

✅ **In short**: MSConfig is one way to access system utilities, but most can also be run via shortcuts or the Start Menu, and not every tool was covered in this module.
