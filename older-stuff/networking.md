#Networking


##Terminology

* **TCP/IP** – Transmission Control Protocol
* **IP** – Internet Protocol
* **UDP** – User Datagram Protocol
* **BIND** – Berkeley Internet Name Domain. Name server software.
* **dhcpd** – Dynamic Host Configuration Protocol Daemon

`TCP/IP` is a set of communications protocols that define how different types of computers talk to each other.

The name `TCP/IP` refers to an entire suite of data communications protocols. The suite gets its name from two of the protocols that belong to it: the Transmission Control Protocol `TCP` and the Internet Protocol `IP`. It is also called the Internet Protocol Suite `IPS`.

Today’s Internet is built by commercial providers. National network providers, called tier-one providers, and regional network providers create the infrastructure. Internet Service Providers `ISPs` provide local access and user services. This network of networks is linked together in the United States at several major interconnection points called Network Access Points `NAPs`.

An `internet` (lowercase “i”) is any collection of separate physical networks, interconnected by a common protocol, to form a single logical network.

*The* `Internet` (uppercase “I”) is the worldwide collection of interconnected networks, which grew out of the original ARPAnet, that uses `IP` to link the various physical networks into a single logical network.

`Intranets` are `TCP/IP`-based enterprise networks that use Internet techniques and web tools to disseminate internal corporate information.

##TCP/IP Important Features

* Open protocol standards, freely available and developed independently from any specific computer hardware or operating system. This makes TCP/IP ideal for uniting different hardware and software components, even when not communicating over the Internet.
* Independence from specific physical network hardware. This allows TCP/IP to integrate many different kinds of networks. TCP/IP can be run over an Ethernet, a DSL connection, a dial-up line, an optical network, and virtually any other kind of physical transmission medium.
* A common addressing scheme that allows any TCP/IP device to uniquely address any other device in the entire network, even if the network is as large as the worldwide Internet.
* Standardized high-level protocols for consistent, widely available user services.

##Protocol Standards

`Protocols` are formal rules of behavior.

TCP/IP creates a heterogeneous network with open protocols that are independent of operating system and architectural differences.

The open nature of TCP/IP protocols requires an open standards development process and publicly available standards documents.

 Internet standards are developed by the Internet Engineering Task Force (IETF) in open, public meetings.

`RFCs` – The protocols developed in this process are published as 'Requests for Comments' (RFCs). 

There are three basic types of `RFCs`: standards `STD`, best current practices `BCP`, and informational `FYI`.





**OSI** – Open Systems Interconnect Reference Model. An architectural model developed by the International Standards Organization (ISO) that is used to describe the structure and function of data communications protocols.

The OSI Reference Model contains seven layers that define the functions of data communications protocols. These seven layers are often called a **stack** or **protocol stack**.

￼7 – **Application Layer** consists of application programs that use the network.

6 – **Presentation Layer** standardizes data presentation to the applications.



**Peers** – A `peer` is an implementation of the same protocol in the equivalent layer on a remote system. e.g. the local file transfer protocol is the peer of a remote file transfer protocol.

In the abstract, each protocol is concerned only with communicating to its peers; it does not care about the layers above or below it.

However, there must also be agreement on how to pass data between the layers on a single computer, because every layer is involved in sending data from a local application to an equivalent remote application.

Data is passed down the stack from one layer to the next until it is transmitted over the network by the Physical Layer protocols.

At the remote end, the data is passed up the stack to the receiving application.

The individual layers do not need to know how the layers above and below them function; they need to know only how to pass data to them.

Although the OSI model is useful, the TCP/IP protocols don’t match its structure exactly.

The Transport Layer in the `OSI` reference model guarantees that the receiver gets the data exactly as it was sent. In `TCP/IP`, this function is performed by the Transmission Control Protocol `TCP`. However, `TCP/IP` offers a second Transport Layer service, User Datagram Protocol `UDP`, that does not perform the end-to-end reliability checks.

The **Internet Protocol** `IP`, which isolates the upper layer protocols from the underlying network and handles the addressing and delivery of data, is usually described as `TCP/IP`’s Network Layer.

