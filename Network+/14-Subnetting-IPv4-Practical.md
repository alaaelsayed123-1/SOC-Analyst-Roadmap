# IPv4 Subnetting – Why, How, and Practical Examples

## TL;DR – SOC Summary
- Subnetting allows dividing a large network into smaller, manageable networks.  
- SOC Analysts use subnet knowledge to map network segments, detect anomalies, and investigate incidents.  
- Understanding network ID, broadcast address, and host range helps correlate logs and firewall events.

---

## 1. Why Subnetting?
- **Efficiency:** Divide large networks into smaller subnets to improve management and reduce broadcast traffic.  
- **Security:** Segments sensitive departments separately (e.g., finance, HR, IT).  
- **ISP Requirement:** ISPs often provide a block of IPs; subnetting ensures optimal usage.  

**Example:**  
- A company has `192.168.0.0/24` but wants separate networks for HR, IT, and Finance.  
- Subnetting allows creating three smaller networks:  
  - HR: `192.168.0.0/26` (64 IPs)  
  - IT: `192.168.0.64/26`  
  - Finance: `192.168.0.128/26`  

---

## 2. Key Concepts

### 2.1 Subnet Mask (SM)
- Determines which bits belong to the **network** and which to **hosts**.  
- **Class C example:** `/24` → 255.255.255.0 → first 24 bits network, last 8 bits host.  

### 2.2 Network ID
- Identifies the subnet.  
- **Example:** `192.168.1.0/26` → Network ID: `192.168.1.0`  

### 2.3 Broadcast Address
- Address used to send messages to all hosts in the subnet.  
- **Example:** `192.168.1.0/26` → Broadcast: `192.168.1.63`  

### 2.4 Host Range
- Valid addresses for devices.  
- **Example:** `192.168.1.0/26` → Hosts: `192.168.1.1 – 192.168.1.62`  

---

## 3. Subnetting by IP Class

### Class A
- Network ID: 8 bits  
- Host bits: 24  
- **Example:**  
  - Original network: `10.0.0.0/8`  
  - Need 32 subnets → Borrow 5 bits → New subnet mask `/13`  
  - Hosts per subnet: `2^19 – 2 = 524,286`  
  - Broadcast calculated per subnet  

### Class B
- Network ID: 16 bits  
- Host bits: 16  
- **Example:**  
  - Original network: `172.16.0.0/16`  
  - Divide for 32 subnets → Borrow 5 bits → `/21`  
  - Hosts per subnet: `2^11 – 2 = 2,046`  

### Class C
- Network ID: 24 bits  
- Host bits: 8  
- **Example:**  
  - Original network: `192.168.1.0/24`  
  - Divide for 32 subnets → Borrow 5 bits → `/29`  
  - Hosts per subnet: `2^3 – 2 = 6`  

---

## 4. Real Lab Exercises (VMware)

### Exercise 1 – 32 Subnets
- **Network:** `192.168.0.0/24`  
- **Objective:** Divide into 32 subnets  
- **Steps:**  
  1. Calculate required bits: `2^n = 32 → n = 5`  
  2. New subnet mask: `/29` → 255.255.255.248  
  3. Calculate subnet IDs, first host, last host, and broadcast addresses for all 32 subnets  
  4. Assign hosts in VMware VM to respective subnets  
- **SOC Note:** Analysts can use this mapping to track traffic per subnet and detect anomalies.

### Exercise 2 – Hosts Requirement
- **Network:** `172.16.0.0/16`  
- **Objective:** Create subnets supporting at least 500 hosts each  
- **Steps:**  
  1. Determine number of host bits: `2^h – 2 ≥ 500 → h = 9`  
  2. New subnet mask: `/23` → 255.255.254.0  
  3. Calculate network ID, host range, broadcast for each subnet  
- **SOC Note:** Understanding host ranges helps detect IP conflicts or rogue devices.

---

## 5. Practical Example in a Company
- **Scenario:** Finance, HR, and IT departments  
  - Finance: `/26` → 64 IPs  
  - HR: `/26` → 64 IPs  
  - IT: `/26` → 64 IPs  
- **Lab Setup:** Assign VMs in VMware to each subnet to simulate department isolation.  
- **SOC Perspective:**  
  - Monitor departmental traffic  
  - Detect cross-subnet attacks  
  - Track firewall and ACL enforcement per subnet

---

## 6. SOC Takeaways
- Subnetting knowledge allows SOC Analysts to:  
  - Map networks for monitoring and incident response  
  - Detect misconfigured IPs or unauthorized access  
  - Analyze traffic by subnet for lateral movement detection  
  - Validate firewall and ACL rules per subnet  

---


