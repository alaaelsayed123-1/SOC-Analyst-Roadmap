
This means:
- To reach `192.168.20.0/24`
- Send traffic to next-hop router `10.0.0.2`

### Advantages
- Secure (no route advertisements)
- Predictable
- Low CPU and memory usage

### Disadvantages
- Not scalable
- Error-prone
- No automatic failover

### SOC Perspective
- Safer in small networks
- But misconfigurations can cause **blackholes** or traffic leakage

---

## 2. Dynamic Routing (Automatic Method)

### Definition
Dynamic routing allows routers to **automatically learn and share routes** using **routing protocols**.

### What is a Routing Protocol?
A routing protocol is a **set of rules** that routers use to:
- Discover neighboring routers
- Share network information
- Choose the best path to a destination

---

# Routing Protocol Characteristics

## 1. Scope (Where the Protocol Is Used)

### IGP – Interior Gateway Protocol
Used **inside one Autonomous System (AS)**.

Examples:
- RIP
- OSPF
- EIGRP
- IS-IS

### EGP – Exterior Gateway Protocol
Used **between different Autonomous Systems**.

Example:
- BGP

### Example
- Company internal network → OSPF
- ISP to ISP communication → BGP

---

## 2. Metric (How Best Path Is Chosen)

A **metric** is a value used by routing protocols to decide the **best route**.

---

### a) Hop Count
- Counts how many routers a packet passes through.
- Lower hop count = better route.

**Used by:** RIP

#### Example
- Route A → 2 hops
- Route B → 4 hops  
Router chooses **Route A**

⚠ Limitation:
- Does NOT consider speed or bandwidth

---

### b) Bandwidth & Delay
- Bandwidth: speed of the link
- Delay: time taken to transmit data

**Used by:** EIGRP

#### Example
- Path 1: Fast Ethernet (100 Mbps)
- Path 2: Serial link (2 Mbps)

Even if Path 2 has fewer hops, EIGRP chooses **Path 1** because it is faster.

---

### c) Cost (Relative or Link Cost)
- Cost is an assigned value to a link.
- Lower cost = preferred path.

**Used by:** OSPF & IS-IS

#### Example
- Fiber link cost = 10
- Copper link cost = 100  
Router selects fiber link.

---

## 3. Route Sharing Method

### a) Distance Vector Protocols

#### How They Work
- Routers share routing tables with **neighbors only**
- Periodic updates
- Simple logic

#### Example
Router A tells Router B:
> “I can reach Network X in 2 hops”

**Protocols:**
- RIP

#### Problems
- Slow convergence
- Routing loops

---

### b) Link-State Protocols

#### How They Work
- Routers build a **full map of the network**
- Share link-state information
- Faster convergence

#### Example
Each router knows:
- All routers
- All links
- All costs

**Protocols:**
- OSPF
- IS-IS

---

### c) Hybrid Protocols

#### How They Work
- Combine distance vector + link-state features

**Protocol:**
- EIGRP

#### Benefits
- Fast convergence
- Efficient updates
- Uses bandwidth & delay

---

## 4. VLSM Support (Variable Length Subnet Mask)

### Definition
Allows different subnet sizes within the same network.

### Example
Network: 192.168.1.0/24

- Sales → /26
- HR → /27
- IT → /28

**Protocols Supporting VLSM:**
- RIP v2
- OSPF
- EIGRP
- IS-IS
- BGP

**Does NOT support VLSM:**
- RIP v1

---

## 5. Administrative Distance (AD)

### Definition
AD is a **trust value** used when multiple routing protocols know the same route.

Lower AD = more trusted

### Common AD Values
- Directly connected → 0
- Static route → 1
- EIGRP → 90
- OSPF → 110
- RIP → 120
- BGP → 20 / 200

### Example
If a router learns the same network via:
- OSPF (110)
- RIP (120)

Router chooses **OSPF**

---

# Routing Protocols Explained

## RIP (Routing Information Protocol)
- Distance Vector
- Metric: Hop Count (max 15)
- Slow convergence
- Small networks only

---

## EIGRP
- Hybrid
- Metric: Bandwidth + Delay
- Fast convergence
- Cisco proprietary (mostly)

---

## OSPF
- Link-State
- Metric: Cost
- Highly scalable
- Enterprise networks

---

## IS-IS
- Link-State
- Used mainly by ISPs
- Very stable and scalable

---

## BGP
- Exterior Gateway Protocol
- Path-based routing
- Used on the Internet
- Routes between Autonomous Systems

---

## Default Route

### Definition
A route used when **no specific route exists**.

### Example
ip route 192.168.20.0 255.255.255.0 10.0.0.2


This means:
- To reach `192.168.20.0/24`
- Send traffic to next-hop router `10.0.0.2`

### Advantages
- Secure (no route advertisements)
- Predictable
- Low CPU and memory usage

