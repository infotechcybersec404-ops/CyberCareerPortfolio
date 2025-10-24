### Introduction to Port Forwarding

- **Purpose**: Port forwarding allows applications and services (like web servers) inside a private network to be accessible from the Internet.  
- **Without it**: Services (e.g., a webserver at `192.168.1.10:80`) are only reachable by devices on the same local network (intranet).  
- **With it**: The router maps a public IP (e.g., `82.62.51.70`) and a specific port to the internal server, making it accessible to external networks.  
- **Key distinction**:  
  - **Port forwarding** → Opens a path to a service by directing traffic to the right internal device.  
  - **Firewall** → Decides whether that traffic is allowed through, even if the port is open.  
- **Configuration**: Always set up on the router.  

---

### Firewalls 101

- **Definition**: A firewall is a network security device (hardware or software) that controls what traffic is allowed to enter or leave a network. Think of it as **border security** for data.  
- **How it works**: Firewalls inspect packets and make decisions based on:  
  - **Source** → Where the traffic is coming from  
  - **Destination** → Where the traffic is going  
  - **Port** → Which service/port the traffic is targeting (e.g., port 80 for HTTP)  
  - **Protocol** → Whether it’s TCP, UDP, or another protocol  

---

### 🛡️ Types of Firewalls

| **Category** | **Description** | **Strengths** | **Weaknesses** |
| --- | --- | --- | --- |
| **Stateful** | Tracks the *entire connection* instead of just individual packets. Makes dynamic decisions based on connection behavior. | Smarter, context-aware, can block entire malicious hosts. | Resource-intensive, slower under heavy load. |
| **Stateless** | Uses fixed rules to evaluate *individual packets* without tracking connections. | Lightweight, fast, effective against large-scale attacks (e.g., DDoS). | Less intelligent, only as good as its rule set, can miss nuanced threats. |

---

✅ **Key takeaway**:  
- **Stateful firewalls** = smarter, but heavier.  
- **Stateless firewalls** = faster, but simpler.  
- Both are essential tools, chosen based on the network’s needs.  

---

### VPN Basics

#### 🔎 What is a VPN?

- A **VPN (Virtual Private Network)** creates a secure, encrypted “tunnel” over the Internet.  
- Devices inside this tunnel behave as if they are on the same private network, even if they’re geographically separated.  
- Example: Two offices (Network #1 and Network #2) can securely connect and form **Network #3** (the VPN), where only VPN‑connected devices can communicate.  

---

#### 🛡️ Benefits of a VPN

| **Benefit** | **Description** |
| --- | --- |
| **Connects remote networks** | Businesses with multiple offices can share resources (servers, infrastructure) securely. |
| **Privacy** | Encryption protects data from being intercepted (especially useful on public WiFi). |
| **Anonymity** | Hides traffic from ISPs and intermediaries. Journalists/activists use VPNs to bypass censorship. |
| **Security in labs (e.g., TryHackMe)** | VPN ensures vulnerable machines are only accessible through the VPN, not directly from the Internet. |

---

#### 🔐 VPN Technologies

| **Technology** | **Description** |
| --- | --- |
| **PPP (Point-to-Point Protocol)** | Provides authentication and encryption using keys/certificates. Non‑routable (can’t leave a network by itself). |
| **PPTP (Point-to-Point Tunneling Protocol)** | Uses PPP data and allows it to travel outside the network. Easy to set up, widely supported, but weak encryption. |
| **IPSec (Internet Protocol Security)** | Encrypts data at the IP layer. Strong encryption, widely supported, but more complex to configure. |

✅ **Key takeaway**:  
A VPN is like building a **secure, private highway** across the public Internet—connecting remote networks, protecting data, and enabling safe communication.  

---

### LAN Networking Devices

## 🛜 Router

- **Purpose**: Connects different networks and forwards data between them.  
- **Operation**: Works at **Layer 3 (Network Layer)** of the OSI model.  
- **Functions**:  
  - Uses routing protocols to determine the best path for data.  
  - Factors include shortest path, reliability, and medium speed (copper vs. fiber).  
  - Provides configuration options (e.g., port forwarding, firewall rules).  
- **Key Point**: Routers are **not the same as switches**—they focus on inter-network communication.  

---

## 🔌 Switch

- **Purpose**: Connects multiple devices within the same network (3–63 devices via Ethernet).  
- **Types**:  
  - **Layer 2 Switch**:  
    - Operates at the **Data Link Layer**.  
    - Forwards **frames** to devices using **MAC addresses**.  
    - Solely responsible for local device-to-device communication.  
  - **Layer 3 Switch**:  
    - Adds some router-like functions.  
    - Can forward frames **and** route packets using **IP addresses**.  
    - Supports **VLANs (Virtual LANs)** to segment networks for security and separation.  
    - Example: Sales and Accounting departments share Internet access but cannot directly communicate with each other.  

---

✅ **In short**:  
- **Routers** connect **different networks** and choose the best path for data.  
- **Switches** connect **devices within a network**; Layer 2 handles MAC-based forwarding, while Layer 3 can also perform routing and VLAN segmentation.  
