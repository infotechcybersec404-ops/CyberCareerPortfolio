# 🌐 DNS Overview

### What is DNS?
- Every device on the internet has a unique **IP address** (e.g., `104.26.10.229`) used for communication.  
- Remembering these numeric addresses is inconvenient for humans.  
- **DNS** acts like the Internet’s phonebook: it translates easy-to-remember **domain names** (e.g., `tryhackme.com`) into their corresponding IP addresses.  
- This allows us to access websites using names instead of long strings of numbers.  

✅ **In short**: DNS makes the internet user-friendly by mapping **human-readable names** to **machine-readable IP addresses**.  

---

## 🏛️ Domain Hierarchy

- **Root Domain**: The starting point of the hierarchy (represented as a dot `.`).  
- **Top-Level Domain (TLD)**:  
  - The **rightmost part** of a domain name (e.g., `.com` in `tryhackme.com`).  
  - **Types**:  
    - **gTLD (Generic TLD)** → originally indicated purpose (e.g., `.com` = commercial, `.org` = organization, `.edu` = education, `.gov` = government).  
    - **ccTLD (Country Code TLD)** → indicates geography (e.g., `.ca` = Canada, `.co.uk` = United Kingdom).  
  - Today, there are **2000+ TLDs**, including newer ones like `.online`, `.club`, `.website`, `.biz`.  

### 🏷️ Second-Level Domain (SLD)
- The part **directly to the left of the TLD**.  
- Example: In `tryhackme.com`, **`tryhackme`** is the SLD.  
- **Rules**:  
  - Up to **63 characters** (plus the TLD).  
  - Allowed: `a-z`, `0-9`, and hyphens.  
  - Restrictions: Cannot start/end with a hyphen, and no consecutive hyphens.  

### 🔑 Subdomain
- A **prefix** added to the SLD, separated by a dot.  
- Example: `admin.tryhackme.com` → **`admin`** is the subdomain.  
- **Rules**:  
  - Same restrictions as SLD (63 characters, only `a-z`, `0-9`, and hyphens).  
  - Multiple subdomains allowed (e.g., `jupiter.servers.tryhackme.com`).  
  - Entire domain length must be **≤ 253 characters**.  
  - No limit on the number of subdomains you can create.  

✅ **In short**:  
- **TLD** = rightmost part (`.com`, `.org`, `.ca`).  
- **SLD** = main domain name (`tryhackme`).  
- **Subdomain** = optional prefix (`admin.tryhackme.com`).  

---

## 📑 DNS Record Types

DNS isn’t just for websites—it supports multiple record types that serve different purposes:

### 🔹 A Record
- Maps a domain name to an **IPv4 address**.  
- Example: `104.26.10.229`.  

### 🔹 AAAA Record
- Maps a domain name to an **IPv6 address**.  
- Example: `2606:4700:20::681a:be5`.  

### 🔹 CNAME Record (Canonical Name)
- Points a domain or subdomain to **another domain name**.  
- Example: `store.tryhackme.com` → `shops.shopify.com`.  
- A second DNS lookup is then performed to resolve the final IP.  

### 🔹 MX Record (Mail Exchange)
- Directs email to the **mail servers** for a domain.  
- Includes a **priority flag** to determine which server to try first.  
- Example: `alt1.aspmx.l.google.com` for `tryhackme.com`.  

### 🔹 TXT Record
- Stores **text-based data**.  
- Common uses:  
  - Email authentication (e.g., SPF/DKIM records to prevent spoofing).  
  - Domain ownership verification for third-party services.  

✅ **In short**:  
- **A / AAAA** → Map domains to IPs (IPv4 / IPv6).  
- **CNAME** → Points one domain to another.  
- **MX** → Handles email routing with priorities.  
- **TXT** → Stores text data for security, verification, and policies.  

---

## 🔄 Making a DNS Request

1. **Local Cache Check**  
   - Computer checks its own DNS cache.  
   - If found → return result immediately.  

2. **Recursive DNS Server**  
   - Usually provided by ISP (or custom, e.g., Google DNS, Cloudflare).  
   - Checks its own cache.  
   - If found → return result to client.  
   - If not → continues the lookup process.  

3. **Root DNS Servers**  
   - Direct the query to the correct **Top-Level Domain (TLD) server** (.com, .org, etc.).  

4. **TLD Servers**  
   - Provide the location of the **Authoritative DNS Server** for the requested domain.  

5. **Authoritative DNS Server**  
   - Stores official DNS records (A, AAAA, MX, etc.).  
   - Sends the correct record back to the Recursive DNS Server.  

6. **Response & Caching**  
   - Recursive server caches the result (based on **TTL – Time To Live**).  
   - Response is sent back to the client.  
   - Future requests can be answered faster from cache.  

👉 **Key Idea:** DNS resolution is a step‑by‑step lookup process with caching at multiple levels (client, recursive server) to reduce repeated queries and speed up responses.  

---
