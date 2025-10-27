### Windows Updates

- **Purpose**:
    
    Provides security updates, feature enhancements, and patches for Windows OS and Microsoft products (e.g., Microsoft Defender).
    
- **Release Schedule**:
    - Regular updates: **2nd Tuesday of each month** → *Patch Tuesday*.
    - Urgent updates: Released immediately, not limited to Patch Tuesday.
- **Accessing Windows Update**:
    - **Settings app**.
    - Run dialog / CMD: `control /name Microsoft.WindowsUpdate`.
- **Virtual Machine Notes**:
    - Settings show as **“managed”** (common in enterprise, not home users).
    - No updates available since the VM lacks Internet access.
- **User Behavior & Microsoft’s Response**:
    - Historically, users delayed or skipped updates (often due to required reboots).
    - With **Windows 10**, updates can only be postponed, not ignored.
    - Eventually, updates install automatically, and the system reboots to ensure security.
- **Restart Management**:
    - Windows provides scheduling options when a restart is required after updates.
- **Further Resources**:
    - Microsoft Security Update Guide.
    - Windows Update FAQ.

### Windows Security

- **Definition**:
    
    Microsoft describes Windows Security as *“your home to manage the tools that protect your device and your data.”*
    
- **Access**:
    
    Available through the **Settings app**.
    
- **Main Protection Areas**:
    - **Virus & threat protection**
    - **Firewall & network protection**
    - **App & browser control**
    - **Device security**
- **Status Icons**:
    - 🟢 **Green** → Device is protected, no action needed.
    - 🟡 **Yellow** → Safety recommendation to review.
    - 🔴 **Red** → Warning, immediate attention required.
- **UI Differences**:
    - Windows Server 2019 looks different from Windows 10 Home/Pro editions.
    - Example images may vary depending on edition.
- **Next Focus**:
    
    The following section will cover **Virus & threat protection** in detail.
    

### Virus & threat protection

### 1. **Main Sections**

- **Current threats**
- **Virus & threat protection settings**

### 2. **Current Threats**

- **Scan options**
    - **Quick scan** → Common folders where threats are usually found.
    - **Full scan** → All files & running programs (can take 1+ hour).
    - **Custom scan** → User-selected files/locations.
- **Threat history**
    - **Last scan** → Automatic scans by Windows Defender.
    - **Quarantined threats** → Isolated, blocked, and later removed.
    - **Allowed threats** → User-approved threats (⚠️ risky, only if 100% sure).

### 3. **Virus & Threat Protection Settings**

- **Manage settings**
    - **Real-time protection** → Blocks malware from installing/running.
    - **Cloud-delivered protection** → Faster, cloud-based updates.
    - **Automatic sample submission** → Sends suspicious files to Microsoft.
    - **Controlled folder access** → Protects files/folders from unauthorized changes.
    - **Exclusions** → Skips scanning specified items (⚠️ risky).
    - **Notifications** → Alerts about device health & security.

### 4. **Updates & Ransomware Protection**

- **Check for updates** → Manually update Defender definitions.
- **Ransomware protection** → Requires *Controlled folder access* + *Real-time protection*.
    - Note: In the VM, real-time protection is disabled for performance, but on personal devices it should always be **enabled and up-to-date** (unless using a 3rd-party AV).

### 5. **Extra Tip**

- Right-click any file/folder → **“Scan with Microsoft Defender”** for on-demand scans.

### Firewall & network protection

### 1. **Definition**

- A firewall controls what traffic is **allowed or blocked** through device ports.
- Think of it as a **security guard** checking IDs at the door for incoming/outgoing traffic.

### 2. **Firewall Profiles**

- **Domain** → Used when the device can authenticate to a domain controller (enterprise networks).
- **Private** → User-assigned for trusted networks (e.g., home).
- **Public** → Default profile for untrusted networks (e.g., coffee shops, airports).