### Disadvantages
- Not scalable
- Error-prone
- No automatic failover

### SOC Perspective
- Safer in small networks
- But misconfigurations can cause **blackholes** or traffic leakage

---

## 2. Dynamic Routing (Automatic Method)

### Definition
Dynamic routing allows routers to **automatically learn and share routes** using **routing protocols**.

### What is a Routing Protocol?
A routing protocol is a **set of rules** that routers use to:
- Discover neighboring routers
- Share network information
- Choose the best path to a destination

---

# Routing Protocol Characteristics

## 1. Scope (Where the Protocol Is Used)

### IGP – Interior Gateway Protocol
Used **inside one Autonomous System (AS)**.

Examples:
- RIP
- OSPF
- EIGRP
- IS-IS

### EGP – Exterior Gateway Protocol
Used **between different Autonomous Systems**.

Example:
- BGP

### Example
- Company internal network → OSPF
- ISP to ISP communication → BGP

---

## 2. Metric (How Best Path Is Chosen)

A **metric** is a value used by routing protocols to decide the **best route**.

---

### a) Hop Count
- Counts how many routers a packet passes through.
- Lower hop count = better route.

**Used by:** RIP

#### Example
- Route A → 2 hops
- Route B → 4 hops  
Router chooses **Route A**

⚠ Limitation:
- Does NOT consider speed or bandwidth

---

### b) Bandwidth & Delay
- Bandwidth: speed of the link
- Delay: time taken to transmit data

**Used by:** EIGRP

#### Example
- Path 1: Fast Ethernet (100 Mbps)
- Path 2: Serial link (2 Mbps)

Even if Path 2 has fewer hops, EIGRP chooses **Path 1** because it is faster.

---

### c) Cost (Relative or Link Cost)
- Cost is an assigned value to a link.
- Lower cost = preferred path.

**Used by:** OSPF & IS-IS

#### Example
- Fiber link cost = 10
- Copper link cost = 100  
Router selects fiber link.

---

## 3. Route Sharing Method

### a) Distance Vector Protocols

#### How They Work
- Routers share routing tables with **neighbors only**
- Periodic updates
- Simple logic

#### Example
Router A tells Router B:
> “I can reach Network X in 2 hops”

**Protocols:**
- RIP

#### Problems
- Slow convergence
- Routing loops

---

### b) Link-State Protocols

#### How They Work
- Routers build a **full map of the network**
- Share link-state information
- Faster convergence

#### Example
Each router knows:
- All routers
- All links
- All costs

**Protocols:**
- OSPF
- IS-IS

---

### c) Hybrid Protocols

#### How They Work
- Combine distance vector + link-state features

**Protocol:**
- EIGRP

#### Benefits
- Fast convergence
- Efficient updates
- Uses bandwidth & delay

---

## 4. VLSM Support (Variable Length Subnet Mask)

### Definition
Allows different subnet sizes within the same network.

### Example
Network: 192.168.1.0/24

- Sales → /26
- HR → /27
- IT → /28

**Protocols Supporting VLSM:**
- RIP v2
- OSPF
- EIGRP
- IS-IS
- BGP

**Does NOT support VLSM:**
- RIP v1

---

## 5. Administrative Distance (AD)

### Definition
AD is a **trust value** used when multiple routing protocols know the same route.

Lower AD = more trusted

### Common AD Values
- Directly connected → 0
- Static route → 1
- EIGRP → 90
- OSPF → 110
- RIP → 120
- BGP → 20 / 200

### Example
If a router learns the same network via:
- OSPF (110)
- RIP (120)

Router chooses **OSPF**

---

# Routing Protocols Explained

## RIP (Routing Information Protocol)
- Distance Vector
- Metric: Hop Count (max 15)
- Slow convergence
- Small networks only

---

## EIGRP
- Hybrid
- Metric: Bandwidth + Delay
- Fast convergence
- Cisco proprietary (mostly)

---

## OSPF
- Link-State
- Metric: Cost
- Highly scalable
- Enterprise networks

---

## IS-IS
- Link-State
- Used mainly by ISPs
- Very stable and scalable

---

## BGP
- Exterior Gateway Protocol
- Path-based routing
- Used on the Internet
- Routes between Autonomous Systems

---

## Default Route

### Definition
A route used when **no specific route exists**.

### Example
ip route 0.0.0.0 0.0.0.0 192.168.1.1


Meaning:
- Send all unknown traffic to gateway `192.168.1.1`

### SOC Perspective
- Attackers often abuse default routes for data exfiltration
- Misconfigured default routes can expose internal networks

---

## Final SOC Takeaways
- Routing protocols affect visibility and security
- Wrong metrics or AD can redirect traffic silently
- Monitoring routing changes is critical in SOC operations
- BGP attacks (route hijacking) are real-world threats

