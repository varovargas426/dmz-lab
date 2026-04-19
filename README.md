# DMZ Lab - Cisco Packet Tracer

## Project Overview

This project demonstrates the implementation of a secure **Demilitarized Zone (DMZ)** using Cisco Packet Tracer.

The objective of the lab was to configure a network divided into three security zones:

- **LAN (Internal Network)**
- **DMZ (Public Server Zone)**
- **External Network (Internet Simulation)**

Security technologies such as **Static NAT** and **Access Control Lists (ACLs)** were implemented to control traffic between zones, securely publish a web server, and protect the internal network from unauthorized access.

---

## Main Goals

- Configure router interfaces and IP addressing
- Implement Static NAT for public web server access
- Apply ACL rules to restrict unnecessary traffic
- Validate connectivity and security behavior
- Simulate a real enterprise firewall and DMZ environment

---

## Repository Contents

### Packet Tracer File

Contains the completed network topology and final router configuration.

### report/

Includes the technical report:

- `report_DMZ.md`

### evidence/

Contains screenshots of:

- Full topology
- Browser access tests
- Blocked traffic tests
- NAT verification
- ACL verification
- Interface status

---

## Final Result

The DMZ server was successfully published to the external network while the internal LAN remained protected through ACL filtering and network segmentation.
