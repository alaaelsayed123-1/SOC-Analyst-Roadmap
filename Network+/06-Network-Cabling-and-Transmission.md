
# Network Cabling, Throughput, and Transmission Fundamentals

## TL;DR – SOC Summary
- Understanding network cabling, signal transmission, and physical layer characteristics is critical for **SOC analysts** when analyzing network performance, troubleshooting connectivity issues, or investigating signal-based anomalies.  
- Key metrics: **Throughput, Bandwidth, Latency, Jitter**  
- Cable types and standards impact both **speed** and **security posture**.

---

## Throughput vs Bandwidth

- **Bandwidth**: Maximum rate at which data can theoretically travel through a medium (bits per second).  
  - Units and Prefixes:  
    - bps → bits per second  
    - Kbps → 10³ bps  
    - Mbps → 10⁶ bps  
    - Gbps → 10⁹ bps  
- **Throughput**: Actual rate achieved by data transfer, often lower than bandwidth due to **latency, noise, and protocol overhead**.  

**SOC Note:** Monitoring throughput vs bandwidth can help detect congestion, bottlenecks, or potential DoS attacks.

---

## Transmission Flows and Signal Quality

### Noise
- **Electromagnetic Interference (EMI)**: Disturbance caused by external electromagnetic fields.  
  - Example: Nearby motors, fluorescent lights  
- **Radio Frequency Interference (RFI)**: Disturbance from radio frequency signals.  
  - Example: Wi-Fi devices interfering with coaxial cables  
- **Attenuation**: Signal loss over distance due to resistance, cable imperfections, or bending.  
  - Twisted Pair (TP) cables reduce interference via pairing wires and reversing polarity  
- **SOC Note:** Noise can corrupt packets, triggering retransmissions observable in network logs.

### Latency
- Time it takes a signal to travel from source to destination.
- Measured using **RTT (Round Trip Time)**
- Factors: cable length, routing, propagation speed

### Jitter
- Variation in packet arrival times (out-of-order packets)
- Impacts VoIP and streaming applications
- Can be minimized using **QoS mechanisms**

---

## Duplex and Multiplexing

- **Simplex**: One-way communication only  
- **Half-Duplex**: Two-way communication, but not simultaneous  
- **Full-Duplex**: Two-way simultaneous communication  
- **Multiplexing**: Combining multiple signals on a single medium (e.g., TDM, FDM)

**SOC Note:** Understanding duplex modes helps identify misconfigurations that may degrade network performance or indicate link attacks.

---

## Network Cable Types

### Coaxial Cable
- Components: Inner conductor, insulating layer, braided shield, outer insulating layer  
- Connectors: BNC, F-Connector  
- Use Cases: Legacy Ethernet, CCTV, broadband

### Twisted Pair Cable (TP)
- Types: STP (Shielded), UTP (Unshielded)  
- Twisting reduces EMI and RFI  
- Longer cables may experience higher attenuation  
- Standards: **TIA/EIA 568** defines wiring and maximum supported throughput

### Fiber Optic Cable
- Transmits data using **light through glass or plastic fibers**  
- Advantages: Immunity to EMI/RFI, high bandwidth, long distance  
- Components: Core, cladding, protective coating  

#### Types of Fiber Optic
- **SMF (Single Mode Fiber)**
  - Small core, laser-based
  - Long distance, high-speed backbone networks
- **MMF (Multi-Mode Fiber)**
  - Larger core, LED-based
  - Shorter distances, used in LANs or data centers

---

## Transmission Improvement Strategies

- Use **full duplex** links where possible  
- Minimize **cable length** to reduce attenuation  
- Use **shielded cables** in high EMI environments  
- Implement **fiber optics** for high-speed, long-distance, or secure transmission  
- Proper termination and standards compliance (**TIA/EIA 568**) ensures maximum throughput

---

## SOC Analyst Perspective

- Cable type and quality impact **packet loss, retransmissions, and latency**, visible in network monitoring tools  
- High EMI/RFI areas can indicate **potential vulnerabilities** or **environmental misconfigurations**  
- Fiber optic segments are critical infrastructure; any disruptions should trigger alerts  
- Latency, jitter, and throughput measurements help detect **network performance degradation** or suspicious traffic patterns

---

## Summary
Understanding **network cabling, transmission flows, and physical layer properties** is essential for:

1. Accurate **network troubleshooting**  
2. Identifying **performance bottlenecks**  
3. Detecting anomalies or **interference-based attacks**  
4. Optimizing SOC visibility into physical and link-layer events
