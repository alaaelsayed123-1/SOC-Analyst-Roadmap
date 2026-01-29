# Network ID and Subnet Mask – Understanding, Calculation, and Examples

## TL;DR – SOC Summary
- The **Network ID** identifies a specific network segment and is crucial for routing and monitoring traffic.  
- SOC Analysts use network IDs to determine which devices belong to which network and to detect unauthorized access.  
- Understanding subnet masks and logical AND operations helps analyze logs, firewalls, and routing tables.

---

## 1. What is a Subnet Mask?
**Definition:**  
- A subnet mask is a 32-bit number used to divide an IP address into **network** and **host** portions.  

**Purpose:**  
- Determines the range of IP addresses in a network.  
- Helps routers forward traffic to the correct network.  

**Example:**  
- IP: `192.168.10.25`  
- Subnet Mask: `255.255.255.0`  
- Network ID is calculated by ANDing the IP and subnet mask.

---

## 2. What is a Network ID?
**Definition:**  
- The **Network ID** identifies a unique network segment.  
- All devices in the same network share the same network ID.  
- **Host IDs** differentiate individual devices within that network.  

**Calculation:**  
- Perform a **bitwise AND** between the IP address and subnet mask.  

**Example:**
- IP: `192.168.10.25` → `11000000.10101000.00001010.00011001`  
- Subnet Mask: `255.255.255.0` → `11111111.11111111.11111111.00000000`  
- AND Operation → `11000000.10101000.00001010.00000000` → `192.168.10.0`  
- **Network ID:** `192.168.10.0`  
- **Host Range:** `192.168.10.1` – `192.168.10.254`  
- **Broadcast Address:** `192.168.10.255`  

---

## 3. Why Subnet Masks are Important
- Allow efficient IP address management.  
- Segment networks for performance and security.  
- Prevent unnecessary broadcast traffic across different networks.  

**SOC Note:** Monitoring network boundaries helps detect lateral movement or attacks across subnets.

---

## 4. Example – Two Networks Connected by a Router
**Scenario:**  
- Network A: `192.168.1.0/24`  
- Network B: `192.168.2.0/24`  
- Router connects both networks.  

**Steps:**  
1. PC1 in Network A: `192.168.1.10 /24`  
2. PC2 in Network B: `192.168.2.20 /24`  
3. Network ID Calculation:
   - PC1: `192.168.1.10 AND 255.255.255.0 = 192.168.1.0`  
   - PC2: `192.168.2.20 AND 255.255.255.0 = 192.168.2.0`  
4. Router routes packets between networks. Source IP remains the same, but MAC addresses update hop by hop.  

**Real-Life Example:**  
- Office building with multiple floors, each floor a separate subnet. Router handles traffic between floors.  

---

## 5. SOC Perspective
- SOC Analysts use subnet knowledge to:
  - Map network segments.  
  - Identify unusual traffic crossing subnet boundaries.  
  - Detect devices using incorrect IP addresses.  
- Logs often show the **Network ID**, making it easier to locate hosts in case of incidents.

---


