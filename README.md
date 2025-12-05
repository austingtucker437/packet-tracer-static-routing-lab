# Packet Tracer Static Routing Lab (Two-LAN Network)

This project demonstrates how to design, configure, and troubleshoot a two-LAN network connected by two routers using **Cisco Packet Tracer**. The lab includes switch and router configuration, IP addressing, static routing, connectivity testing, and real troubleshooting of interface issues.

This repository contains:
- Full network topology  
- All device configurations  
- Static routing setup  
- Troubleshooting steps and solutions  
- Ping verification tests  
- Screenshots documenting the entire build  

---

# **Project Overview**

This lab simulates two separate LANs connected through two routers:

- **LAN A** → Router0 → Router1 → **LAN B**  
- Each LAN has 2 PCs and 1 switch  
- Routers are connected via a GigabitEthernet crossover link  
- Static routing is used to allow communication between LANs  

The goal was to:
1. Build the topology  
2. Assign correct IP addressing  
3. Configure routers and interfaces  
4. Add static routes  
5. Test same-LAN and cross-LAN communication  
6. Troubleshoot red/down interfaces  
7. Verify full connectivity  

---

# **Final Network Topology**

### Initial Topology (Before Cabling)
![Initial Topology (Before Cabling)](screenshots/Initial%20Topology%20(Before%20Cabling).png)

---

# **Physical Cabling Layout**

### 📷 Completed Physical Topology (With Cables)
![Completed Physical Topology (With Cables)](screenshots/Completed%20Physical%20Topology%20(With%20Cables).png)

---

# **IP Addressing Plan**

| Device | IP Address | Subnet Mask | Gateway |
|--------|------------|-------------|---------|
| PC0 | 192.168.10.10 | 255.255.255.0 | 192.168.10.1 |
| PC1 | 192.168.10.11 | 255.255.255.0 | 192.168.10.1 |
| Router0 G0/0 | 192.168.10.1 | 255.255.255.0 | — |
| Router0 G0/1 | 10.10.10.1 | 255.255.255.252 | — |
| Router1 G0/1 | 10.10.10.2 | 255.255.255.252 | — |
| Router1 G0/0 | 192.168.20.1 | 255.255.255.0 | — |
| PC2 | 192.168.20.10 | 255.255.255.0 | 192.168.20.1 |
| PC3 | 192.168.20.11 | 255.255.255.0 | 192.168.20.1 |

---

# **Router Configuration Summary**

## **Router0**
```bash
enable
configure terminal
interface gigabitEthernet0/0
 ip address 192.168.10.1 255.255.255.0
 no shutdown
interface gigabitEthernet0/1
 ip address 10.10.10.1 255.255.255.252
 no shutdown
exit
ip route 192.168.20.0 255.255.255.0 10.10.10.2

enable
configure terminal
interface gigabitEthernet0/0
 ip address 192.168.20.1 255.255.255.0
 no shutdown
interface gigabitEthernet0/1
 ip address 10.10.10.2 255.255.255.252
 no shutdown
exit
ip route 192.168.10.0 255.255.255.0 10.10.10.1


Connectivity Testing

After configuring devices and static routes, the following tests were performed:

Same LAN Ping Tests

PC0 → PC1 = Success

PC2 → PC3 = Success

Cross LAN Ping Tests (After Static Routes)

PC0 → PC2

PC0 → PC3

PC1 → PC2

PC1 → PC3
All = Success


Troubleshooting Summary

During the lab, Router1’s G0/0 interface and the switch port initially showed red/down.

Fix applied:

enable
configure terminal
interface gigabitEthernet0/0
 no shutdown

Final Connectivity Test  Cross Network Ping
Cross LAN Ping Output

All devices across both LANs successfully communicated, confirming correct static routing.


Skills Demonstrated

Network topology design

Subnetting and IP addressing

Router and switch configuration

Interface troubleshooting

Static routing

End to end connectivity testing

Repository Structure

packet-tracer-static-routing-lab/
│
├── README.md
└── screenshots/
    ├── Initial Topology (Before Cabling).png
    ├── Completed Physical Topology (With Cables).png
    ├── Final Network State — All Links Up (Green).png
    └── 03-cross-network-ping-success.png


Conclusion

This lab demonstrated the process of designing and configuring a multi LAN network using Cisco Packet Tracer.
Troubleshooting interface issues, applying static routes, and validating communication across networks.


Contact/Portfolio

If you’d like to explore more of my labs or reach out:

GitHub: https://github.com/austingtucker437
