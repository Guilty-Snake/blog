---
title: "Networking Core Protocols"
date: 2026-04-23
tags: ['THM', 'Cybersecurity101', 'Networking']
image: "images/Network_protocols.png"
---
## Learning Objectives
* WHOIS
* DNS
* HTTP and FTP
* SMTP, POP3, and IMAP

## DNS
DNS or Domain Name System is a protocol which in simple terms resolves traffic from a readable url like google.com to its respective ip address through DNS servers which stores records such as the ones given below:
* A record: The A (Address) record maps a hostname to one or more IPv4 addresses. For example, you can set example.com to resolve to 172.17.2.172.
* AAAA Record: The AAAA record is similar to the A Record, but it is for IPv6. Remember that it is AAAA (quad-A), as AA and AAA would refer to a battery size; furthermore, AAA refers to Authentication, Authorization, and Accounting; neither falls under DNS.
* CNAME Record: The CNAME (Canonical Name) record maps a domain name to another domain name. For example, www.example.com can be mapped to example.com or even to example.org.
* MX Record: The MX (Mail Exchange) record specifies the mail server responsible for handling emails for a domain.

DNS operates at the application layer and uses UDP port 53 by default and TCP port 53 as a default fallback.

## WHOIS
When registering a domain one must provide accurate contact information, which can be viewed by everyone through **whois**, which provides information about the entity that registered a domain name, including name, phone number, email, and address.

## HTTP(S)
HTTP stands for Hyper Text Transfer Protocol and HTTPS is the more secure version, its S standing for secure. This protocol relies on TCP and defines how your web browser communicates with the web servers.
HTTP and HTTPS commonly use TCP ports 80 and 443, respectively.

Some methods browsers use to communicate with a webserver are:
* **GET** retrieves data from a server, such as an HTML file or an image.
* **POST** allows us to submit new data to the server, such as submitting a form or uploading a file.
* **PUT** is used to create a new resource on the server and to update and overwrite existing information.
* **DELETE**, as the name suggests, is used to delete a specified file or resource on the server.
