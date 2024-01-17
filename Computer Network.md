## Chapter- 1: Roadmap

### Overview

#### Basic components

- Server

  A server is a computer or system that provides resources,data, services, or programs to other computers, known as clients, over a network.

- Client

  a client is a computer that accesses a service made available by a server.

- Hub（集线器）

  Hub is a device that splits a network connection into multiple computers.

- Router（路由器）

  A Router is a networking device that receives and forwards data packets between computer networks.

- Data cable

  Data cables are used to transmit the information from a source to a destination.

- Peers（对等）

  a peer is also a node that accesses a service made available by a server.

#### Transmission modes

- Types of data communication 
  - Simplex Mode（单工）
  - Half-Duplex Mode（半双工）
  - Full-Duplex Mode（全双工）
- Data communication ways in computer networks
  - Unicast（单播）
  - Broadcast（广播）
  - Multicast（多播）

#### Network structure

- End systems（网络边缘）

  Computers, switches（交换机, routers, hubs, printers, servers, smart phone and tablet

- Access networks（网络核心）

- Links

  Fiber optics（光纤）, Coaxial pair cable（同轴电缆）, copper（铜线）, radio wave, micro wave

#### Physical media

- Guided media
  - Twisted-pair copper wire: The least expensive and most commonly used. The data rate depends on the thickness of the wire and the distance. 
  - Coaxial Cable: Better immunity to noise and hence signal strength is better for longer distances.
  - Fiber optic cables: A single optical fiber can support high bit rates, up to tens or even hundreds of gigabits per second.
- Unguided media
  - radio wave, micro wave and Infrared signals

### The network core

- Circuit switching（电路交换）: Used in telephone networks.

  - Frequency Division Multiplexing（FDM频度复用）

  <img src="C:\Users\Crazbeans\Desktop\HappyThing\计算机网络\image-20240114160002468-17052192064121.png" alt="image-20240114160002468" style="zoom:50%;" />

  - Time Division Multiplexing（TDM时间复用）

    <img src="C:\Users\Crazbeans\Desktop\HappyThing\计算机网络\image-20240114160225712-17052193479013.png" alt="image-20240114160225712" style="zoom:50%;" />

- Packet switching（分组交换）: The source breaks long messages into smaller chunks of data known as packets.

  - Store-and-Forward Transmission（存储与转发）: The packet switch must receive the entire packet before it can begin to transmit the first bit of the packet onto the out link.
  - Delays:
    - processing delay
    - queuing delay
    - transmission delay
    - propagation delay
  - Packet loss:  An arriving packet may find that the buffer is completely full with other packets waiting for transmission and packet loss will occur, the already-queued packets will be dropped.

### Networks topology

- Bus topology: a common bus or channel is used for communication in the network.
- Star Topology: all the nodes are connected to a centralized hub.
- Ring topology: each computer is connected to exactly two other computers.
- Tree topology: This topology combines the properties of a bus topology and a star topology.

## Chapter- 2: Application Layer

###  Internet protocol stack

- Application Layer（应用层）: 网络应用，HTTP&SMTP&FTP.......
- Transport Layer（传输层）: 主机之间的通信，确保数据的可靠性，TCP&UDP
- Network Layer（网络层）: 提供端到端之间的通信，IP
- Link Layer（链路层）: 提供相邻两端之间的通信
- Physical Layer（物理层）: 在线路上传输bit

### Application Layer  mode

#### Network application architectures

- Client server architecture（Web, FTP, e-mail）
  - Servers are always on, has a permanent and fixed IP address
  - Clients communicate with server, may have dynamic IP addresses
- Peer-to-peer (P2P) architecture

#### Processes communicating

- A network application consists of pairs of processes that send messages to each other over a network. 
- Socket（套接字）
  - TCP Socket keeps the destination IP address, destination port, source IP address and source port.
  - Process sends/receives messages to/from its socket


### Application Layer Examples

#### HTTP

- Hyper Text Transfer Protocol (HTTP): Web’s application layer protocol.

![img](C:\Users\Crazbeans\Desktop\HappyThing\计算机网络\060828381f30e924d1997f3a6756df0e1d95f767.png)

- RTT(round-trip time): time for a small packet to travel from client to server and back.
- Cookies are messages that web servers pass to your web browser when we visit internet sites.

#### E-mail