##TCP/IP Protocol Architecture

TCP/IP is generally viewed as being composed of fewer layers than the seven used in the OSI model. Most descriptions of TCP/IP define three to five functional levels in the protocol architecture.

￼4 – **Application Layer** consists of applications and processes that use the network.





As in the OSI model, data is passed down the stack when it is being sent to the network, and up the stack when it is being received from the network.

Each layer in the stack adds control information to ensure proper delivery. This control information is called a `header` because it is placed in front of the data to be transmitted. Each layer treats all the information it receives from the layer above as data, and places its own header in front of that information. The addition of delivery information at every layer is called encapsulation.

When data is received, the opposite happens. Each layer strips off its **header** before passing the data on to the layer above. As information flows back up the stack, information received from a lower layer is interpreted as both a header and data.

Each layer has its own independent data structures. Conceptually, a layer is unaware of the data structures used by the layers above and below it. In reality, the data structures of a layer are designed to be compatible with the structures used by the surrounding layers for the sake of more efficient data transmission.

Still, each layer has its own data structure and its own terminology to describe that structure.

Applications using **TCP** refer to data as a `stream`, while applications using **UDP** refer to data as a message. **TCP** calls data a `segment`, and **UDP** calls its data a `packet`. The **Internet layer** views all data as blocks called `datagrams`.

Most networks refer to transmitted data as `packets` or `frames`.

##A Closer Look at the functions of each layer

### The Network Access Layer

The protocols in this layer provide the means for the system to deliver data to the other devices on a directly attached network.

This layer defines how to use the network to transmit an IP datagram.

Unlike higher-level protocols, **Network Access Layer**


Functions performed at this level include encapsulation of IP datagrams into the frames transmitted by the network, and mapping of IP addresses to the physical addresses used by the network.

The IP address must be converted into an address that is appropriate for the physical network over which the datagram is transmitted.

### Internet Layer

The Internet Protocol `IP` is the most important protocol in this layer.

The release of IP used in the current Internet is IP version 4 `IPv4`, which is defined in RFC 791. `IPv6` is an IP standard that provides greatly expanded addressing capacity. Because `IPv6` uses a completely different address structure, it is not interoperable with `IPv4`.

The Internet Protocol is the heart of TCP/IP. IP provides the basic packet delivery service on which TCP/IP networks are built. All protocols, in the layers above and below IP, use the Internet Protocol to deliver data. All incoming and outgoing TCP/IP data flows through IP, regardless of its final destination.

### Internet Protocol

The Internet Protocol is the building block of the Internet. Its functions include:



This means that it does not exchange control information (called a “handshake”) to establish an end-to-end connection before transmitting data. In contrast, a connectionoriented protocol exchanges control information with the remote system to verify that it is ready to receive data before any data is sent. When the handshaking is successful, the systems are said to have established a connection. The Internet Protocol relies on protocols in other layers to establish the connection if they require connection-oriented service.

`IP` can be relied upon to accurately deliver your data to the connected network, but it doesn’t check whether that data was correctly received. Protocols in other layers of the `TCP/IP` architecture provide this checking when it is required.

 A **packet** is a block of data that carries with it the information necessary to deliver it, similar to a postal letter, which has an address written on its envelope. A packet-switching network uses the addressing information in the packets to switch packets from one physical network to another, moving them toward their final destination. Each packet travels the network independently of any other packet.
 
The datagram is the packet format defined by the Internet Protocol.

The Internet Protocol delivers the datagram by checking the Destination Address in word 5 of the header.

If the Destination Address is the address of a host on the local network, the packet is delivered directly to the destination. If the Destination Address is not on the local network, the packet is passed to a gateway for delivery. Gateways are devices that switch packets between the different physical networks. Deciding which gateway to use is called routing. IP makes the routing decision for each individual packet.

Internet gateways are commonly (and perhaps more accurately) referred to as IP routers because they use Internet Protocol to route packets between networks.

