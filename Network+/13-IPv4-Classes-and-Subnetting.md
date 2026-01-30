# IPv4 32-bit Addressing and Classes

## TL;DR – SOC Summary
- Understanding IPv4 32-bit structure, subnetting, and IP classes is essential for routing, traffic analysis, and incident investigation.  
- SOC Analysts use network IDs, host IDs, and class knowledge to detect misconfigured devices, unauthorized access, and network anomalies.

---

## 1. IPv4 32-bit Address Distribution
- IPv4 addresses are **32 bits**, divided into **4 octets** (8 bits each).  
- Each octet can be represented in **binary, decimal, or hexadecimal**.  

**Example:**
- IP Address: `192.168.10.25`  

| Octet | Binary       | Decimal | Hex  |
|-------|-------------|---------|------|
| 1     | 11000000    | 192     | C0   |
| 2     | 10101000    | 168     | A8   |
| 3     | 00001010    | 10      | 0A   |
| 4     | 00011001    | 25      | 19   |

---

## 2. IP Address Components
- **Network ID:** Identifies the network segment (calculated with subnet mask).  
- **Subnet ID:** Optional segment within a network for hierarchical addressing.  
- **Host ID:** Identifies a specific device in the network/subnet.  

**Example Calculation:**  
- IP: `192.168.10.25 /24`  
- Subnet Mask: `255.255.255.0`  
- Network ID: `192.168.10.0`  
- Host Range: `192.168.10.1 – 192.168.10.254`  
- Broadcast: `192.168.10.255`

---

## 3. IPv4 Address Classes
IPv4 addresses are categorized into classes A, B, C, D, and E.  

### 3.1 Class A
- **Range:** 0.0.0.0 – 127.255.255.255  
- **Subnet Mask:** /8 (255.0.0.0)  
- **Network Bits:** 8  
- **Host Bits:** 24  
- **First bit:** 0  
- **Special Addresses:**  
  - `127.x.x.x` → Loopback  
  - `0.0.0.0` → Default route  
- **Example:**  
  - Network ID: `10.0.0.0`  
  - Host ID range: `10.0.0.1 – 10.255.255.254`  
  - Broadcast: `10.255.255.255`

### 3.2 Class B
- **Range:** 128.0.0.0 – 191.255.255.255  
- **Subnet Mask:** /16 (255.255.0.0)  
- **Network Bits:** 16  
- **Host Bits:** 16  
- **Example:**  
  - Network ID: `172.16.0.0`  
  - Host ID range: `172.16.0.1 – 172.16.255.254`  
  - Broadcast: `172.16.255.255`

### 3.3 Class C
- **Range:** 192.0.0.0 – 223.255.255.255  
- **Subnet Mask:** /24 (255.255.255.0)  
- **Network Bits:** 24  
- **Host Bits:** 8  
- **Example:**  
  - Network ID: `192.168.1.0`  
  - Host ID range: `192.168.1.1 – 192.168.1.254`  
  - Broadcast: `192.168.1.255`

### 3.4 Class D
- **Range:** 224.0.0.0 – 239.255.255.255  
- **Usage:** Multicast

### 3.5 Class E
- **Range:** 240.0.0.0 – 255.255.255.255  
- **Usage:** Experimental / Future use

---

## 4. Summary Table of IPv4 Classes

| Class | Range                  | Default Subnet Mask | Network Bits | Host Bits | Example Network | Broadcast Address       |
|-------|-----------------------|------------------|-------------|----------|----------------|-----------------------|
| A     | 0.0.0.0 – 127.255.255.255 | 255.0.0.0       | 8           | 24       | 10.0.0.0       | 10.255.255.255        |
| B     | 128.0.0.0 – 191.255.255.255 | 255.255.0.0     | 16          | 16       | 172.16.0.0     | 172.16.255.255        |
| C     | 192.0.0.0 – 223.255.255.255 | 255.255.255.0   | 24          | 8        | 192.168.1.0    | 192.168.1.255         |
| D     | 224.0.0.0 – 239.255.255.255 | N/A              | N/A         | N/A      | N/A            | N/A                   |
| E     | 240.0.0.0 – 255.255.255.255 | N/A              | N/A         | N/A      | N/A            | N/A                   |

---

## 5. SOC Perspective
- **Class awareness** helps SOC Analysts:  
  - Determine internal vs external traffic.  
  - Detect misconfigured hosts using wrong IP classes.  
  - Map subnets and network segments efficiently for monitoring.  
- Tools like Wireshark, firewall logs, and SIEM can show Network IDs and host ranges.

---

**File Name Suggestion:**  

