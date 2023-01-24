# Sumário

1. [Backend Developer Roadmap](#computer-science-roadmap)
2. [Internet](#internet)  
    2.1 [How does the internet work?](#21-how-does-the-internet-work)  
    2.2 [Who runs the internet?](#22-who-runs-the-internet)  
    2.3 [Some terms](#23-some-terms)  
    2.4 [Ping program](#24-ping-program)  
    2.5 [Protocol Stacks and Packets](#25-protocol-stacks-and-packets)  
    2.6 [traceroute program](#26-traceroute-program)  
    2.7 [Internet Protocols](#27-internet-protocols)  

---

## 1. Backend Developer Roadmap

Thanks to roadmap.sh  and Kamran Ahmed for providing this and more amazing roadmaps. 
You can access the complete roadmap at the link: [🔗 Backend Developer](https://roadmap.sh/backend)

## 2. Internet

[🎥 How does the internet work?](https://roadmap.sh/guides/what-is-internet)

### 2.1 How does the internet work?

**Intenet != web** 
- Web is just one o many internet apllications. Other popular ones include email and BitTorrent.

**Three basic parts**
- The last mile => Connects homes and small businesses to the internet.
- Data centers => Rooms full of servers.
- The backbone => Long-distance networks - Carry data beteween data centers and consumers.

### 2.2 Who runs the internet?
- Internet os a decentralized network of networks.
- The standardas are managed by  an organization called **Internet Engineering Task Force - IETF**.
- **Internet Corporation for Assigned Names and Numbers - ICANN -** is resposible for internet governance. ICANN is in charge of distributin domain names an IP addresses, but doesn't control who or what kind of information can be sent over it.

### 2.3 Some terms
- **IP address** => Internet Protocol addresses, numbers that identify a client. Ex: 216.146.46.10. 
- **IPv6** => Natural evolution of IPv4. The IPv4 only allows for about 4 billion Ip addresses. IPv6 allows a number 39 digits long!.
- **Cloud** => Cloud computing allows consumers and businesses to treat computing as a utility, leaving the technical details to technology companies.
- **Packet** => Basic unit of information transmitted over the internet. A packet has two parts. The header contains information that helps the packet get to its destination, including the length of the packet, its source and destination, and a checksum value that helps the recipient detect if a packet was damaged in transit. After the header comes the actual data. A packet can contain up to 64 kilobytes of data, which is roughly 20 pages of plain text. If internet routers experience congestion or other technical problems, they are allowed to deal with it by simply discarding packets. It’s the sending computer’s responsibility to detect that a packet didn’t reach its destination and send another copy. This approach might seem counterintuitive, but it simplifies the internet’s core infrastructure, leading to higher performance at lower cost.
- **World Wide Web** => The web is just one of many internet applications supporting hyperlinks,  images, audio, video, and interactive content. World Wide Web Consortium (W3C) to be the web’s official standards organization.
- **Web Browser** => Computer program that allows users to download and view websites.
- **Secure Sockets Layer - SSL** => Family of encryption technologies that allows web users to protect the privacy of information they transmit over the internet.
- **Domain Name System - DNS** => The reason you can access Google by typing google.com into your browser rather than a hard-to-remember numeric address such as 216.146.46.10.

See more at: [🔗 How Does the Internet Work?](http://web.stanford.edu/class/msande91si/www-spr04/readings/week1/InternetWhitepaper.htm)

### 2.4 Ping program

Windows and Linux have a program named ping. The ping program will send a 'ping' (actually an ICMP (Internet Control Message Protocol) echo request message) to the named computer. The pinged computer will respond with a reply. The ping program will count the time expired until the reply comes back (if it does). Also, if you enter a domain name (i.e. www.google.com) instead of an IP address, ping will resolve the domain name and display the computer's IP address.
```bash
    ping google.com
```

### 2.5 Protocol Stacks and Packets
|Protocol Layer|Comments|
|------|------|
|Application Protocols Layer|Protocols specific to applications such as WWW, e-mail, FTP, etc.|
|Transmission Control Protocol Layer|TCP directs packets to a specific application on a computer using a port number.|
|Internet Protocol Layer|IP directs packets to a specific computer using an IP address.|
|Hardware Layer|Converts binary packet data to network signals and back.|

```
 v Application               Application  ↑
 | TCP                       TCP          | 
 | IP                        IP           |
 ↳ Hardware --> Internet --> Hardware    ⤴

 Your Computer               Another Computer
(1.2.3.4)                   (5.6.7.8)
```

### 2.6 traceroute program

Another nice program is the **tracetroute** it shows the path your packets are taking to a given Internet destination. Like ping, you must use traceroute from a command prompt.
```bash
    traceroute www.google.com
```
For windows users, the command is ```tracert www.google.com```

### 2.7 Internet Protocols

- Hypertext Transfer Protocol - HTTP => HTTP is a connectionless text based protocol. Clients (web browsers) send requests to web servers for web elements such as web pages and images. After the request is serviced by a server, the connection between client and server across the Internet is disconnected. A new connection must be made for each request. Most protocols are connection oriented. This means that the two computers communicating with each other keep the connection open over the Internet. HTTP does not however. Before an HTTP request can be made by a client, a new connection must be made to the server.
```bash
    curl www.google.com --head
```
- Application Protocols: SMTP ands Electronic Mail => E-mail uses an application level protocol called Simple Mail Transfer Protocol or SMTP. SMTP is also a text based protocol, but unlike HTTP, SMTP is connection oriented. SMTP is also more complicated than HTTP. There are many more commands and considerations in SMTP than there are in HTTP.
- Transmission Control Protocol - TCP => TCP is responsible for routing application protocols to the correct application on the destination computer. There is no place for an IP address in the TCP header. This is because TCP doesn't know anything about IP addresses. TCP's job is to get application level data from application to application reliably. The task of getting data from computer to computer is the job of IP.
- Internet Protocol - IP => Unlike TCP, IP is an unreliable, connectionless protocol. IP doesn't care whether a packet gets to it's destination or not. Nor does IP know about connections and port numbers. IP's job is too send and route packets to other computers.

```
                    Complete packet
<------------------------------------------------------>
| IP header | TCP header | data from application layer |
<--20bytes--><--20bytes-->
```
