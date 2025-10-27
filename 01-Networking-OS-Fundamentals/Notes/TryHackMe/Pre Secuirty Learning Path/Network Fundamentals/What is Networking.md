# 🧠 Networking Fundamentals

---

## 🔌 What is Networking?

- **Definition**: A network is simply a set of things connected.
- **Everyday Examples**:
  - Friendship circles
  - Public transportation systems
  - Power grids
  - Postal systems
  - Neighborhood interactions
- **In Computing**:
  - The same principle applies, but with devices instead of people or infrastructure.
  - Networks can range from **2 devices to billions**, including laptops, phones, cameras, traffic lights, and even farming equipment.
  - Devices communicate by following specific rules (**protocols**).
- **Importance**:
  - Networks are deeply embedded in daily life—power delivery, weather data collection, traffic control, and more.
  - Because of this, **understanding networking is essential in cybersecurity**.
- **Key Point**: Networks come in many forms and scales, and this variety will be explored further in the module.

---

## 🌐 What is the Internet?

- **Network basics**: A network = devices connected together.
- **The Internet**:
  - A massive global network made up of many smaller networks.
- **History**:
  - **1960s**: ARPANET (funded by U.S. Defense Department) → first working network.
  - **1989**: Tim Berners-Lee created the **World Wide Web (WWW)** → transformed the Internet into a platform for storing and sharing information.
- **Types of networks**:
  - **Private network** → small, local, internal connections.
  - **Public network** → connects private networks together; this is the Internet.
- **Key Point**: Devices on a network use **labels (identifiers)** to communicate.

---

## 🔑 Identifying Devices on a Network

### 🧭 Device Identification

- **Why it matters**: Devices must be identifiable to communicate properly, just like people need names or fingerprints.
- **Two identifiers (human analogy)**:
  - **IP Address** → like a name (can change).
  - **MAC Address** → like fingerprints/serial number (unique, factory‑set).

---

### 🌍 IP Addresses

- **Definition**: Numerical label (4 octets in IPv4) that identifies a device on a network.
- **Key traits**:
  - Can change between devices.
  - Must be unique within the same network.
  - Governed by **protocols** (shared communication rules).
- **Types**:
  - **Private IP** → identifies a device within a local/private network.
  - **Public IP** → identifies a device on the Internet (assigned by ISP).
  - Multiple devices on the same private network can share one public IP when accessing the Internet.
- **IPv4 vs IPv6**:
  - **IPv4**: 32‑bit, ~4.29 billion addresses → shortage due to billions of devices.
  - **IPv6**: 128‑bit, ~340 trillion+ addresses → solves shortage, more efficient.

---

### 🖥️ MAC Addresses

- **Definition**: Unique 12‑character hexadecimal address assigned to a device’s network interface card (NIC).
- **Format**: `a4:c3:f0:85:ac:2d`
  - First 6 chars → manufacturer.
  - Last 6 chars → unique device ID.
- **Key points**:
  - Permanent (but can be **spoofed**).
  - Spoofing = pretending to be another device by copying its MAC.
  - Can bypass weak security setups (e.g., firewalls trusting specific MACs).
- **Real‑world use**:
  - Public Wi‑Fi (cafes, hotels) often use MAC filtering for access control or tiered services.
  - Example: Paid vs free Wi‑Fi access based on MAC.

---

✅ **Takeaway**:

- Devices need **two identifiers**:
  - **IP Address** (changeable, logical, location‑based).
  - **MAC Address** (unique, hardware‑based).
- Together, they ensure devices can be recognized, communicate, and be managed securely on networks.

---

## 📡 Ping (ICMP)

- **Purpose**: Tests connectivity and performance between devices.
- **How it works**:
  - Uses **ICMP (Internet Control Message Protocol)**.
  - Sends an **echo request** → target replies with an **echo reply**.
  - Measures **round‑trip time (latency)** of packets.
- **Usage**:
  - Works on both **private networks** (e.g., home devices) and the **Internet** (e.g., websites).
  - Built into most OSs (Linux, Windows, etc.).
- **Syntax**:

  ```bash
  ping <IP address or website URL>
  ```
  👉 **Key takeaway**: Ping is a quick, universal way to check if a device is reachable and how fast it responds.
