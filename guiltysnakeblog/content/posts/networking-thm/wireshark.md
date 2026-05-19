---
title: Wireshark The Basics
date: 2026-05-10
tags: ['THM', 'Cybersecurity101', 'Networking']
images: "images/wireshark-logo.jpg"
---
## Learning Objectives
* Navigate and configure Wireshark
* Inspect packets and discover information from different layers of TCP/IP
* Apply display filters

## Tool Overview
Wireshark is one of the most popular tools to analyse traffic. Below are some of its usecases:
* Detecting and troubleshooting network problems, such as network load failure points and congestion.
* Detecting security anomalies, such as rogue hosts, abnormal port usage, and suspicious traffic.
* Investigating and learning protocol details, such as response codes and payload data.

### GUI and Data
**Toolbar:** The main toolbar contains multiple menus and shortcuts for packet sniffing and processing, including filtering, sorting, summarising, exporting and merging.  

**Display Filter Bar:** The main query and filtering section.  

**Recent Files:** List of the recently investigated files. You can recall listed files with a double-click.   

**Capture Filter and Interfaces:** Capture filters and available sniffing points (network interfaces).  The network interface is the connection point between a computer and a network. The software connection (e.g., lo, eth0 and ens33) enables networking hardware.  

**Status Bar:** Tool status, profile and numeric packet information.

### Loading PCAP files
A packet capture(PCAP) file can be opened through the file window in wireshark. After loading a PCAP file the following panels can be seen:
**Packet List Pane:**	Summary of each packet (source and destination addresses, protocol, and packet info). You can click on the list to choose a packet for further investigation. Once you select a packet, the details will appear in the other panels.  

**Packet Details Panel:**	Detailed protocol breakdown of the selected packet.  

**Packet Bytes Pane:**	Hex and decoded ASCII representation of the selected packet. It highlights the packet field depending on the clicked section in the details pane.

### Colouring Packets 
Along with quick packet information wireshark also color codes packets based on differenet conditions and protocols making it easier to spot anomolies.  
Wireshark has two types of packet colouring methods: temporary rules that are only available during a program session and permanent rules that are saved under the preference file (profile) and available for the next program session. The "right-click menu" or "View --> Coloring Rules" menu can be used to create permanent colouring rules. The "Colourise Packet List" menu activates/deactivates the colouring rules. Temporary packet colouring is done with the "right-click menu" or "View --> Conversation Filter" menu, which is covered in TASK-5.

### Traffic sniffing
The blue "shark button" can be used to start network sniffing (capturing traffic), the red button will stop the sniffing, and the green button will restart the sniffing process. The status bar will also provide the used sniffing interface and the number of collected packets.

### Merge PCAP files
Wireshark can combine two pcap files into one single file. The "File --> Merge" menu path can be used to merge a pcap with the processed one. When the second file is chosen, Wireshark will show the total number of packets in the selected file. Once one clicks "open", it will merge the existing pcap file with the chosen one and create a new pcap file. 
>Note that one needs to save the "merged" pcap file before working on it.

### View Details
Knowing the file details is helpful. Especially when working with multiple pcap files, sometimes it is needed to know and recall the file details (File hash, capture time, capture file comments, interface and statistics) to identify the file, classify and prioritise it. The details can be viewed by following "Statistics --> Capture File Properties" or by clicking the "pcap icon located on the left bottom".

## Packet Dissection
Packet dissection is also known as protocol dissection which investigates packet details by decodiing availabe protocols and fields. Wireshark supports a large number of protocols for dissection but custom dissection scripts can also be written.

### Packet Details
You can click on a packet in the packet list pane to open its details (double-click will open details in a new window). Packets consist of 5 to 7 layers based on the OSI model. We will go over all of them in an HTTP packet from a sample capture.
We can see seven distinct layers to the packet: frame/packet,source [MAC],source [IP],protocol,protocol errors, application protocol, and application data. Below we will go over the layers in more detail.
* **The Frame (Layer 1):** It will show you what frame/packet you are looking at and details specific to the Physical layer of the OSI model.
* **Source [MAC] (Layer 2):** It will show you the source and destination MAC Addresses; from the Data Link layer of the OSI model.
* **Source [IP] (Layer 3):** It will show you the source and destination IPv4 Addresses; from the Network layer of the OSI model.
* **Protocol (Layer 4):** It will show you details of the protocol used (UDP/TCP) and source and destination ports; from the Transport layer of the OSI model.
**Protocol Errors:** THis continuation of the 4th layer shows specific segments from TCP that needed to be reassembled.
* **Application Protocol (Layer 5):** This will show details specific to the protocol used, such as HTTP, FTP,  and SMB. From the Application layer of the OSI model.

## Packet Navigation
### Packet Numbers
Wireshark calculates the number of investigated packets and assigns a unique number for each packet. This helps the analysis process for big captures and makes it easy to go back to a specific point of an event which can be done by using the "Go" menu option.

### Find Packets
Apart from packet number, Wireshark can find packets by packet content. The "Edit --> Find Packet" menu can be used to make a search inside the packets for a particular event of interest. This helps analysts and administrators to find specific intrusion patterns or failure traces.

This functionality accepts four types of inputs (Display filter, Hex, String and Regex). String and regex searches are the most commonly used search types. Searches are case insensitive, but the case sensitivity can be set in the search by clicking the radio button.

searches can be conducted in the three panes (packet list, packet details, and packet bytes), and it is important to know the available information in each pane to find the event of interest. For example, if you try to find the information available in the packet details pane and conduct the search in the packet list pane, Wireshark won't find it even if it exists.

### Mark Packets
Packets can be marked by clicking "Edit" or the "right-click"  menu. Marked packets will be marked in black regardless of their previous color.
>Marked packet information is renewed every file session.

### Packet Comments
Packets can be commented through "Edit --> Packet" or the "right-click"  menu.

### Exporting
Wireshark can extract files transferred through the wire. For a security analyst, it is vital to discover shared files and save them for further investigation. Exporting objects are available only for selected protocol's streams (DICOM, HTTP, IMF, SMB and TFTP).
Packets can also be exported through the same "File" in the menu.

### Expert Info
Expert info can provide a group of categories in three different severities. Details are shown in the table below:
| Severity | Colour | Info |
|:----------:|:--------:|:------:|
| Chat | Blue | Information on usual workflow. |
| Note | Cyan | Notable events like application error codes. |
| Warn | Yellow | Warnings like unusual error codes or problem statements. |
| Error | Red | Problems like malformed packets. |
   
  

Frequently encountered information groups are listed in the table below:
| Group | Info | Group | Info |
|:-------:|:------:|:-------:|:------:|
| Checksum | Checksum errors | Deprecated | Deprecated protocol usage |
| Comment |  Packet comment detection  | Malformed | Malformed packet detection |

## Packet Filteing














