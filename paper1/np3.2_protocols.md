---
title: Paper 1 lesson 3.2 - Protocols and Standards
---

# Standards (3.1.2)

A **standard** is an agreed-upon way of formatting data, exchanging information, or otherwise *doing* or *creating* something. Technically, to be officially defined as a standard, the rules must be approved by some sort of official body, called a *standards organization*. Computer networking is entirely about exchanging information, so for that to work it is very important that the computers and people using the information agree on what the information will look like. Think of this as an agreed-upon *language* for computers to share information globally.

We have already seen some examples of standards back in Topic 2, such as the standard for [representing characters](np2.6_representing_characters.md) (ASCII or Unicode).

# Protocols (3.1.6 and 3.1.7)

A **protocol** is an agreed-upon system for exchanging information. Most protocols are standards, but some protocols are not because they are *proprietary* - for example, the way that messges are sent using discord may not be standardized, it may be secret to discord, but it is still a protocol. 

Protocols allow for several important features in data exchange, including

* **data integrity** - protocols can help ensure that the data received by the receiving computer is complete.
* **flow control** - protocols can help make sure data is received in the correct order
* **deadlock** - protocols can help ensure that a network doesn't get "stuck" waiting for data
* **congestion** - protocols can help make sure that networks don't get too full, which can lead to deadlock above.
* **error checking** - this is similar to 'data integrity'; protocols can create systems to make sure that data doesn't have any errors.

Let's consider four protocols now, to have a basic understanding.

## Ethernet

This protocol allows computers that are connected over a LAN to communicate with each other. The basic process is this: 

1. A computer decides to send some information to another computer over the network
2. It adds a *header* to the data it wants to send that contains the MAC address of the destination computer
3. It then checks to see if the "cable" is available. if it is, it will take over the cable to send the message.
   1. This means that every computer connected to that cable can actually see the data! The protocol states that only the computer whose MAC address is on the header will *listen*, but that's just an agreement.
4. IF the "cable" is currently being used, then it will wait a programmed amount of time (that is partially random) to try again - this is to reduce *congestion* and avoid *deadlock*.

Ethernet works really well with a small number of computers, or a large number of computers that aren't using the network a lot. As congestion increases, it becomes important to break an ethernet network into smaller pieces and connect them using hardware such as *switches* or *routers*.

## IP

IP is the **internet protocol**. It is concerned with how to get pieces of information to computers that are very far away.

The primary thing that defines the IP is the IP Address. Every computer that wants to interact with the internet needs to have an IP address that serves as its location on the network.

Your IP address is 4 bytes. You might see it as something like 172.26.0.1 . This was settled on to make it user rememberable back when there were only a few hundred computers using the internet.

The internet protocol defines the way that **routers** can find the best pathway to send a message over the various wires connecting the internet together.

Every packet sent over the internet starts with a header that contains the destination IP address and **port**, a number which tells to the receiving computer which application the IP address is intended for. For example, world wide web traffic (also known as HTTP traffic) is most commonly sent to port 80 or port 443.

Routers will often change the ports of outgoing traffic as a way of keeping track of which *computer* on a local network is requesting a response; this is called **port mapping** and is one way to manage the fact that there are not enough IP addresses for every device in the world to have its own.

## TCP

TCP is the **transport control protocol**. It is concerned with *how the computer* breaks up its information into packets, labels those packets, and ensures that the packets are all put together correctly.

In TCP, the following happens:

1. A header is added to each packet that contains the number of packets in the current piece of information. So for example, if I am sending a giant video file, it might be made of 5000 packets. it ALSO contains which packet out of that 5000 this packet is.
   1. A header might look like "This is a video file. It is packet 23/5000."
2. The receiving computer will examine each packet as it comes in and it will send a reply that it received that packet. 
3. If the sending computer doesn't receive a response within a certain amount of time it will automatically resend the packet.
4. Once all packets are received, the receiving computer will assemble them and give them to the correct program.

This can result in many resent packets if there are any issues on the line between the two computers. It also means that every single piece of information sent requires multiple pieces of information back and forth. However, it is also EXTREMELY reliable! The packet is going to get there eventually as long as a connection exists.

## UDP

The **user datagram protocol** is a different protocol for sending and receiving and assembling packets. In this protocol, the sending computer will put a packet number and a final number on the packet, but they never resend and do not expect responses.

Ths results in a system that is more efficient, but it is possible that packets are never received. A time-sensitive application like video streaming would likely use UDP, since missed and re-sent packets would arrive too late to be useful.

## TCP/IP or UDP/IP

When you combine TCP and IP together, you get a combination protocol often simply referred to as "TCP/IP", which is considered the foundational protocol combination of the modern internet. Of course, some of it uses UDP isntead, but you rarely see the phrase "UDP/IP". These protocols work together to label packets with an address and port (IP), a packet count and number (TCP/UDP), and set up a system of rules that govern routing (IP) and packet receipt confirmation (TCP); everything the internet is is built on those ideas.

## DNS Protocol

The DNS protocol, or **domain name server** protocol, defines the system by which computers can convert human-readable names like "google.com" to actual IP address, like 142.251.128.78 . This is done through a combination of local files and information hosted by special servers on the internet called DNS servers.    

## HTTP

The **hyper-text transfer protocol** defines the system for sending information that is associated with the World-Wide Web. It was designed for communication between web servers and browsers, but is a pretty flexible protocol that can be used to send all kinds of information.

The basic structure involves a client, usually a web browser, sending requests called GET requests to get information from a local server such as web pages, pictures, files, etc. The server sends each of those elements to the browser independently, which then combines them together.

Here is an example of an HTTP *response* message, just to give you an idea of what it looks like:

```
HTTP/1.1 200 OK
Date: Sat, 09 Oct 2010 14:28:02 GMT
Server: Apache
Last-Modified: Tue, 01 Dec 2009 20:18:22 GMT
ETag: "51142bc1-7449-479b075b2891b"
Accept-Ranges: bytes
Content-Length: 29769
Content-Type: text/html
```