- Three major components: 
  - User agents: User agents allow users to read, reply to, forward, save, and compose, edit messages.
  - Mail servers: mailbox and message queue
  - SMTP (simple mail transfer protocol)
- The process of an e-mail:
  - Alice uses UA to compose message  to bob@someschool.edu
  - Alice’s UA sends message to her mail server; message placed in message queue
  - Client side of SMTP opens TCP connection with Bob’ s mail server
  - SMTP client sends Alice’ s message over the TCP connection
  - Bob’s mail server places the message in Bob’s mailbox
  - Bob’s mail server places the message in Bob’s mailbox
- Mail access protocols
  - POP, IMAP and HTTP

#### DNS

- DNS is a directory service that provides a mapping between the name of a host on the network and its IP address.
- The DNS client sends a query containing the hostname to a DNS server and the DNS client eventually receives a reply, which includes the IP address for the hostname.

#### P2P

- Unlike client-server architecture, there is no central server for processing requests in a P2P architecture.
- Arbitrary end systems directly communicate.
- Example: file distribution (BitTorrent)

#### CDN

- Content Distribution Network（CDN） is a solution that provides faster delivery of content to the users distributed worldwide.
- A CDN is essentially a group of servers that are strategically placed across the globe with the purpose of accelerating the delivery of web content.

## Chapter- 3: Transport Layer

### Overview

- It provides logical communication between application processes.
- It relies on, enhances, network layer services.
- Internet transport-layer protocols
  - Transmission Control Protocol（TCP）is a reliable, connection-oriented service.
  - User Datagram Protocol（UDP）is an unreliable, connectionless service.

### Multiplexing/demultiplexing

- Multiplexing at sender
  - Handle data from multiple sockets, add transport header
  - Encapsulating each data with header information to create segments, and passing the segments to the network layer is called multiplexing
- Demultiplexing at receiver
  - Use header info to deliver received segments to correct socket
  - At the receiving end, the transport layer examines these fields to identify the receiving socket and then directs the segment to that socket

<img src="C:\Users\Crazbeans\Desktop\HappyThing\计算机网络\image-20240114224346955-17052434280167.png" alt="image-20240114224346955" style="zoom:50%;" />

### UDP

- There is no need to establish a connection prior to data transfer and each UDP segment handled independently of others.
- Data lost and Unreliable.

<img src="C:\Users\Crazbeans\Desktop\HappyThing\计算机网络\image-20240114225005502-17052438069139.png" alt="image-20240114225005502" style="zoom: 45%;" /><img src="C:\Users\Crazbeans\Desktop\HappyThing\计算机网络\image-20240114225551444-170524415224314.png" alt="image-20240114225551444" style="zoom:49%;" />

### TCP

- Feature:
  - Connection oriented service: handshaking
  - Full duplex service data（全双工）: bi-directional data flow in same connection at the same time
  - Reliability: TCP is reliable as it uses checksum for error detection

#### TCP Segment

<img src="C:\Users\Crazbeans\Desktop\HappyThing\计算机网络\image-20240114230314306-170524459545716.png" alt="image-20240114230314306" style="zoom:50%;" />

#### TCP reliable data transfer

- TCP creates reliable data transfer service on top of IP’s unreliable service.
- TCP time-out period often relatively long and detect lost segments via duplicate ACKs.

<img src="C:\Users\Crazbeans\Desktop\HappyThing\计算机网络\image-20240114233219245-170524634067718.png" alt="image-20240114233219245" style="zoom:50%;" />

#### TCP connection management

- TCP 3-way handshake

<img src="C:\Users\Crazbeans\Desktop\HappyThing\计算机网络\image-20240114234117059-170524687985720.png" alt="image-20240114234117059" style="zoom:50%;" />

> Requires both the client and server to exchange SYN (synchronization) and ACK (acknowledgment) packets before actual data communication begins.

- TCP close connection

<img src="C:\Users\Crazbeans\Desktop\HappyThing\计算机网络\image-20240115150556900.png" alt="image-20240115150556900" style="zoom:50%;" />

## Chapter- 4: Network layer

### Overview

- network-layer functions
  - forwarding: move packets from router’s input to appropriate router output.
  - routing: determine route taken by packets from source to destination.
- Data plane（数据平面）
  - local, per-router function
  - determines how datagram arriving on router input port is forwarded to router output port
  - forwarding function
