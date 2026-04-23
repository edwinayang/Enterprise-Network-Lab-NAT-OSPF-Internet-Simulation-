# Enterprise-Network-Lab-NAT-OSPF-Internet-Simulation
This project simulates a real-world enterprise network accessing the internet using Cisco Packet Tracer.
It combines dynamic routing (OSPF) with Network Address Translation (NAT/PAT) to allow internal users with private IP addresses to communicate with an external server.

 #Topology

topology1.jpg
NAT.jpg
Ping-from-pc.jpg
ip-route.jpg

 #Network Design
Internal Network (LAN)
Network	Gateway
192.168.10.0/24	192.168.10.1
#WAN Link (R1 ↔ R2)
Device	IP Address
R1-NAT	10.0.0.1
R2-ISP	10.0.0.2

Network: 10.0.0.0/30

Internet Network
Device	IP Address
R2-ISP	200.0.0.1
Server	200.0.0.10

Network: 200.0.0.0/24

## Technologies Used
Cisco Packet Tracer
OSPF (Open Shortest Path First)
NAT/PAT (Port Address Translation)
Router-on-a-Stick (subinterfaces)
Basic network troubleshooting
## OSPF Configuration
R1-NAT
router ospf 1
network 192.168.10.0 0.0.0.255 area 0
network 10.0.0.0 0.0.0.3 area 0
R2-ISP
router ospf 1
network 10.0.0.0 0.0.0.3 area 0
network 200.0.0.0 0.0.0.255 area 0
 NAT Configuration (R1-NAT)
interface g0/0.10
ip nat inside

interface g0/1
ip nat outside

access-list 1 permit 192.168.10.0 0.0.0.255

ip nat inside source list 1 interface


#What I Learned
How NAT enables private networks to access the internet
Difference between routing (OSPF) and translation (NAT)
Importance of correct interface roles (inside vs outside)
How to troubleshoot NAT and routing issues
How enterprise networks connect to ISPs
