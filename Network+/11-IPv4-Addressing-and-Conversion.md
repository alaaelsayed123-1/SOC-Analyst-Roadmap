# IPv4 Addressing – Understanding, Conversion, and Examples

## TL;DR – SOC Summary
- IPv4 addressing identifies devices on a network and is essential for routing and monitoring traffic.  
- SOC Analysts use IP addresses to trace suspicious activity, identify sources of attacks, and understand network flows.  
- Understanding binary, decimal, and hexadecimal representations helps in analyzing logs, packet captures, and firewall rules.

---

## 1. What is an IPv4 Address?
**Definition:**  
- IPv4 (Internet Protocol version 4) is a 32-bit address used to identify hosts on a network.  
- Written in **dotted decimal notation**: four octets separated by periods (e.g., `192.168.1.10`).  

**Purpose:**  
- Identify the network portion and host portion of a device.  
- Facilitate routing across networks.

**Example in real life:**  
- Office PC: `192.168.1.25`  
- Web server in data center: `172.16.10.100`  

---

## 2. IPv4 Address Structure
IPv4 addresses consist of **4 octets** (8 bits each):  

| Octet | Range | Example |
|-------|-------|---------|
| 1     | 0–255 | 192     |
| 2     | 0–255 | 168     |
| 3     | 0–255 | 1       |
| 4     | 0–255 | 10      |

- **Network Portion:** Identifies the network.  
- **Host Portion:** Identifies the device on that network.  

**Subnet Mask:**  
- Determines which bits are network and which are host.  
- Example: `255.255.255.0` → first 3 octets are network, last is host.

---

## 3. Binary, Decimal, and Hexadecimal Representations

### 3.1 Decimal to Binary
- Each octet is converted into 8-bit binary.  
- Example: `192.168.1.10`  

| Decimal | Binary      |
|---------|------------|
| 192     | 11000000   |
| 168     | 10101000   |
| 1       | 00000001   |
| 10      | 00001010   |

**Explanation:** Computers use binary to route and process packets.

---

### 3.2 Binary to Decimal
- Convert each 8-bit binary octet back to decimal.  
- Example: `11000000.10101000.00000001.00001010` → `192.168.1.10`  

**How it works:**  
1. Multiply each binary bit by its power of 2.  
2. Sum the results for each octet.

---

### 3.3 Binary to Hexadecimal
- Convert 8-bit binary octets into 2-digit hexadecimal numbers.  
- Example: `192.168.1.10`  

| Decimal | Binary      | Hex  |
|---------|------------|------|
| 192     | 11000000   | C0   |
| 168     | 10101000   | A8   |
| 1       | 00000001   | 01   |
| 10      | 00001010   | 0A   |

- Complete address in hex: `C0.A8.01.0A`  

**Why useful:** Hexadecimal is shorter and easier to read in networking tools and packet analysis.

---

## 4. Practical Examples

1. **Host Communication on Same Network**
   - PC1: `192.168.1.10` /24  
   - PC2: `192.168.1.20` /24  
   - Both convert to binary for packet delivery; MAC addresses are used at the data link layer.

2. **Host Communication Across Networks**
   - PC1: `192.168.1.10` /24  
   - Web Server: `172.16.10.100` /16  
   - Router uses network portions to forward packets; source IP remains the same while MAC addresses update hop-to-hop.

---

## 5. SOC Perspective
- SOC analysts **trace attacks** using source and destination IPs in logs.  
- Conversion knowledge helps analyze network captures (`Wireshark`) and firewall logs.  
- Understanding network vs host portions is critical for **subnet monitoring** and detecting unauthorized access.

---


