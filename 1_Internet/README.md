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
3. [HTTP](#3-http)
    3.1 [What is in a HTTP request?](#31-what-is-in-a-http-request) 
        3.1.1 [What is an HTTP method?](#311-what-is-an-http-method)
        3.1.2 [HTTP request header](#312-http-request-header)
        3.1.3 [HTTP request body](#313-http-request-body)
    3.2 [What is in an HTTP response?](#32-what-is-in-an-http-response)
        3.2.1 [What's an HTTP status code?](#321-whats-an-http-status-code)
        3.2.2 [HTTP response headers](#322-http-response-headers)
        3.2.3 [HTTP response body](#323-http-response-body)

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

## 3. HTTP

First things first, HTTP is the TCP/IP based application layer communication protocol which standardizes how the client and server communicate with each other. It defines how the content is requested and transmitted across the internet. By application layer protocol, I mean it's just an abstraction layer that standardizes how the hosts (clients and servers) communicate and itself it depends upon TCP/IP to get request and response between the client and server. By default TCP port 80 is used but other ports can be used as well. HTTPS, however, uses port 443.

HTTP is generally designed to be simple and human-readable, even with the added complexity introduced in HTTP/2 by encapsulating HTTP messages into frames. HTTP messages can be read and understood by humans, providing easier testing for developers, and reduced complexity for newcomers.

While the core of HTTP itself is stateless, HTTP cookies allow the use of stateful sessions. Using header extensibility, HTTP Cookies are added to the workflow, allowing session creation on each HTTP request to share the same context, or the same state.

[🔗 Journey to HTTP/2](https://kamranahmed.info/blog/2016/08/13/http-in-depth)  
[🏆🔗 HTTP Crash Course & Exploration](https://youtu.be/iYM2zFP3Zn0)

### 3.1 What is in a HTTP request?

Each HTTP request made across the Internet carries with it a series of encoded data that carries different types of information. A typical HTTP request contains:  

a. HTTP version type  
b. a URL  
c. an HTTP method  
d. HTTP request headers  
e. Optional HTTP body 

#### 3.1.1 What is an HTTP method?

An HTTP method, sometimes referred to as an HTTP verb, indicates the action that the HTTP request expects from the queried server. For example, two of the most common HTTP methods are ‘GET’ and ‘POST’;

[🔗 HTTP request methods](https://developer.mozilla.org/en-US/docs/Web/HTTP/Methods)

#### 3.1.2 HTTP request header

```
:authority: www.google.com
:method: GET
:path: /
:scheme: https
accept: text/html
accept-encoding: gzip, deflate, br
accept-language: en-US, en;q-0.9
upgrade-insecure-request: 1
user-agent: Mozilla/5.0
```

#### 3.1.3 HTTP request body

The body of a request is the part that contains the ‘body’ of information the request is transferring. The body of an HTTP request contains any information being submitted to the web server, such as a username and password, or any other data entered into a form.

### 3.2 What is in an HTTP response?

A typical HTTP response contains:  
a. an HTTP status code  
b. HTTP response headers  
c. optional HTTP body

#### 3.2.1 What's an HTTP status code?

HTTP status codes are 3-digit codes most often used to indicate whether an HTTP request has been successfully completed. Status codes are broken into the following 5 blocks:  

a. 1xx Informational  
b. 2xx Success  
c. 3xx Redirection  
d. 4xx Client Error  
e. 5xx Server Error  

[🔗 HTTP response status codes](https://developer.mozilla.org/en-US/docs/Web/HTTP/Status)

#### 3.2.2 HTTP response headers
```
    cache-control: private, max-age=0
    content-encoding: br
    content-type: text/html; charset=UTF-8
    date: Thu, 21 Dec 2017 18:25:08 GMT
    status: 200
    strict-transport-security: max-age=86400
    x-frame-options: SAMEORIGIN
```

#### 3.2.3 HTTP response body

Successful HTTP responses to ‘GET’ requests generally have a body which contains the requested information. In most web requests, this is HTML data that a web browser will translate into a webpage.