Each type of network has a maximum transmission unit (MTU), which is the largest packet that it can transfer.

## Internet Control Message Protocol

**Internet Control Message Protocol (ICMP)** is part of the Internet Layer and uses the IP datagram delivery facility to send its messages.


## Transport Layer

The two most important protocols in the Transport Layer are Transmission Control Protocol (TCP) and User Datagram Protocol (UDP). TCP provides reliable data delivery service with end-to-end error detec- tion and correction. UDP provides low-overhead, connectionless datagram delivery service. Both protocols deliver data between the Application Layer and the Internet Layer. Applications programmers can choose whichever service is more appropriate for their specific applications.

### User Datagram Protocol (UDP)
The User Datagram Protocol gives application programs direct access to a datagram delivery service. 

Applications that fit a query-response model are also excellent candidates for using UDP. The response can be used as a positive acknowledgment to the query. If a response isn’t received within a certain time period, the application just sends another query.

### Transmission Control Protocol (TCP)

Applications that require the transport protocol to provide reliable data delivery use TCP because it verifies that data is delivered across the network accurately and in the proper sequence.

The unit of data exchanged between cooperating TCP modules is called a **segment**.

If the data segment is received undamaged, the receiver sends a positive acknowledgment back to the sender. If the data segment is damaged, the receiver discards it.

It establishes a logical end-to-end connection between the two communicating hosts. Control information, called a handshake, is exchanged between the two endpoints to establish a dialogue before data is transmitted.

TCP views the data it sends as a continuous stream of bytes, not as independent packets. Therefore, TCP takes care to maintain the sequence in which bytes are sent and received.

TCP is also responsible for delivering data received from IP to the correct applica- tion. The application that the data is bound for is identified by a 16-bit number called the port number. The Source Port and Destination Port are contained in the first word of the segment header.

## The Applcation Layer

The Application Layer includes:

* **Telnet** – The Network Terminal Protocol, which provides remote login over the network.
* **Domain Name System (DNS)** – Also called name service, this application maps IP addresses to the names assigned to network devices.










The broadcast address for network `172.16` is `172.16.255.255`. A datagram sent to this address is delivered to every indi- vidual host on network 172.16. An IP address with all host bits set to `0` identifies the network itself. For example, `10.0.0.0` refers to network `10`, and `172.16.0.0` refers to network `172.16`.

Network addresses with a first byte value greater than 223 cannot be assigned to a physical network, because those addresses are reserved for special use.

Network `0.0.0.0` designates the default route and network `127.0.0.1` is the loopback address. The default route is used to simplify the routing information that IP must handle. The loopback address simplifies network applications by allowing the local host to be addressed in the same manner as a remote host. These addresses are not assigned to devices on real networks.

## Address Structure

An IP address contains a network part and a host part, but the format of these parts is not the same in every IP address.

The number of address bits used to identify the net- work and the number used to identify the host vary according to the prefix length of the address. The prefix length is determined by the address bit mask. 

An address bit mask works like this: if a bit is on in the mask, that equivalent bit in the address is interpreted as a network bit; if a bit in the mask is off, the bit belongs to the host part of the address.

A shorthand notation is available for writing an address with its associated address mask. We can write `172.31.26.32/27`. The format of this notation is address/prefix-length, where prefix-length is the number of bits in the network portion of the address. Without this notation, the address `172.31.26.32` could easily be misinterpreted.

Organizations usually obtain official IP addresses by purchasing a block of addresses from their Internet service provider. The ISP normally assigns a single organization a continuous block of addresses that is appropriate for the needs of the organization.

Internally, however, the organization may have several separate physical networks within the address block. The flexibility of address masks means that service provid- ers can assign arbitrary length blocks of addresses to their customers, and the cus- tomers can subdivide those address blocks using different length masks.

##Subnets

The structure of an IP address can be locally modified by using host address bits as additional network address bits. Essentially, the “dividing line” between network address bits and host address bits is moved, creating additional networks but reduc- ing the maximum number of hosts that can belong to each network. These newly designated network bits define an address block within the larger address block, which is called a **subnet**.

