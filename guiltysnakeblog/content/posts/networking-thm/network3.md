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

>DNS operates at the application layer and uses UDP port 53 by default and TCP port 53 as a default fallback.

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

## FTP
HTTP is used webpages where as FTP(File Transfer Protocol) is designed for file transfer.
Example commands defined by the FTP protocol are:
* USER is used to input the username
* PASS is used to enter the password
* RETR (retrieve) is used to download a file from the FTP server to the client.
* STOR (store) is used to upload a file from the client to the FTP server.

>FTP server listens on TCP port 21 by default; data transfer is conducted via another connection from the client to the server.

## SMTP: Sending Email
Simple Mail Transfer Protocol is a protocol for sending emails which defines how a mail clients talks with a mail server and how a mail server with another.

Commands used by mail client when it transfer email to an SMTP server:
* **HELO** or **EHLO** initiates an SMTP session
* **MAIL FROM** specifies the sender’s email address
* **RCPT TO** specifies the recipient’s email address
* **DATA** indicates that the client will begin sending the content of the email message
* **.** is sent on a line by itself to indicate the end of the email message

>The SMTP server listens on TCP port 25 by default. Telnet was used to utilize SMTP through the CLI but has now been mostly replaced by SSH since it transmits data through plaintext.

## POP3: Receiving Email
The Post Office Protocol version 3(POP3) allows a client to receive an email sent to them through SMTP.
Common POP3 commands:
* **USER <username>** identifies the user
* **PASS <password>** provide the user's password
* **STAT** requests the number of messages and total size
* **LIST** list all messages and their sizes
* **RETR <message_number>** retrieves the message
* **DELE <message_number>** marks a message for deletion
* **QUIT** ends the POP3 session applying changes such as deletions
>the POP3 server listens on TCP port 110 by default.

## IMAP: Synchronizing Email
In the current decade everyone has multiple devices which they use on a daily basis so POP3 which can only save messages on 1 device has now become outdated. Internet Message Access Protoco(IMAP) is now used instead POP3 dues to its capability to synchronizing read, moved, and deleted messages via multiple clients.
Some IMAP commands:
* **LOGIN <username> <password>** authenticates the user
* **SELECT <mailbox>** selects a mailbox to work with
* **FETCH <mail_number> <data_item_name>** Example fetch 3 body[] to fetch message number 3, header and body.
* **MOVE <sequence_set> <mailbox>** moves the specified messages to another mailbox
* **COPY <sequence_set> <data_item_name>** copies the specified messages to another mailbox
* **LOGOUT** logs out
>The IMAP server listens on TCP port 143 by default.
