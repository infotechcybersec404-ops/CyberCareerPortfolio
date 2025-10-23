# Introducing LAN Topologies

## 🔹 Topology = Network Design
Refers to the physical or logical layout of how devices are connected.

---

## ⭐ Star Topology
- **Design**: All devices connect to a central hub/switch.  
- **Advantages**:  
  - Reliable and scalable (easy to add devices).  
  - Centralized management of traffic.  
- **Disadvantages**:  
  - Higher cost (extra cabling + networking hardware).  
  - Central device failure = entire network down.  
  - More devices = more maintenance and troubleshooting complexity.  

---

## 🚌 Bus Topology
- **Design**: All devices share a single backbone cable.  
- **Advantages**:  
  - Low cost (minimal cabling, no expensive hardware).  
  - Simple to set up.  
- **Disadvantages**:  
  - Prone to bottlenecks (all traffic on one cable).  
  - Troubleshooting is difficult.  
  - Single point of failure (if backbone breaks, network fails).  

---

## 🔄 Ring Topology
- **Design**: Devices connected in a loop; data travels in one direction.  
- **Advantages**:  
  - Less cabling than star.  
  - Easier to troubleshoot (faults are easier to trace).  
  - Less prone to bottlenecks than bus.  
- **Disadvantages**:  
  - Inefficient (data may pass through many devices).  
  - One device/cable failure = entire network breaks.  

---

## 🔌 Switch
- **Purpose**: Connects multiple devices (computers, printers, etc.) via Ethernet.  
- **Features**:  
  - Ports: 4, 8, 16, 24, 32, 64.  
  - Smarter than hubs: sends packets only to intended device (reduces traffic).  
  - Common in businesses, schools, large networks.  

---

## 🌐 Router
- **Purpose**: Connects different networks and directs data between them.  
- **Function**: Uses *routing* to determine best path for data delivery.  
- **Benefit**: Enables communication across multiple networks.  

---

## 🔗 Switches + Routers Together
- Can be interconnected for redundancy.  
- Multiple paths = higher reliability (no downtime if one path fails).  
- Trade-off: may reduce performance slightly due to longer routes.  

---

# A Primer on Subnetting

## 🔹 What is Subnetting?
- **Definition**: Splitting a larger network into smaller, manageable subnetworks.  
- **Analogy**: Like slicing a cake—each slice (subnet) is reserved for a group.  
- **Purpose**: Organizes and controls traffic between different groups (e.g., Accounting, Finance, HR).  

---

## 🔹 IP Address & Subnet Mask
- **IP Address**: 4 octets (32 bits).  
- **Subnet Mask**: Also 4 octets; defines how many hosts fit in a subnet.  
- **Subnetting** = dividing available host addresses into smaller ranges.  

---

## 🔹 Subnet Addressing Roles

| **Type**           | **Purpose**                     | **Explanation**                  | **Example**       |
|---------------------|---------------------------------|----------------------------------|-------------------|
| **Network Address** | Identifies the network itself   | Defines the start of the subnet  | `192.168.1.0`     |
| **Host Address**    | Identifies a device on subnet   | Assigned to each device          | `192.168.1.100`   |
| **Default Gateway** | Connects subnet to other nets   | Usually first/last host address  | `192.168.1.254`   |

---

## 🔹 Where Subnetting is Used
- **Small networks (home)**: Usually one subnet (≤254 devices).  
- **Large networks (businesses, offices)**: Multiple subnets for PCs, printers, cameras, sensors, etc.  

---

## 🔹 Benefits of Subnetting
- **Efficiency**: Better use of IP addresses.  
- **Security**: Isolates groups (e.g., employees vs. public Wi‑Fi in a café).  
- **Control**: Easier management of traffic and resources.  

---

# ARP (Address Resolution Protocol)

## 🔹 Purpose
- Maps **IP addresses** (logical identifiers) to **MAC addresses** (physical identifiers).  
- Ensures devices can locate each other on a local network.  
- Each device maintains an **ARP cache** (a table of IP ↔ MAC mappings).  

---

## 🔹 How ARP Works
1. **ARP Request**  
   - Broadcast message: *“Who has this IP address?”*  
   - Sent to all devices on the local network.  
2. **ARP Reply**  
   - The device with that IP responds with its **MAC address**.  
   - The requesting device stores this mapping in its ARP cache for future use.  

---

## 🔹 Key Points
- **Broadcast-based**: Requests go to all devices, but only the owner replies.  
- **Cache efficiency**: Prevents repeated broadcasts by storing known mappings.  
- **Essential for communication**: Without ARP, IP packets couldn’t be delivered to the correct physical device.  

👉 Think of ARP as the **“phonebook” of the local network**.  

---

# DHCP (Dynamic Host Configuration Protocol)

## 🔹 Purpose
- Automates the assignment of **IP addresses** to devices on a network.  
- Saves administrators from manually configuring each device.  

---

## 🔹 Manual vs Automatic Assignment
- **Manual**: IP entered directly into device settings.  
- **Automatic (DHCP)**: Device requests an IP from a DHCP server.  

---

## 🔹 DHCP Process (DORA)
The process follows **four key steps**, often remembered as **DORA**:

1. **Discover**  
   - Device broadcasts: *“Is there a DHCP server?”*  
2. **Offer**  
   - DHCP server replies with an available IP address.  
3. **Request**  
   - Device responds: *“I’d like to use that IP.”*  
4. **Acknowledge (ACK)**  
   - Server confirms assignment. Device can now use the IP.  

---

## 🔹 Key Points
- Ensures **unique IPs** on the network.  
- Reduces **configuration errors**.  
- Common in **home, office, and enterprise networks**.  

👉 Think of DHCP as a **“rental service” for IP addresses**:  
- Device asks for a lease → server offers one → device accepts → server confirms.  
