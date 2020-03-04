# Application Layer


| Material | Authors | Chapter 
| :-:  | :-:     | :-:
| Computer Networking A Top-Down Approach, 6th Edition | Jim Kurose, Keith Ross | 2


Application layer is the fifth layer; think of it as an layer for apps. 

examples given:
* web app
* gaming app
* instant messaging
* e-mail application


<details closed>
<summary>Addressing processes:</summary>
More in chapter 4. For now, all we need to know is that an IP address is a 32-bit quantity that we can think of as uniquely identifying the host. In addition to knowing the address of the host to which a message is destined, the sending process must also identify the receiving process (more specifically, the receiving socket) running in the host. This information is needed because in general a host could be running many network applications. A destination port number serves this purpose. 
</details>

<details closed>
<summary>Transport services available to applications:</summary>
socket is the interface between the application process and the transport-layer protocol. Unless you're making a stand alone application, communication with "peers" is a necessity. Therefore usage of the basic protocols like TCP/UDP or its underlying protocols(HTTP/DHCP) all lie under socket programming.
</details> 

<details closed>
<summary>Reliable Data and throughput</summary>
<ul> 
  <li>
    Applications that have throughput requirements are said to be bandwidth-sensitive applications.
  </li>
  <li>
    elastic applications can make use of as much, or as little, throughput as happens to be available.
  </li>
</ul>
</details> 

### Assignments

2.1:
To be able to evaluate the quality of connections, bandwidth and latency are two important factors. What other factors are important when you are considering
<sup>Chapter 1.4.3: End systems, applications, and other delays</sup>
> A uniform delivery time is needed for voice as well as video, so the amount of jitter in the network is important. This could be expressed as the standard deviation of the delivery time. Having short delay but large variability is actually worse than a somewhat longer delay and low variability.


2.2:
A client-server system uses a satellite network, with the satellite at a height of about 40,000 km. What is the best-case delay in response to a request?
> The request has to go up and down, and the response has also to go up and down. The total path length traversed is thus 160.000 km. Lightspeed is 300,000 km/sec. So the propagation delay alone is about 160,000/300,000 sec or about 533 msec.

3.1
List four broad classes of services that a transport protocol might provide?
<sup>Chapter 2.1.3: Transport Services Available to Applications</sup>
<sup>Chapter 2.1.4: TCP Services</sup>
<sup>Chapter 2.1.4: UDP Services</sup>

> Connection-oriented service: TCP has the client and server exchange transport layer control information with each other before the application-level messages begin to flow.

> Reliable data transfer service: The communicating processes can rely on TCP to deliver all data sent without error and in the proper order.

> Unreliable data transfer service: UDP services, useful for video streams and other.

> Throughout services: the application could request a guaranteed throughput of r bits/sec, and the transport protocol would then ensure that the available throughput is always at least r bits/sec.

Timing services: 
Security services:

3.2
Will web caching reduce delay for all objects requested by a user or only for some of the objects? Why?
<sup>Chapter 2.2.5: Web caching</sup>

> Also called a proxy server. Web caching can bring the desired content “closer” to the user, possibly to the same LAN to which the user’s host is connected. Web caching can reduce the delay for all objects, even objects that are not cached, since caching reduces the traffic on links

5.1
Client-server, P2P, or Hybrid? Section 2.1.1 in your textbook discusses three application architectures: client-server, P2P, and a hybrid of the two. Classify each of the scenarios below as client-server, P2P, or hybrid, and explain your answer briefly
<sup>Kafli 2.1.1 Network Application Architectures</sup>

A) When two Skype clients talk to each other, they do so as peers. However, in order to locate a peer, a Skype client will first contact a directory server in a client-server manner. Therefore, Skype has a hybrid application architecture.

>	When two Skype clients talk to each other, they do so as peers. However, in order to locate a peer, a Skype client will first contact a directory server in a client-server manner. Therefore, Skype has a hybrid application architecture.

B) (EBay is pure client-server application architecture. Ebay is implemented as a Web server (more accurately, a farm of Web servers) that responds to Web client (browser) requests using HTTP.)

