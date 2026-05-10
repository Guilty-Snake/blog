---
title: Networking Secure Protocols
date: 2026-05-09
tags: ['THM', 'Cybersecurity101', 'Networking']
image: "images/security-protocols.webp"
---
## Learning objectives
* SSL/TLS
* Securing existing plain text protocol:
    * HTTP
    * SMTP
    * POP3
    * IMAP
* How SSH replaced the plaintext TELNET
* How VPN creates a secure network over an insecure one

## TLS
In the early days of the internet all data used to be in plain text so attacks had to simply capture packets to view users credentials. Due to lack of secure communication on the internet Secure Sockets Layer was created, more versions of it were realased.

Transport Layer Security(TLS) is now the successor of SSL (TLS 3.0 to be specific), similar to SSL it is a cryptographic protocol which operates on the transport layer of the OSI model. It allows for a secure communication between a client and a server over an otherwise insecure network.

#### Overview of how  of how TLS is setup and used:
The first step for every server (or client) that needs to identify itself is to get a signed TLS certificate. Generally, the server administrator creates a Certificate Signing Request (CSR) and submits it to a Certificate Authority (CA); the CA verifies the CSR and issues a digital certificate. Once the (signed) certificate is received, it can be used to identify the server (or the client) to others, who can confirm the validity of the signature. For a host to confirm the validity of a signed certificate, the certificates of the signing authorities need to be installed on the host. In the non-digital world, this is similar to recognising the stamps of various authorities. The screenshot below shows the trusted authorities installed in a web browser.
<center><img src="../certificate-manager.png" alt="certificate manager" width="640" height="420"></center>

## HTTPS
HTTPS is the http protocol carried out over the TLS which makes the protocol more secure. The following are the common steps a client has to go through to request a page over https(after resolving a domain name):
1. Establish a TCP three-way handshake with the target server
2. Establish a TLS session
3. Communicate using the HTTP protocol; for example, issue HTTP requests, such as GET / HTTP/1.1
For a HTTP page on the otherhand a client only has to go through step 1 and 3.
> To view the content of an HTTPS page in cleartext a encryption key is required.

## SMTPS, POP3S, and IMAP5
Adding TLS to SMTP, POP3, and IMAP is no different than adding TLS to HTTP. Similar to how HTTP gets an appended S for Secure and becomes HTTPS, SMTP, POP3, and IMAP become SMTPS, POP3S, and IMAPS, respectively. Using these protocols over TLS is no different than using HTTP over TLS; therefore, almost all the points from the HTTPS discussion apply to these protocols.
#### Insecure and secure ports of protocols:

| Protocol | Default Port |
| :--------: | :--------: |
| HTTP    | 80   |
| SMTP    | 25   |
| POP3    | 110  |
| IMAP    | 143  |

Secure versions over TLS:
| Protocol | Default Port |
| :--------: | :--------: |
| HTTPS    | 443   |
| SMTPS    | 465&507 |
| POP3S    | 995  |
| IMAPS    | 993  |

## SSH
Secure shell(ssh) is now used ove **telnet** as it encrypts the traffic it sends. 
Benefits of SSH over telnet:
* **Secure authentication:** Besides password-based authentication, SSH supports public key and two-factor authentication.
* **Confidentiality:** OpenSSH provides end-to-end encryption, protecting against eavesdropping. Furthermore, it notifies you of new server keys to protect against man-in-the-middle attacks.
* **Integrity:** In addition to protecting the confidentiality of the exchanged data, cryptography also protects the integrity of the traffic.
* **Tunneling:** SSH can create a secure “tunnel” to route other protocols through SSH. This setup leads to a VPN-like connection.
* **X11 Forwarding:** If you connect to a Unix-like system with a graphical user interface, SSH allows you to use the graphical application over the network.
>While the TELNET server listens on port 23, the SSH server listens on port 22.

## SFTP and FTPS
SFTP stands for SSH File Transfer Protocol and allows secure file transfer. It is part of the SSH protocol suite and shares the same port number, 22. If enabled in the OpenSSH server configuration, you can connect using a command such as sftp username@hostname. Once logged in, you can issue commands such as get filename and put filename to download and upload files, respectively. Generally speaking, SFTP commands are Unix-like and can differ from FTP commands.

To setup a SFTP server an obtion needs to be enabled in OpenSSH server.
>SFTP shares port with SSH i.e. 22 while FTPS uses port 990 by default.

## VPN
If a user connects to a VPN(Virtual Private Network) server in Japan, they will appear to the servers they access as if located in Japan. These servers will customise their experience accordingly, such as redirecting them to the Japanese version of the service. The screenshot below shows the Google Search page after connecting to a VPN server in Japan. When a VPN tunnel is established all traffic goes through the VPN connection.
So if anyone tries to view a user's traffic they will only be able to see the vpns ip address isolating a user from prying eyes.

In many scenarios once a VPN connection is established all traffic is routed through the VPN tunnel however not all VPN connections do this. A VPN server maybe configured to give one access to a private network but not to route one's traffic.
>Testing a VPN prior to using it is advisable