Each profile allows you to:

- Turn the firewall **on/off**.
- Block **all incoming connections**.

⚠️ Recommendation: Always keep Windows Defender Firewall **enabled** unless you are absolutely sure of what you’re doing.

### 3. **Managing Apps**

- You can **allow apps through the firewall** for specific profiles (Private/Public).
- Some apps provide extra details via the **Details** button.

### 4. **Advanced Settings**

- Advanced configuration is intended for **experienced users**.
- Best practices are documented by Microsoft.
- **Shortcut command**: `WF.msc` opens Windows Defender Firewall directly.

### App & browser control

- **Purpose**:
    
    Protects against phishing, malware websites/apps, and potentially malicious file downloads.
    
- **Features**:
    - **Check apps and files** → Screens unrecognized apps/files from the web.
    - **Exploit protection** → Built into Windows 10 and Windows Server 2019 to guard against attacks.
- **Best Practice**:
    
    ⚠️ Unless you are absolutely sure of what you’re doing, keep the **default settings enabled** for maximum protection.
    

### Device security

### 1. **Core Isolation**

- **Memory Integrity** → Prevents malicious code from being injected into high-security processes.
- ⚠️ Recommendation: Leave default settings enabled unless you are absolutely certain of what you’re doing.

### 2. **Security Processor (TPM)**

- **Trusted Platform Module (TPM)** → A hardware-based security chip.
- **Functions**:
    - Performs cryptographic operations.
    - Provides secure, tamper-resistant protection.
    - Ensures malicious software cannot interfere with its security functions.

This section highlights **low-level security features** (Memory Integrity + TPM) that most users won’t modify, but which are critical for protecting the system against advanced attacks.

### BitLocker

- **Definition**:
    
    A Windows feature that protects data against theft or exposure from **lost, stolen, or improperly decommissioned computers**.
    
- **Integration**:
    
    Works directly with the operating system for seamless data protection.
    
- **Best Protection**:
    - Achieved when used with a **Trusted Platform Module (TPM) v1.2 or later**.
    - **TPM** is a secure hardware chip that:
        - Performs cryptographic operations.
        - Ensures the system hasn’t been tampered with while offline.
        - Provides tamper-resistant, hardware-based security.
- **Availability**:
    
    Not included in the attached VM (but available on supported Windows editions/devices).
    

### Volume Shadow Copy Service

- **Definition**:
    
    Creates consistent **shadow copies** (snapshots/point-in-time copies) of data for backup purposes.
    
- **Storage Location**:
    
    Shadow copies are stored in the **System Volume Information** folder on each protected drive.
    
- **Functions (when System Protection is enabled)**:
    - Create a **restore point**
    - Perform a **system restore**
    - Configure restore settings
    - Delete restore points
- **Security Consideration**:
    - Malware often targets and deletes shadow copies to prevent recovery.
    - Protection against ransomware requires **offline or off-site backups** in addition to VSS.
- **Hands-On Practice**:
    
    Suggested exercise → *Day 23 of Advent of Cyber 2* for exploring VSS.
    

### Conclusion

- **Coverage**:
    
    Reviewed several **built-in Windows security tools** that help protect devices.
    
- **Learning Path**:
    - This content is designed for those who want to use Windows at a **more comfortable, practical level**.
    - To deepen knowledge, learners are encouraged to **continue exploring independently**.
- **Further Reading**:
    - Antimalware Scan Interface
    - Credential Guard
    - Windows Hello
    - *CSO Online*: Best new Windows 10 security features
- **Security Note**:
    - Attackers often exploit **built-in Windows tools/utilities** to avoid detection.
    - This technique is called **Living Off The Land (LOTL)**.
    - Additional resources are available to study this tactic.

This section essentially **concludes the module**, pointing learners toward **self-study and advanced topics** while reinforcing that Windows’ built-in tools are both powerful for defense and sometimes abused by attackers.