- Control plane（控制平面）
  - determines how datagram is routed among routers along end-end path from source host to destination host
- Interplay between routing and forwarding
  - routing algorithm determines end-end-path through network
  - forwarding table determines local forwarding at this router
- Per-router control plane（每-路由器控制平面）
  - Each and every router interact with each other in control plane to compute forwarding tables
- Logically centralized control plane（逻辑集中控制平面）
  - A distinct (typically remote) controller interacts with local control agents (CAs) in routers to compute forwarding tables

### Dijkstra’s algorithm

<img src="C:\Users\Crazbeans\Desktop\HappyThing\计算机网络\image-20240115162540685.png" alt="image-20240115162540685" style="zoom:50%;" />

- 首先从第一个节点向外标记。之后选出当前距离最短的并且没被选择过的节点继续标记，同时若距离变短则更新该节点的距离，直至最后一个节点被选择。

### Distance vector algorithm 

<img src="C:\Users\Crazbeans\Desktop\HappyThing\计算机网络\image-20240115164552073.png" alt="image-20240115164552073" style="zoom: 50%;" />

- 每个节点定期给相邻的其他节点发送自己的矢量值，并根据其他节点发送的矢量表，计算自己经过这些节点到目标的最小距离。

### Software defined networking

- Individual routing algorithm components in each and every router interact with each other in control plane to compute forwarding tables.

### IP addressing

- IP address: 32-bit identifier for host, router interface.
- IPV4 uses a 32-bit address scheme to store 2^32 addresses which is more than 4 billion addresses.
- IPV6 uses a 128-bit address space, it allows 340 undecillion (36 zeros) unique address space.
- The maximum amount of data that a link-layer frame can carry is called the maximum transmission unit(MTU).

<img src="C:\Users\Crazbeans\Desktop\HappyThing\计算机网络\image-20240115212700492.png" alt="image-20240115212700492" style="zoom:50%;" />

## Chapter- 5: Link Layer

### Overview

- data-link layer has responsibility of transferring datagram from one node to physically adjacent node over a link.
- Framing
  - A frame is consisting of a data field, in which the network-layer datagram is inserted, and a number of header fields.
- Link access
  - channel access in shared medium
- MAC（medium access control）
  - addresses used in frame headers to identify source, destination.

### Error detection

- Parity checking: On receiving a frame, the receiver counts the number of 1s in it.
- Internet checksum: detect “errors” in transmitted packet (note: used at transport layer only)
- Cyclic redundancy check

### Multiple access links and protocols

- Desirable characteristics:
  - When one node wants to transmit, it can send at rate R.
  - When M nodes want to transmit, each can send at average rate R/M
  - no special node to coordinate transmissions and no synchronization of clocks, slots
- Pure ALOHA
  - In pure ALOHA, whenever any node transmits a frame, it expects the acknowledgement from the receiver.
  - If the frame is destroyed because of collision, the node waits for a random amount of time and sends it again.
- Slotted ALOHA
  - In slotted ALOHA, the time of the shared channel is divided into discrete intervals called slots.
  - The nodes can send a data only at the beginning of the slot.
- CSMA
  - CSMA listens to or senses network signals on the carrier/medium before transmitting any data. 
    - If channel sensed idle: transmit entire frame.
    - If channel sensed busy: defer transmission.
- Taking turns
  - Control token passed from one node to next sequentially.

### LANs

- ARP table
  - each IP node (host, router) on LAN has table.
  - IP/MAC address mappings for some LAN nodes.< IP address; MAC address; TTL>
- A wants to send datagram to B（No B's MAC address）:
  - A broadcasts ARP query packet, containing B's IP address to all nodes in LAN
  - B also receives ARP packet, replies to A with its (B's) MAC address
  - A now receive the MAC address of B and send the data accordingly
- send datagram from A to B via R

<img src="C:\Users\Crazbeans\Desktop\HappyThing\计算机网络\image-20240115233432718.png" alt="image-20240115233432718" style="zoom:50%;" />

<img src="C:\Users\Crazbeans\Desktop\HappyThing\计算机网络\image-20240115233601771.png" alt="image-20240115233601771" style="zoom:50%;" />

<img src="C:\Users\Crazbeans\Desktop\HappyThing\计算机网络\image-20240115233613214.png" alt="image-20240115233613214" style="zoom:50%;" />





























































