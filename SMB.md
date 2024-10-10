# SMB(Simple Message Block) Exploitation

## Difference Between NetBIOS & SMB

<div style="text-align: justify">
Many a times people tend to get a bit confused between these two things. That’s why I thought about writing this article that hopefully will clear out some things for you. NetBIOS and SMB do kind of the same job of enabling communication between two applications on different devices in a network but they are entirely two different things.
What is NetBIOS 
</div>


<div style="text-align: justify">
NetBIOS is an acronym that stands for Network Basic Input Output System. It might seem like a protocol but isn’t one, it is an API that provides session layer services that allow applications on different computers to communicate over the LAN. In modern networks NetBIOS runs over TCP/IP via the NetBIOS over TCP/IP or commonly known as NBT protocol. This results in each computer on the network having a NetBIOS name along with the IP Address corresponding to the host name.
</div>

### NetBIOS provides three distinct services:

* NetBIOS-NS: 
<div style="text-align: justify">
Name service, used for name registration and resolution like DNS. In order to initiate a session, an application has to register its NetBIOS name using this service. In NBT this service runs on UDP port 137 and can also be seen rarely on TCP port 137.
</div>

* NetBIOS-DGM: 
<div style="text-align: justify">
Datagram distribution service, connection-less. Runs on UDP (as you might’ve guessed) port 138. As it is connection-less service, the application is responsible for error detection and data recovery.
</div>

*NetBIOS-SSN: 

<div style="text-align: justify"> 
Session service for connection-oriented communications. This service lets two devices establish a connection and also has error detection and recovery unlike datagram distribution service. It runs on TCP port 139.
</div>

## What is SMB

<div style="text-align: justify">
SMB stands for Server Message Block. It is an application layer protocol that is mainly used for providing shared access to things like files and printers on the network. For instance, whenever you send a print request to the printer that is present inside you LAN, SMB is used to send the print request. It is based on request-response model.
</div>

### SMB usually runs on top of the Session (and lower) layers of the OSI model. And it can do so in a few ways:

    * Run directly over TCP port 445. On Windows SMB can run directly over TCP/IP without the need for NBT, using services like microsoft-ds that allow direct hosting of SMB via port 445.
    * Run via NetBIOS API which in turn can run in several different ways — on UDP ports 137, 138 or TCP ports 139 as we saw earlier in the NetBIOS section.

TLDR: SMB runs on top of NetBIOS over TCP/IP (NBT), however SMB does not rely on NetBIOS for communication. NetBIOS is simply an API that other technologies use and is completely independent from SMB.
