# Network Cabling, Pinouts, and PoE Fundamentals

## TL;DR – SOC Summary
- Understanding **cable pinouts, TX/RX, Ethernet types, console ports, and PoE** is essential for SOC analysts to troubleshoot connectivity, monitor physical network configurations, and identify misconfigurations or unauthorized devices.
- Key focus: **TIA/EIA standards, straight-through vs crossover, rollover cables, PoE injection/splitting**

---

## Cable Pinouts (Twisted Pair)

### TIA/EIA Standards
- Defines two main wiring schemes for twisted pair cables:
  1. **TIA/EIA 568A**
  2. **TIA/EIA 568B**
- Determines the order of the colored wires in RJ-45 connectors
- Ensures compatibility for proper **TX/RX signal alignment**

### TX/RX (Transmit / Receive)
- TX → Transmit pins (send data)
- RX → Receive pins (receive data)
- Proper alignment is crucial for:
  - **Fast Ethernet (100 Mbps)**
  - **Gigabit Ethernet (1 Gbps)**  
- Gigabit Ethernet uses all 8 wires; fast Ethernet uses only 4

---

## Types of Networking Cables

### 1. Straight-Through Cable
- Connects **different devices**: e.g., PC → Switch  
- Both ends wired with same standard (568A → 568A or 568B → 568B)
- TX pins on one end connect to RX pins on the other through the switch
- Common in LANs for end-device connections

### 2. Crossover Cable
- Connects **similar devices directly**: e.g., Switch → Switch, PC → PC
- TX pins connect to RX pins directly without intermediary device
- Flow Example:  
  - PC1 TX → PC2 RX  
  - PC2 TX → PC1 RX

### 3. Rollover Cable (Console Cable)
- Connects PC **serial port** to switch/router console port  
- Pin 1 → Pin 8, Pin 2 → Pin 7 (reversed all 8 wires)
- Used for device management and configuration

---

## Terminating Twisted Pair Cables
- Steps to terminate an Ethernet cable (Straight, Crossover, or Rollover):
  1. Strip cable jacket
  2. Untwist pairs and arrange according to standard (568A/B)
  3. Cut to uniform length
  4. Insert into RJ-45 connector
  5. Crimp with a tool to secure pins
- Ensures proper **TX/RX alignment** and reliable connectivity

---

## Console Ports & Serial Connections
- **Console ports**: Access switch or router configuration directly  
- **Serial ports**: Legacy connections for WAN links  
- Essential for device management, firmware updates, and troubleshooting

---

## Power over Ethernet (PoE)

### What is PoE?
- Delivers **electricity and data** over the same Ethernet cable
- Common for devices like **IP cameras, phones, and wireless access points**

### PoE Types
1. **PSE (Power Sourcing Equipment)**  
   - Switches or injectors that provide power
2. **PD (Powered Device)**  
   - Devices that receive power (IP phones, cameras)

### PoE Flow Example
- **Using Injector**: Switch without PoE → Injector adds power → PD device receives both data and power
- **Using Splitter**: PoE cable → Splitter separates power and data → Non-PoE device receives appropriate power and data

---

## SOC Analyst Perspective
- Miswiring or wrong pinouts can cause:
  - Connectivity issues
  - Device downtime
  - False positive alarms in monitoring tools
- PoE logs are crucial for:
  - Detecting power delivery issues
  - Identifying unauthorized powered devices
- Console/rollover usage helps verify device access and secure configuration

---

## Summary
Understanding **cable types, pinouts, TX/RX, and PoE mechanics** ensures:
- Reliable network connectivity
- Proper device configuration
- Clear visibility into physical and link-layer network behavior for SOC analysis