Organizations usually decide to subnet in order to overcome topological or organizational problems. Subnetting allows decentralized management of host addressing.

Subnetting divides a single address block into many unique subnet addresses, so that each physical network can have its own unique address.

On the outside, the address is still interpreted using the address mask known to the outside world.

Because of the dual role of IP addresses, the flexibility of address masks not only makes more addresses available for use, but also has a positive impact on routing.

## CIDR Blocks and Route Aggregation

The use of an address mask instead of the old address classes to determine the destination network is called Classless Inter-Domain Routing (CIDR).

In the TCP/IP protocol suite, addressing is defined by the IP protocol. There- fore, to define a new address structure, the Internet Engineering Task Force (IETF) created a new version of IP called IPv6.
























The most common example of this Network Access Layer function is the translation of IP addresses to Ethernet addresses, performed by the **Address Resolution Protocol (ARP)**.

The ARP software maintains a table of translations between IP addresses and Ethernet addresses. This table is built dynamically.

Answering ARP queries for other computers is called **proxy ARP**. Proxy ARP is used to answer queries for systems that can’t answer for themselves.

ARP tables normally don’t require any attention because they are built automatically by the ARP protocol, which is very stable.

## Protocols, Ports, and Sockets

Once data is routed through the network and delivered to a specific host, it must be delivered to the correct user or process.

As the data moves up or down the TCP/IP layers, a mechanism is needed to deliver it to the correct protocols in each layer. The system must be able to combine data from many applications into a few transport protocols, and from the transport protocols into the Internet Protocol. Combining many sources of data into a single data stream is called **multiplexing**.

Data arriving from the network must be **demultiplexed**: divided for delivery to multiple processes. To accomplish this task, IP uses protocol numbers to identify transport protocols, and the transport protocols use port numbers to identify applications.

