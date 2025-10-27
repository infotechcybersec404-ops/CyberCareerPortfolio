# Introduction to Defensive Security

## 🛡️ Defensive Security (Blue Teaming) Overview

- **Focus:** Protecting networks and organizations from cyber threats  
- **Role:** Defensive teams monitor, detect, and respond to attacks  
- **Importance:** Failures in defensive security can lead to massive data breaches, financial losses, and regulatory fines  

---

## ⚠️ Real-World Breach Examples

| Organization                        | Year | Incident                                                                 | Impact                                | Penalty                  |
|-------------------------------------|------|--------------------------------------------------------------------------|---------------------------------------|--------------------------|
| **British Airways**                 | 2018 | Leak of personal + payment details of 400k+ customers                     | Severe data exposure                   | £20M fine                |
| **Marriott International**          | 2020 | Leak of 334M customer records (passport, payment, names) due to outdated systems | Global impact                          | $52M lawsuit settlement  |
| **Advanced Computer Software Group**| 2022 | Leak of 79,904 medical records + phone numbers                            | Sensitive health data exposed          | £3.07M fine              |
| **23andMe**                         | 2023 | Leak of 7M+ users’ names, addresses, health + DNA data                    | Highly sensitive personal data         | £2.31M fine              |
| **SK Telecom**                      | 2024 | Poorly configured servers leaked data of ~27M users                       | Large-scale exposure                   | $97M fine                |

---

## ✍️ Key Takeaways

- Defensive security is **critical** to prevent costly breaches  
- Weak policies, outdated systems, and poor configurations are common causes of incidents  
- Consequences include:  
  - **Loss of trust**  
  - **Exposure of sensitive data**  
  - **Multi-million fines/lawsuits**  

---

## 🛡️ Responsibilities of Defensive Security

### Key Areas

- **Monitoring & Detecting**  
  - Continuous observation of network/system activity  
  - Example: spotting logins from unusual locations  

- **Incident Response**  
  - Team acts when suspicious activity is confirmed  
  - Steps: contain → remove threat → restore operations  

- **Threat Intelligence**  
  - Collect attacker info (methods, targets, trends)  
  - Example: knowing attackers target a specific software  

- **Vulnerability Management**  
  - Identify and fix flaws to reduce attack risk  
  - Done manually or with automated tools  

- **Investigation & Analysis**  
  - Differentiate normal vs. suspicious activity  
  - Dig deep into events like solving a puzzle for insights  

---

### 👥 Defensive Security Team Roles

- **SOC Analyst**  
  - Monitors network/system events  
  - First line of defense  

- **Incident Responder**  
  - Investigates/responds to active incidents  
  - Stops attackers in real time and shares lessons learned  

- **Security Engineer**  
  - Builds/maintains tools and systems for monitoring and investigation  

- **Digital Forensics Specialist**  
  - Collects, preserves, and analyzes evidence  
  - Reconstructs attacker methods and incident details  

---

✅ **Summary in one line:**  
Defensive security combines monitoring, response, intelligence, vulnerability management, and analysis—carried out by specialized roles like SOC analysts, responders, engineers, and forensic experts—to protect organizations from threats.  

---

## 🛡️ Defensive Security in Practice

### Defence in Depth

- Organisations use **multiple layers of defence** (like an onion or castle walls)  
- If one measure fails, others provide backup protection  

### 🔑 Key Defensive Measures

- **Employee Training**  
  - Humans are often the target of attacks (e.g., phishing)  
  - Training builds awareness and proactive response  

- **Intrusion Detection Systems (IDS)**  
  - Act like surveillance cameras for IT systems  
  - Monitor and alert on suspicious behaviour  

- **Firewalls**  
  - Act like security guards at the network perimeter  
  - Control which traffic is allowed or blocked  

- **Security Policies**  
  - Define correct system use  
  - Examples: block risky sites, enforce strong passwords  
  - Provide backup protection if an employee makes a mistake (e.g., opening a malicious attachment)  

---

### 🏢 Security Operations Centre (SOC)

- The **frontline hub** for defensive security  
- Operates 24/7/365 with dedicated professionals  
- Typical tasks:  
  - Reviewing alerts  
  - Investigating anomalies  
  - Responding to incidents  

---

### 📡 SIEM (Security Information and Event Management)

- Acts like a **radar/control centre** for security data  
- Collects and centralises logs from devices, servers, and workstations  
- Provides visibility and insight into what’s happening across IT  
- Enables multiple analysts to review and respond quickly  

---

👉 **This summary captures the layered approach, core tools, and the role of SOCs and SIEMs in defensive security.**

---

## 🛡️ Practical: Defend FakeBank

### FakeBank Defensive Security Scenario – Summary

- **Role:** Join FakeBank’s defensive security team  
- **Focus:** Investigate and resolve suspicious events flagged by the **SIEM** system  
- **Objective:** Protect FakeBank and its customers from threats  
- **Approach:** Be proactive, inquisitive, and thorough in analysis  
