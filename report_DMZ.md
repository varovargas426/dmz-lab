
# DMZ Configuration Report with Cisco Packet Tracer

### 1. Lab Objective

> Briefly explain what was intended to be achieved with this lab.

The objective of this lab was to configure a secure DMZ using a Cisco ISR router in Cisco Packet Tracer. NAT and ACLs were implemented to control traffic between the internal LAN, the DMZ server zone, and the external network.

The goal was to safely expose a web server to external users while protecting the internal network from unauthorized access.

---

### 2. Implemented Topology

> Describe the network. You can include an image if the software allows it (Packet Tracer screenshot).

- **Number of networks:** 3

- **Devices used:**
  - 1 Cisco ISR 2911 Router (`Router_FW`)
  - 3 Cisco 2960 Switches
  - 1 PC_Internal
  - 1 Server_DMZ
  - 1 PC_External

- **Brief description of each zone:**

  - **LAN:** Trusted internal user network used by employees or local users.
  - **DMZ:** Public-facing zone where the web server is located.
  - **External:** Simulated internet network used to test outside access.

---

### 3. IP Addressing Plan

Complete the table with the assigned IPs.

| Device                | IP            | Mask            | Gateway       |
|-----------------------|---------------|-----------------|---------------|
| PC_Internal           | 192.168.1.10  | 255.255.255.0   | 192.168.1.1   |
| Server_DMZ            | 192.168.2.10  | 255.255.255.0   | 192.168.2.1   |
| PC_External           | 192.168.3.10  | 255.255.255.0   | 192.168.3.1   |
| Router_FW Gi0/0 (LAN) | 192.168.1.1   | 255.255.255.0   | N/A           |
| Router_FW Gi0/1 (DMZ) | 192.168.2.1   | 255.255.255.0   | N/A           |
| Router_FW Gi0/2 (Ext) | 192.168.3.1   | 255.255.255.0   | N/A           |

---

### 4. Applied Configuration (Summary)

> Summarize the most relevant commands or steps you executed. Use text + code snippets as needed.

- Interfaces configured with `ip address`

```bash
interface g0/0
ip address 192.168.1.1 255.255.255.0
no shutdown

interface g0/1
ip address 192.168.2.1 255.255.255.0
ip nat inside
no shutdown

interface g0/2
ip address 192.168.3.1 255.255.255.0
ip nat outside
no shutdown
```

### 5. Verifications Performed

> Describe the tests and their results. Include screenshots or command outputs if possible.

ping from PC_Internal to router (192.168.1.1): ✅
ping from Server_DMZ to router (192.168.2.1): ✅
Web access from PC_Internal to http://192.168.2.10: ✅
Web access from PC_External to http://192.168.3.1: ✅
Ping from PC_External to 192.168.3.1: ❌ Blocked
Ping from Server_DMZ to PC_Internal (192.168.1.10): ❌ Blocked
NAT translation verified with show ip nat translations: ✅
ACL counters verified with show access-lists: ✅

### 6. Conclusions and Recommendations

> What did you learn from this exercise? What would you improve?

This lab helped me understand how to apply NAT and ACLs in a simulated enterprise environment.

I learned that a DMZ is useful to publish public services without exposing the internal LAN directly. I also learned how ACLs can restrict traffic between zones and improve security.

One important lesson was that firewall rules must be tested carefully, because incorrect ACL rules can block legitimate traffic.

Recommendations:

Verify IP addressing before configuring ACLs.
Test connectivity before and after applying security rules.
Use DMZ zones for public-facing services.
Save configurations regularly.
Validate both blocked and allowed traffic.



### 7. Evidence Screenshots

> Attach here (or in an annexed PDF) the requested screenshots: pings, browser, `show` commands, etc.
*Screenshots annexed in PDF