The protocol numbers and port numbers are assigned to well-known services by the Internet Assigned Numbers Authority (IANA). Officially assigned numbers are documented at [http://www.iana.org](http://www.iana.org).

### Protocol Numbers

The protocol number is a single byte in the third word of the datagram header.

On a Unix system, the protocol numbers are defined in `/etc/protocols`.

When a datagram arrives and its destination address matches the local IP address, the IP layer knows that the datagram has to be delivered to one of the transport protocols above it. To decide which protocol should receive the datagram, IP looks at the datagram’s protocol number.

### Port Numbers

After IP passes incoming data to the transport protocol, the transport protocol passes the data to the correct application process. Application processes (also called network services) are identified by port numbers, which are 16-bit values.


Ports numbered from 1024 to 49151 are “registered ports.” IANA tries to maintain a registry of services that use these ports, but it does not officially assign port numbers in this range.








It is the *pair of port numbers*, source and destination, that uniquely identifies each network connection.

The combination of an IP address and a port number is called a **socket**.

A **socket** uniquely identifies a single network process within the entire Internet.









Every network interface attached to a TCP/IP network is identified by a unique 32-bit IP address. A name (called a hostname) can be assigned to any device that has an IP address. Names are assigned to devices because, compared to numeric Internet addresses, names are easier to remember and type correctly. Names aren’t required by the network software, but they do make it easier for humans to use the network.

In most cases, hostnames and numeric addresses can be used interchangeably.

A user wishing to telnet to the workstation at IP address `172.16.12.2` can enter:

	$ telnet 172.16.12.2


## The Host Table

The host table is a simple text file that associates IP addresses with hostnames. On most Unix systems, the table is in the file `/etc/hosts`.

In a host table, you can have many names resolving to the same IP address. Much like aliases.

`loghost` is a special hostname used by Solaris in the syslog.conf configuration file. Other commonly used generic hostnames are `lprhost`, `mailhost`, and `dumphost`.

The host address `127.0.0.1` is a special address used to designate the loopback address of the local host—hence the hostname `localhost`.











































### Post Office Protocol (POP)


On an average POP server, the entire contents of the mailbox are moved to the client and either deleted from the server or retained as if never read. Email clients that want to remotely maintain a mailbox on the server are more likely to use IMAP.

### Internet Message Access Protocol (IMAP)

**Internet Message Access Protocol (IMAP)** is an alternative to POP. It provides the same basic service as POP and adds features to support mailbox synchronization, which is the ability to read individual mail messages on a client or directly on the server while keeping the mailboxes on both systems completely up to date. IMAP provides the ability to manipulate individual messages on the client or the server and to have those changes reflected in the mailboxes of both systems.

IMAP uses TCP for reliable, sequenced data delivery. The IMAP port is TCP port 143. Like the POP protocol, IMAP is also a request/response protocol with a small set of commands. The IMAP command set is somewhat more complex than the one used by POP because IMAP does more, yet there are still fewer than 25 IMAP com- mands.









* application (binary data)
* image
* video
* audio
* multipart
* message

The Content-Transfer-Encoding header identifies the type of encoding used on the data.

MIME defines data types that SMTP was not designed to carry.

One response of the `EHLO` command is for the receiving system to return a list of the SMTP extensions it supports. This response allows the sending system to know what extended services can be used, and to avoid those that are not implemented on the remote system. SMTP implementations that support the `EHLO` command are called **Extended SMTP (ESMTP)**.

**ESMTP** and **MIME** are important because they provide a standard way to transfer non-ASCII data through email.

## File and Print Servers

### File Sharing

File sharing is not the same as file transfer; it is not simply the ability to move a file from one system to another. A true file-sharing system does not require you to move files across the network. It allows files to be accessed at the record level so that it is possible for a client to read a record from a file located on a remote server, update that record, and write it back to the server—without moving the entire file from the server to the client.

File sharing is transparent to the user and to the application software running on the user’s system.

Through file sharing, users and programs access files located on remote systems as if they were local files. In a perfect file-sharing environment, the user neither knows nor cares where files are actually stored.

File sharing didn’t exist in the original TCP/IP protocol suite. It was added to support diskless workstations. Several TCP/IP protocols for file sharing have been defined, but two hold the lion’s share of the file sharing market:

1. **NetBIOS/Server Message Block (SMB)**










A **Reverse Address Resolution Protocol** server maps a physical address to an IP address for a client that doesn’t know its own IP address. The client sends out a broadcast using the broadcast services of the physical network. The broadcast packet contains the client’s physical network address and asks if any system on the network knows what IP address is associated with the address. The RARP server responds with a packet that contains the client’s IP address.
The RARP server looks up the IP address that it uses in its response to the client in the `/etc/ethers` file. The `/etc/ethers` file contains the client’s Ethernet address followed by the client’s hostname. E.g.

	2:60:8c:48:84:49	clock
 
To respond to a RARP request, the server must also resolve the hostname found in the `/etc/ethers` file into an IP address. DNS or the hosts file is used for this task.

The following hosts file entries could be used with the ethers file shown above:








1. **Permanent fixed addresses:** The Administrator assigns the address manually without using the DHCP system. While this happens completely outside of DHCP, DHCP makes allowances for it by permitting addresses to be excluded from the range of addresses under the control of the DHCP server.

2. **Manual allocation:** The network administrator keeps complete control over addresses by specifi- cally assigning them to clients in the DHCP configuration. This is exactly the same way that addresses are handled under BOOTP.

3. **Automatic allocation:** The DHCP server permanently assigns an address from a pool of addresses. The administrator is not involved in the details of assigning a client an address.

4. **Dynamic allocation:** The server assigns an address to a DHCP client for a limited period of time. The limited life of the address is called a lease. The client can return the address to the server at any time but must request an extension from the server to retain the address longer than the time permitted. The server automatically reclaims the address after the lease expires if the client has not requested an extension. Dynamic allocation uses the full power of DHCP, whereas the others don't.

Unused addresses are returned to the pool of addresses without relying on users or system administrators to deliberately return them. Addresses are used only when and where they’re needed. Dynamic allocation allows a network to make the maximum use of a limited set of addresses.




