# Ethernet – Definition, Architecture, and Standards

## TL;DR – SOC Summary
- Ethernet is the most widely used LAN technology.  
- Understanding Ethernet architecture, topologies, and media is essential for SOC Analysts to monitor traffic, detect anomalies, and troubleshoot connectivity issues.  
- Key focus: **media types, access methods, frame structure, and limitations**.

---

## 1. What is Ethernet?
**Definition:**  
- Ethernet is a network technology used for local area networks (LANs) to transmit data between devices.  
- Provides standardized **rules for communication, data formatting, and media access**.  

**Purpose:**  
- Connect multiple devices within a network to share resources efficiently.  
- Support different data rates and media types.  

**Example in real life:**  
- Connecting PCs, servers, and printers in an office LAN.  
- Home routers and switches use Ethernet ports to connect devices.

---

## 2. Ethernet Architecture
Ethernet architecture consists of:  

1. **Network Topologies**  
   - **Bus Topology:** Single backbone; all devices tap into the bus. Rare today.  
   - **Star Topology:** Devices connect to a central switch or hub. Most common in modern LANs.  
   - **Ring / Hybrid:** Used in specialized setups.  

   **Physical vs Logical Topology:**  
   - Physical: Actual cable layout.  
   - Logical: How data flows across the network.  

2. **Network Media**  
   - **Twisted Pair Cables:** UTP, STP; easy to install, cost-effective, limited distance.  
   - **Fiber Optic Cables:** High-speed, long-distance, immune to EMI/RFI.  

3. **Media Access Methods**  
   - **CSMA/CD (Carrier Sense Multiple Access with Collision Detection):**  
     - Devices check if the medium is free before transmitting.  
     - If collision occurs, devices stop, wait, and retry after random time.  
   - Ensures orderly communication on shared media.  

4. **Frame Length**  
   - Ethernet frames have **minimum 64 bytes and maximum 1518 bytes**.  
   - Includes headers, payload, and CRC for error detection.

---

## 3. Ethernet Standards
Ethernet standards define **speed, transmission media, distance, and maximum hosts**:  

| Standard         | Speed       | Media                   | Max Distance | Max Hosts (approx.) |
|-----------------|------------|------------------------|-------------|------------------|
| 10BASE-T        | 10 Mbps    | Twisted Pair           | 100 m       | 1024             |
| 100BASE-TX      | 100 Mbps   | Twisted Pair           | 100 m       | 1024             |
| 1000BASE-T      | 1 Gbps     | Twisted Pair           | 100 m       | 1024             |
| 10GBASE-T       | 10 Gbps    | Twisted Pair           | 100 m       | 1024             |
| 1000BASE-SX     | 1 Gbps     | Multi-mode Fiber       | 550 m       | 1024             |
| 1000BASE-LX     | 1 Gbps     | Single-mode Fiber      | 5 km        | 1024             |
| 10GBASE-SR      | 10 Gbps    | Multi-mode Fiber       | 300 m       | 1024             |
| 10GBASE-LR      | 10 Gbps    | Single-mode Fiber      | 10 km       | 1024             |

---

## 4. Twisted Pair Cabling
**4 Bases for Twisted Pair (TIA/EIA):**  
1. **Cat 5:** Up to 100 Mbps, 100 m distance, common in older LANs.  
2. **Cat 5e:** Up to 1 Gbps, reduced crosstalk, common today.  
3. **Cat 6:** Up to 10 Gbps for short distances, improved performance.  
4. **Cat 6a:** 10 Gbps at longer distances, enhanced shielding.  

**Example:**  
- Connecting office computers to a switch using Cat 6 cables.

---

## 5. Fiber Optic Cabling
**4 Bases for Fiber Optic:**  
1. **Single-mode Fiber (SMF):** Small core, uses lasers, long-distance, high-speed.  
2. **Multi-mode Fiber (MMF):** Large core, uses LEDs, short to medium distance, cost-effective.  
3. **OM1:** Legacy multi-mode, 62.5 µm core, slower speeds.  
4. **OM3/OM4:** Optimized for high-speed 10/40/100 Gbps over multi-mode fiber.  

**Example:**  
- Data center connections between racks using single-mode fiber for long-distance backbone.  

---

## 6. Real-Life Scenarios
1. **Office LAN:** Star topology with Cat 6 cables connecting PCs to a switch; CSMA/CD ensures collision-free communication.  
2. **Campus Network:** Multi-mode fiber between buildings, single-mode fiber for backbone to support 10 Gbps.  
3. **Troubleshooting:** SOC analyst checks collisions, bandwidth utilization, or faulty cabling to investigate slow performance or connectivity issues.

---

## 7. SOC Perspective
- Ethernet knowledge helps **monitor traffic, detect anomalies, and identify misconfigurations**.  
- Logs from switches and routers indicate collisions, dropped frames, and network performance issues.  
- Understanding topologies and media aids in **incident response** and **network forensics**.

---


