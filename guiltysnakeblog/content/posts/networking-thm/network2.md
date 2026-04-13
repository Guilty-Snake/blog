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

#### TTL
The IP has a fielt called Time-To-Live (TTL), it is used to calculate the number of routers a packet can go through before it is dropped. A router decreases the value of TTL each time a packet passes through and when TTL reaches zero a ICMP type 11 TIme Exceeded message is sent.


