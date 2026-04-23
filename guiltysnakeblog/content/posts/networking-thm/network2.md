---
title: "Networking Essectials"
date: 2026-04-13
tags: ['THM', 'Cybersecurity101', 'Networking']
image: "images/Basic-network.jpg"
---
## Learning Objectives
* Dynamic Host Configuration Protocol (DHCP)
* Address Resolution Protocol (ARP)
* Network Address Translation (NAT)
* Internet Control Message Protocol (ICMP)
    * Ping
    * Traceroute

## DHCP
In simple termes DHCP is a protocal set to automatically assign a ip address to new devices on a network so it can be connected to all other devices.
DHCP is an application-level protocol that relies on UDP; the server listens on UDP port 67, and the client sends from UDP port 68.

<img src="../DHCP-dora.svg" alt="DORA" width="420" height="280">

DHCP steps:
1. DHCP Discover: The client broadcasts a DHCPDISCOVER message seeking the local DHCP server if one exists.
2. DHCP Offer: The server responds with a DHCPOFFER message with an IP address available for the client to accept.
3. DHCP Request: The client responds with a DHCPREQUEST message to indicate that it has accepted the offered IP.
4. DHCP Acknowledge: The server responds with a DHCPACK message to confirm that the offered IP address is now assigned to this client.

## ARP
Two devices on the same network cannot communicate with each other without knowing each other's MAC address. ARP is the protocol that makes it possible to find the mac address of another device on the same network.

A device sends an ARP request asking for communication to a device with a specific ip address which is sent from the mac address of the requestor the broadcast mac address i.e ff:ff:ff:ff:ff:ff. Then the other device responds with a ARP reply sharing their mac address.
ARP is considered a layer 2 protocol as it deals with mac addresses.

## ICMP
ICMP is used for network diagnostics and error reporting, two popular commands that rely on ICMP are:
* ping:<br>This command uses ICMP to test connectivity to a target system and measures the round-trip time (RTT). In other words, it can be used to learn if a target is alive and if its reply can reach a system.
* traceroute:<br>It uses ICMP to discover the route from a host to target.

### TTL
The IP has a fielt called Time-To-Live (TTL), it is used to calculate the number of routers a packet can go through before it is dropped. A router decreases the value of TTL each time a packet passes through and when TTL reaches zero a ICMP type 11 TIme Exceeded message is sent.

**traceroute** makes use of TTL to discover routers between a system and a site but it too has it caveats as some routers might simply drop the packets without sending any ICMP message, and in some cases ICMP the time excedded message can get blocked as well.

## Routing
The internet has billions of devices and millions of routers connected to each other, as such for two systems to connect to each other but as there are a large number of paths some are less efficient than others, to find the most optimal path routing algorithms are utilized:
* **OSPF (Open Shortest Path First):** <br>
OSPF is a routing protocol that allows routers to share information about the network topology and calculate the most efficient paths for data transmission. It does this by having routers exchange updates about the state of their connected links and networks. This way, each router has a complete map of the network and can determine the best routes to reach any destination.
* **EIGRP (Enhanced Interior Gateway Routing Protocol):** <br>
EIGRP is a Cisco proprietary routing protocol that combines aspects of different routing algorithms. It allows routers to share information about the networks they can reach and the cost (like bandwidth or delay) associated with those routes. Routers then use this information to choose the most efficient paths for data transmission.
* **BGP (Border Gateway Protocol):** <br>
BGP is the primary routing protocol used on the Internet. It allows different networks (like those of Internet Service Providers) to exchange routing information and establish paths for data to travel between these networks. BGP helps ensure data can be routed efficiently across the Internet, even when traversing multiple networks.
* **RIP (Routing Information Protocol):** <br>
RIP is a simple routing protocol often used in small networks. Routers running RIP share information about the networks they can reach and the number of hops (routers) required to get there. As a result, each router builds a routing table based on this information, choosing the routes with the fewest hops to reach each destination.

## NAT
As the number of devices connected to the internet kept increasing it became apparant that IPv4 would run out quickly, as a solution to this issue **Network Address Translation(NAT)** is utilized. 
In simple terms instead of a company with dozens of computers needing indivial ip address for each computer, they instead share the same public ip address to connect to the internet.
NAT-supporting routers maintain a table translating network addresses between internal and external networks. The internal network will use a private IP address range, while the external network would use a public IP address which can be observed on the image below.

<img src="../NAT.svg" alt="NAT" width="640" height="420">




