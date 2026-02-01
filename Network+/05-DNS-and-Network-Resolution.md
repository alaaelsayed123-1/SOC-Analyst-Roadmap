# DNS (Domain Name System) – Full Explanation with Examples & SOC Perspective

## What is DNS?
DNS (Domain Name System) is the service responsible for translating **human-readable domain names** (like `www.google.com`) into **IP addresses** (like `142.250.190.4`) that computers understand.  
Without DNS, users would need to remember IP addresses instead of names.

---

## DNS Client and DNS Server

### DNS Client
A DNS client is any device (PC, phone, server) that requests domain name resolution.
- Usually the operating system acts as the DNS client.
- It sends DNS queries automatically when a user accesses a website.

### DNS Server
A DNS server responds to DNS queries.  
Types of DNS servers include:
- Local DNS Server
- Recursive DNS Server
- Root DNS Server
- TLD DNS Server
- Authoritative DNS Server

---

## DNS Internet Process (High-Level Overview)
When a user types a website name in a browser:

1. The client checks **local cache**.
2. If not found, it sends a request to the **local DNS server**.
3. If still unknown, DNS resolution starts across the Internet.

This process is called **DNS Lookup** or **DNS Resolution**.

---

## DNS Hierarchy (Internet Structure)
DNS works in a hierarchical structure:

### Root Domain (.)
- The top of the DNS hierarchy
- Represented by a dot `.` (usually invisible)
- Knows where TLD servers are located

### Top-Level Domains (TLDs)
Examples:
- `.com`
- `.org`
- `.net`
- `.edu`
- `.gov`

Each TLD has its own DNS servers.

### Domain Name
Example:
- `google.com`

### Subdomain
Example:
- `www.google.com`
- `mail.google.com`

### Fully Qualified Domain Name (FQDN)
The full domain path:
 www.google.com.

 
---

## DNS Lookup Process (Step-by-Step – Deep)
### Scenario:
User types `www.example.com` in a browser.

**Step 1: Local Cache Check**
- Browser cache
- OS cache
- Hosts file  
If found → process stops.

**Step 2: Query Local DNS Server**
- Client sends a DNS query to its configured DNS server (ISP or company DNS).

**Step 3: Root DNS Server**
- If local DNS does not know, it asks a **Root DNS server**.
- Root replies: "I don’t know the IP, but I know where `.com` TLD servers are".

**Step 4: TLD DNS Server**
- Query sent to `.com` TLD server.
- TLD replies: "I know where the authoritative DNS server for `example.com` is".

**Step 5: Authoritative DNS Server**
- Holds the actual DNS records.
- Replies with the IP address.

**Step 6: Response to Client**
- IP is returned to the client.
- Cached for future use.
- Browser connects to the server using the IP.

---

## DNS Record Types

### A Record
Maps a domain name to an IPv4 address.  
**Example:**  
example.com → 93.184.216.34

Used for:
- Email validation
- Logging
- Security checks

---

## DNS in Virtual Lab (VMware Example)

### Lab Scenario:
- Client VM
- DNS Server VM

Steps:
1. Client sends DNS query.
2. DNS server receives it.
3. DNS server checks records.
4. DNS server responds with IP.
5. Client caches result.
6. Client connects to server.

This lab demonstrates:
- Real DNS traffic
- Query/Response mechanism
- Caching behavior

---

## DNS Security Risks (SOC Perspective)

### DNS Spoofing / Poisoning
- Attacker injects fake DNS responses.
- **Impact:** Redirects users to malicious sites.
- **Detection:** DNS logs mismatch, unexpected IP changes.

### DNS Tunneling
- Attackers hide data inside DNS queries.
- **Impact:** Data exfiltration, C&C communication.
- **Detection:** Long or random-looking domain names, high volume of requests.

---

## SOC Analyst View – Where to Monitor DNS
SOC Analysts monitor:
- DNS server logs
- Firewall DNS traffic
- IDS/IPS alerts
- SIEM correlations

Key questions:
- Is the domain trusted?
- Is the query pattern normal?
- Is the IP reputation clean?

---

## SOC Summary (TL;DR)
- DNS translates names to IPs.
- Uses a hierarchical structure.
- Multiple servers involved.
- Critical attack vector.
- Heavy monitoring required in SOC environments.

**Understanding DNS deeply helps SOC Analysts:**
- Detect redirections.
- Identify malware communication.
- Investigate suspicious network behavior.
