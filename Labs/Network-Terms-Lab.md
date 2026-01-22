# Network Terms Lab – Practical Observations

## Lab Objective
Understand network connectivity, addressing, firewall behavior, and device communication in practice.

---

## Lab Environment
- Two PCs in the same LAN
- Firewall enabled/disabled
- Ping and arp commands

---

## Steps and Observations

1. **Ping on Same Network**
   - PCs on the same subnet can ping each other successfully.
   - **SOC Note:** Monitoring internal traffic helps detect abnormal lateral movement.

2. **Ping on Different Networks**
   - Without routing, ping fails.
   - **SOC Note:** Identifies need for proper routing and ACL configuration.

3. **Firewall Enabled**
   - Ping requests are blocked (Request Timed Out).
   - **SOC Note:** Firewall logs are essential for detecting blocked traffic.

4. **Firewall Disabled**
   - Ping succeeds.
   - **SOC Note:** Shows which hosts communicate freely and highlights potential attack vectors.

5. **Subnet Mask Observation**
   - Correct subnet mask ensures devices identify each other as same network or different network.
   - **SOC Note:** Misconfigured subnet masks can cause traffic to be blocked or misrouted.

---

## Key Takeaways
- Understanding LAN/WAN connectivity is fundamental for network monitoring.
- Firewalls directly affect visibility and connectivity.
- SOC teams must track device and traffic behavior for security insights.

