
# TCP vs UDP – Deep Dive (Structure, Mechanisms, Detection & Logs)

## TL;DR (SOC Summary)
- **TCP** is reliable, stateful, and logged heavily (handshakes, retransmissions, resets).
- **UDP** is fast, stateless, and harder to monitor (commonly abused in attacks).
- SOC analysts monitor **TCP flags, sequence numbers, window sizes, and errors**
- Abnormal TCP/UDP behavior often indicates **scans, DoS, spoofing, or data exfiltration**

---

## Why TCP and UDP Exist
Different applications have different needs:
- Some need **reliability** → TCP
- Some need **speed** → UDP

Both operate at the **Transport Layer** and provide **host-to-host communication**.

---

## TCP – Transmission Control Protocol

### Key Characteristics
- Connection-oriented
- Reliable delivery
- Sequencing and acknowledgments
- Flow control and congestion handling

---

## TCP Segment Structure (Fields Explained)

### TCP Header Fields

- **Source Port**: Sending application port
- **Destination Port**: Receiving application port
- **Sequence Number**: Identifies the position of data in the stream
- **Acknowledgment Number**: Confirms received data
- **Header Length**: Size of TCP header
- **Reserved**: For future use
- **Flags**:
  - **URG** – Urgent data
  - **ACK** – Acknowledgment valid
  - **PSH** – Push data immediately
  - **RST** – Reset connection
  - **SYN** – Synchronize sequence numbers
  - **FIN** – Finish connection
- **Window Size**: Flow control (how much data can be received)
- **Checksum**: Error detection
- **Urgent Pointer**: Points to urgent data
- **Options**: MSS, window scaling, timestamps
- **Padding**: Aligns header
- **Data**: Actual payload

---

## TCP Flags – Why They Matter (SOC View)

| Flag | Purpose | SOC Relevance |
|----|----|----|
| SYN | Start connection | SYN floods |
| ACK | Confirm receipt | Session tracking |
| FIN | Graceful close | Normal termination |
| RST | Force close | Scans, crashes |
| PSH | Immediate delivery | Data exfil |
| URG | Priority data | Rare, suspicious |

---

## TCP Three-Way Handshake (How & Why)

### Step-by-Step Flow

1. **SYN**
   - Client sends SYN with initial sequence number
2. **SYN-ACK**
   - Server responds with its sequence number and ACK
3. **ACK**
   - Client acknowledges → connection established

### Why This Matters
- Prevents half-open connections
- Synchronizes sequence numbers
- Enables reliable communication

---

## Sequence Numbers (Security Perspective)

- Randomized to prevent prediction
- Ensure correct ordering of packets

### Attacks
- **TCP Sequence Prediction**
- **Session Hijacking**
- **Blind Spoofing**

**SOC Detection:**
- Unusual ACK patterns
- Duplicate sequence numbers
- Mid-session SYN packets

---

## TCP Flow Control (Sliding Window)

### How It Works

1. Receiver advertises window size
2. Sender transmits data within window
3. Receiver acknowledges received data
4. Window adjusts dynamically

### Error Handling
- Lost packet → retransmission
- Timeout → resend
- Corruption → checksum failure

**SOC Note:** Excessive retransmissions may indicate congestion or attack.

---

## Where TCP Appears in Logs (IMPORTANT)

- Firewall logs: SYN, RST spikes
- IDS/IPS: abnormal flags
- Server logs: connection resets
- NetFlow: session duration anomalies

---

## UDP – User Datagram Protocol

### Key Characteristics
- Connectionless
- No sequencing
- No acknowledgments
- Minimal overhead

---

## UDP Segment Structure

- **Source Port**
- **Destination Port**
- **Length**
- **Checksum**
- **Data**

---

## UDP Communication Mechanism

1. Application sends data
2. UDP wraps data
3. IP routes packet
4. Receiver processes if available

No handshake. No retries.

---

## Why UDP Is Used
- Fast
- Low latency
- Real-time communication

**Used By:** DNS, DHCP, VoIP, Streaming, TFTP

---

## UDP Security Risks

- Spoofing
- Amplification attacks
- Reflection attacks
- Data loss unnoticed

**SOC Detection:**
- High-volume UDP traffic
- One-way communication
- Unusual port usage

---

## TCP vs UDP Comparison

| Feature | TCP | UDP |
|----|----|----|
| Connection | Yes | No |
| Reliability | Guaranteed | Not guaranteed |
| Speed | Slower | Faster |
| Logging | Rich | Limited |
| Attack Surface | Session-based | Volume-based |

---

## Detection & Logs Summary (SOC-Critical)

### TCP Indicators
- SYN floods
- RST storms
- Window size manipulation
- Abnormal handshake failures

### UDP Indicators
- DNS amplification
- NTP reflection
- Unidirectional flows
- Sudden traffic spikes

---

## Final SOC Summary
TCP provides visibility, reliability, and control — making it easier to monitor.
UDP sacrifices reliability for speed — making it attractive for attackers.

Understanding **fields, flags, flows, and logs** is essential for:
- Threat detection
- Incident response
- Network forensics
