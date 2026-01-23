
# OSI Model and ARP Practical Lab

## Lab Objective
To observe how data flows through the OSI model layers, how encapsulation/decapsulation occurs, and how ARP resolves IP addresses to MAC addresses within a LAN.

---

## Lab Environment
- Two PCs in the same LAN
- Network interface with IP and MAC addresses
- Firewall enabled/disabled
- Ping, arp commands, and network inspection tools

---

## Part 1: OSI Communication Flow

### Step 1: Initiating Communication
- Sent a ping request from PC A to PC B.
- **Observation:** The request passes through all OSI layers:
  - Application Layer creates request
  - Transport Layer segments data
  - Network Layer adds IP addresses
  - Data Link Layer adds MAC addresses
  - Physical Layer transmits bits

### Step 2: Encapsulation
- Each layer adds its header, forming a frame.
- **SOC Note:** Encapsulation allows layers to operate independently while maintaining communication integrity.

### Step 3: Decapsulation
- Destination PC removes headers layer by layer, ultimately delivering the payload to the application.
- **SOC Note:** Monitoring encapsulation/decapsulation helps SOC analysts troubleshoot network issues.

---

## Part 2: ARP Process

### Step 1: Checking ARP Cache
- Used `arp -a` to inspect stored IP-to-MAC mappings.

### Step 2: ARP Broadcast Request
- Sent an ARP request for a new IP.
- Broadcast MAC: FF-FF-FF-FF-FF-FF
- Switch forwards request to all ports.

### Step 3: ARP Reply
- Target device responds with its MAC address.
- ARP table updates.

### Step 4: ARP Cache Clearing
- Cleared ARP cache using `arp -d *`.
- Triggered new broadcast to learn updated MAC addresses.
- **SOC Note:** Clearing ARP cache is necessary if network interfaces change.

---

## Observations
- ARP operates at Layer 2, supporting Layer 3 communication.
- Switch forwards broadcasts; only the correct IP responds.
- Incorrect ARP entries prevent communication until cache is refreshed.

---

## Security Relevance (SOC Perspective)
- Abnormal ARP traffic may indicate ARP spoofing attacks.
- Broadcast storms can signal misconfigurations or malicious activity.
- OSI understanding helps identify the affected layer during incidents.

---

## Key Takeaways
- OSI encapsulation and decapsulation are observable in real networks.
- ARP is critical for local network IP-to-MAC resolution.
- Understanding OSI & ARP strengthens SOC analyst troubleshooting skills.
