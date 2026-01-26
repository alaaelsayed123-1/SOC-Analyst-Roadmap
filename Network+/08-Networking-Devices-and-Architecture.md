# Networking Devices and Network Architecture

## TL;DR – SOC Summary
- Understanding **networking devices, adapters, and media converters** is critical for SOC Analysts to monitor traffic, troubleshoot connectivity issues, and identify misconfigurations or unauthorized devices.
- Key focus: **Adapters, Hubs, Bridges, Switches, Media Converters, Wireless Access Points**

---

## Network Adapters
- A **network adapter** connects a computer or device to a network.  
- Supports Ethernet, Wi-Fi, or fiber depending on hardware and network architecture.  
- Examples:  
  - Ethernet NIC for LAN  
  - Fiber NIC for server connections  

**SOC Note:** NIC logs are essential to track connected devices and detect rogue endpoints.

---

## Transceivers and Modules
- **Transceiver:** Converts electrical signals to optical signals and vice versa for fiber connections.  
- **SFP/XFP Modules:** Small form-factor pluggable modules for fiber or high-speed Ethernet links.  
- **Use Case:** LAN server only has fiber NIC, LAN switch supports only twisted pair → use **media converter** to connect them.  

---

## Network Devices Overview

### HUB
- Broadcasts incoming traffic to all ports.  
- Works at **Layer 1 (Physical Layer)**.  
- Example: PC1 sends data → HUB forwards it to PC2, PC3, PC4.  

**SOC Note:** Hubs generate **high broadcast traffic** visible in network monitoring.

### BRIDGE
- Connects two network segments and filters traffic based on MAC addresses.  
- Reduces collisions between segments.  
- Works at **Layer 2 (Data Link Layer)**.  
- Example: Bridge connects two LANs → only forwards frames destined for the other segment.  
- Slower than a switch due to **shared virtual circuit**.

### SWITCH
- Connects multiple devices and builds a **MAC address table**.  
- Allows direct communication between ports (virtual circuits).  
- Works at **Layer 2 (Data Link Layer)**.  
- Switches include bridges internally but are faster due to **direct port-to-port forwarding**.  

**SOC Note:** Switch MAC tables help track devices and detect unauthorized hosts or MAC spoofing.

### Wireless Access Point (WAP)
- Connects wireless devices to a wired LAN.  
- Filters traffic by **MAC address**.  
- Example: Laptop connects via Wi-Fi → AP forwards traffic to switch port.  
- Supports monitoring for rogue devices and signal interference.  

---

## Media Converters
- Converts signals from **twisted pair to fiber** or vice versa.  
- Example: LAN using twisted pair → server only fiber NIC → media converter ensures connectivity.  

**SOC Note:** Media converter logs help trace cross-media connections and troubleshoot fiber/Ethernet link issues.

---

## SOC Analyst Perspective
- Misconfigured bridges, hubs, or APs can cause **collisions, broadcast storms, or unauthorized access**.  
- Switch and AP MAC tables provide critical visibility into **network topology** and connected devices.  
- Media converters, transceivers, and modules are key points for monitoring **traffic entering or leaving secure zones**.  

---

## Summary
Understanding **networking devices, adapters, and media conversion** ensures:  

1. Proper device connectivity  
2. Efficient traffic management  
3. Accurate monitoring of network flows  
4. Quick detection of anomalies and unauthorized devices

