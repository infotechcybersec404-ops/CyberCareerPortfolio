### What is Offensive Security?

- **Core Principle**: *“To outsmart a hacker, you need to think like one.”*

- **Definition**:  
  Offensive Security is the practice of simulating hacker behavior to test and strengthen systems.

- **Methods Used**:  
  - Breaking into computer systems (ethical hacking / penetration testing)  
  - Exploiting software bugs  
  - Finding loopholes in applications  

- **Purpose**:  
  - Gain unauthorized access in a controlled, ethical way  
  - Understand hacker tactics and strategies  
  - Use that knowledge to **improve system defenses**

👉 **In short:** Offensive Security = *ethical hacking mindset + proactive defense building*


---

### Hacking Your First Machine

## Overview

- **Tool used:** Gobuster (command-line application)  
- **Purpose:** Brute-force a website to discover hidden directories/pages  
- **Scenario:** FakeBank website with potentially exposed admin/transfer pages  
- **Ethical hacking context:** With permission, identify vulnerabilities and report them  

### Step 1: Open a Terminal

- **Terminal = command line interface (CLI).**  
- Allows interaction with the system without a GUI.  
- Open by clicking the **Terminal icon** on the machine.  

### Step 2: Use Gobuster to Find Hidden Pages

- **Why?**  
  - Companies often have hidden admin portals.  
  - If not secured, attackers can discover them and gain access.  

- **Command syntax:**

    ```bash
    gobuster -u http://fakebank.thm -w wordlist.txt dir
    ```

    - `u` → target URL  
    - `w` → wordlist file (list of possible directory/page names)  
    - `dir` → mode (directory brute-forcing)  

### Step 3: Access the Hidden Page

- **Discovered page:** `/bank-transfer`  
- Enter it in the browser:

    ```
    http://fakebank.thm/bank-transfer
    ```

- **Scenario outcome:**  
  - Page allows money transfers between accounts.  
  - Demonstrates how attackers could exploit exposed functionality.  

---

## Ethical Hacking Reminder

- **Real-world role:**  
  - Ethical hackers **do not exploit** vulnerabilities for personal gain.  
  - Instead, they **report findings** to the organization.  

- **This exercise:**  
  - Teaches how hidden pages can be discovered.  
  - Reinforces importance of securing sensitive endpoints.  

---

## Key Concepts to Remember

- **Gobuster basics:**  
  - Directory brute-forcing tool.  
  - Requires a target URL + wordlist.  

- **Status codes:**  
  - `200` → OK (page exists)  
  - `301/302` → Redirect  
  - `403` → Forbidden (exists but restricted)  

- **Security lesson:**  
  - Hidden ≠ secure  
  - Sensitive pages must be properly authenticated and protected  