> EBay is pure client-server application architecture. Ebay is implemented as a Web server (more accurately, a farm of Web servers) that responds to Web client (browser) requests using HTTP.
C) BitTorrent is a pure P2P application architecture. It is interesting because it will concurrently download different pieces of a file from different peers.)
> (BitTorrent is a pure P2P application architecture. It is interesting because it will concurrently download different pieces of a file from different peers.)
D) (Telnet is a pure client-server application architecture. The client is the process that contacts the Telnet server (at port 23 to allow remote login on the remote machine where the Telnet server process is running).)
> (Telnet is a pure client-server application architecture. The client is the process that contacts the Telnet server (at port 23 to allow remote login on the remote machine where the Telnet server process is running).)
E) (DNS is a pure client-server application architecture. The DNS client is the process that sends the DNS REQUEST message (to port 53 at the DNS server); the server is the DNS server process that replies with a DNS REPLY message.)
>	(DNS is a pure client-server application architecture. The DNS client is the process that sends the DNS REQUEST message (to port 53 at the DNS server); the server is the DNS server process that replies with a DNS REPLY message.)

5.2
(Persistent versus non-persistent HTTP connections. Suppose within your Web browser you click on a link to obtain a Web page. Suppose the IP address for the associated URL is cached in your local host, so that a DNS lookup is not necessary. Denote RTT as the roundtrip time between the local host and the server containing the Web page. Assume the Web page consists of a base HTML file and three small images. Assume the transmission times for all of the objects are negligible in comparison with the RTT. How much time elapses (in terms of RTTs) from when the user clicks on the link until the client receives the entire Web page with each of the following?)
<sup>2.2 The Web and HTTP</sup>
<sup>2.2.2 Non-Persistent and Persistent Connections</sup>
<sup>3.4.2 Pipelined Reliable Data Transfer Protocols</sup>

A) Non-persistent HTTP with no parallel connections.
>(2 RTT for base, 2 RTT to get each image: 4(2 RTT) = 8 RTT in total)
Base: 1RTT = set up connection, 1 RTT = get base html
Images: 1RTT = set upconnection, 1RTT get image
1base + 3image = 2+2+2+2 = 8RTT
B) Non-persistent HTTP with up to five parallel connections.)
>	(2 RTT for base, 2 RTT for remaining three images (three parallel connections): 4 RTT in total)
Base: 1RTT = set up connection, 1 RTT = get base html
Images: 1RTT = set upconnection, 1RTT get images (3 at once is no problem)
C) (Persistent HTTP with pipelining.)
> (2 RTT for base; 1 RTT for remaining three images: 3 RTT in total)
		
6.1
(HTTP basics. The text below shows the reply sent from a server in response to a HTTP GET message.
HTTP/1.1 200 OKDate: Tue, 07 Mar 2006 12:39:45GMT..Server: Apache/2.0.52 (Fedora) Last-Modified: Sat, 10 Dec 2005 18:27:46 GMTETag: "526c3-f22- a88a4c80"AcceptRanges: bytesContent-Length: 3874KeepAlive: timeout=max=100Connection: KeepAliveContent-Type: text/html; charset=ISO88591 

<sup>Chapter 2.2.3: HTTP Message Format</sup>
A) (Was the server able to find the document successfully or not?)
>	(The status code of 200 and the phrase OK indicate that the server was able to locate the document successfully.)
B) At what time was the document reply provided?)
> (The reply was provided on Tuesday, 07 Mar 2006 12:39:45 Greenwich Mean Time.)
C) (When was the document last modified?)
> (The document index.html was last modified on Saturday, 10 Dec 2005 18:27:46 GMT.)
D) (How many bytes are there in the document being returned?)
> (There are 3874 bytes in the document being returned.)
E) (What are the first 5 bytes of the document being returned?)
> (The first five bytes of the returned document are: <!doc)
F) (Did the server agree to a persistent connection?)
> (The server agreed to a persistent connection, as indicated by the “Connection: Keep-Alive“ field.)


