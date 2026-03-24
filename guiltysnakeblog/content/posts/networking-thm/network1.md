---
title: "Networking Concepts"
date: 2026-03-24
tags: ['THM', 'Cybersecurity101', 'Networking']
image: "images/networking.webp"
---
## OSI Model
The OSI(Open Systems Interconnection) model is a conceptual model created by ISO(International Organization for Standarization) that describes how network communication should occur in a computer network. So, it provides a framework for computer network communications.

<img src="../OSILayers.svg" alt="OSI Layers" width="420" height="280">

### Layer 1 Physical Layer
The Physical Layer of the OSI model includes the physical connections between devices, including medium such as wires. The transmission of data can be done through electrical/optical signals or wireless signals. Depending on the medium different physical component may be required such as wires or antennas.

### Layer 2 Data Link Layer
Data link layer represents the protocols that enables data transfer between nodes on the same network segment. A network negment refers to a group of networked i.e. connected devices using the a shared medium or channel to transfer information.

The data link layer refers to the agreement i.e. protocol between different systems on a network segment on how to communicate.

Examples of layer 2 include Ethernet, i.e., 802.3, and WiFi, i.e., 802.11. Ethernet and WiFi addresses are six bytes. Their address is called a MAC address, where MAC stands for Media Access Control. They are usually expressed in hexadecimal format with a colon separating each two hexadecimal digits (one byte). The three leftmost bytes identify the vendor while the rightmost identifies a network interface. Eg: a4:c3:f0(intel):85:ac:2d

### Layer 3 Network Layer
The network layer, i.e., layer 3, is concerned with sending data between different networks. In more technical terms, the network layer handles logical addressing and routing, i.e., finding a path to transfer the network packets between the diverse networks.

Examples of the network layer include Internet Protocol (IP), Internet Control Message Protocol (ICMP), and Virtual Private Network (VPN) protocols such as IPSec and SSL/TLS VPN.



### Layer 4 Transport Layer
Layer 4, the transport layer, enables end-to-end communication between running applications on different hosts. For example when viewing this site one's web browser will be connected to a github webserver.

Examples of layer 4 are Transmission Control Protocol (TCP) and User Datagram Protocol (UDP).

### Layer 5 Session Layer
The session layer is responsible for establishing, maintaining, and synchronising communication between applications running on different hosts. Establishing a session means initiating communication between applications and negotiating the necessary parameters for the session. Data synchronisation ensures that data is transmitted in the correct order and provides mechanisms for recovery in case of transmission failures.

Examples of the session layer are Network File System (NFS) and Remote Procedure Call (RPC).

### Layer 6 Presentation Layer
The presentation layer ensures the data is delivered in a form the application layer can understand.

 Layer 6 handles data encoding, compression, and encryption. An example of encoding is character encoding, such as ASCII or Unicode.

### Layer 7 Application Layer
The application layer provides network services directly to end-user applications. Our web browser would use the HTTP protocol to request a file, submit a form, or upload a file.

The application layer is the top layer, and you might have encountered many of its protocols as you use different applications. Examples of Layer 7 protocols are HTTP, FTP, DNS, POP3, SMTP, and IMAP. Don’t worry if you are not familiar with all of them.

### Table
| Layer Number | Layer Name | Main Function | Example Protocols and Standards |
| --- | --- | --- | --- |
| Layer 7 | Application layer | Providing services and interfaces to applications | HTTP, FTP, DNS, POP3, SMTP, IMAP |
| Layer 6 | Presentation layer | Data encoding, encryption, and compression | Unicode, MIME, JPEG, PNG, MPEG |
| Layer 5 | Session layer | Establishing, maintaining, and synchronising sessions | NFS, RPC |
| Layer 4 | Transport layer | End-to-end communication and data segmentation | UDP, TCP |
| Layer 3 | Network layer | Logical addressing and routing between networks | IP, ICMP, IPSec |
| Layer 2 | Data link layer | Reliable data transfer between adjacent nodes | Ethernet (802.3), WiFi (802.11) |
| Layer 1 | Physical layer | Physical data transmission media | Electrical, optical, and wireless signals |