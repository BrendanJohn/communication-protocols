CSCI S-40 Communication Protocols and Internet Architectures
Homework 3
Brendan Murphy

	•	(1) Host A's application passes its data off to the layer-4 UDP module where it is encapsulated and a UDP header is added. In the UDP header there are four fields - a protocol port indicating where the message came from, protocol port indicating where the message is to be sent, message length, and a UDP checksum.

(2) Data is passed to IP layer from the UDP. This data is then encapsulated into the form of an IP message called an IP datagram. This datagram has two parts, a header and a payload. The header contains addressing and control fields like a source address and a destination address, and various control settings like Time to Live (TTL) and a header checksum to guard against transmission corruption. The payload contains the actual data of the message.

(3) The IP layer looks at the header of the datagram and sees that the destination IP address is on the same network it is on and determines that the datagram can be delivered directly. It knows they are both on the same network because both start with a 10.0.0.0 IP address. The IP layer now needs a MAC address to build the Ethernet frame, to get this it passes the destination IP address down into the Address Resolution Protocol (ARP) to dynamically bind the IP address to the matching MAC address.

(4) The ARP module lets a host find the physical address of a destination host on the same network using only the target`s IP address. First it checks its cache for any recent MAC addresses and finds none because this is the first data sent from host A to host B. Next, Host A broadcasts an ARP request packet to host B and asks it to reply with its MAC address.

(5) In the physical layer, the request is carried out containing the target machine`s IP address. All the hosts on the network receive the ARP request, but only host B responds with an ARP reply that is unicast and contains host B`s IP address and hardware address of MAC_B.

(6) The ARP module notes the hardware address of host B and includes it in its cache. It then passes the address to the requesting IP layer.

(7) The IP module passes the datagram to the Ethernet module where it is repackaged into an Ethernet frame including a header and trailer. The header will contain properties including the source address and destination address that was just acquired from the ARP module.

(8) The Ethernet frame is now ready to ship. It is placed on the network and picked up by host B's Ethernet interface.



	•	(B) (1) Host A's application passes its data off to the layer-4 UDP module where it is encapsulated and a UDP header is added. In the UDP header there are four fields - a protocol port indicating where the message came from, protocol port indicating where the message is to be sent, message length, and a UDP checksum.

(2) Data is passed to IP layer from the UDP. This data is then encapsulated into the form of an IP message called an IP datagram. This datagram has two parts, a header and a payload. The header contains addressing and control fields like a source address and a destination address, and various control settings like Time to Live (TTL) and a header checksum to guard against transmission corruption. The payload contains the actual data of the message.

(3) The IP layer looks at the header of the datagram and sees that the destination IP address is not on the same network it is on and determines that the datagram must first be passed to the router on the network. In order to target the router, it must find its MAC address using the ARP module. The router's IP address is sent to the ARP module in search of its matching MAC address.

(4) The ARP module lets a host find the physical address of a destination host on the same network using only the target`s IP address. First it checks its cache for any recent MAC addresses and finds none because this is the first data sent from host A to Router R. Next, Host A broadcasts an ARP request packet to Router R and asks it to reply with its MAC address.

(5) In the physical layer, the request is carried out containing the target's IP address. All of the hosts on the network receive the ARP request, but only router R responds with an ARP reply that is unicast and contains router R`s IP address and hardware address of MAC_R1.

(6) The ARP module notes the hardware address of router R and includes it in its cache. It then passes the address to the requesting IP layer.

(7) The IP module passes the datagram to the Ethernet module where it is repackaged into an Ethernet frame including a header and trailer. The header will contain properties including the source address and destination address that was just acquired from the ARP module.

(8) The Ethernet frame is now ready to ship. It is placed on the network and picked up by router R.

(9) Router R receives the Ethernet frame and looks at its destination address. It sees that the destination is on the same network as it is one and determines that it must acquire a more concrete destination MAC address using the ARP module so that it can correctly build the Ethernet frame.

(10) The ARP module lets a host find the physical address of a destination host on the same network using only the target`s IP address. First it checks its cache for any recent MAC addresses and finds none because this is the first data sent from router R to host D. Next, router R broadcasts an ARP request packet to host D and asks it to reply with its MAC address.

(11) In the physical layer, the request is carried out containing the target machine`s IP address. All the hosts on the network receive the ARP request, but only host D responds with an ARP reply that is unicast and contains host D`s IP address and hardware address of MAC_D.

(12) The ARP module notes the hardware address of host D and includes it in its cache. It then passes the address to the requesting IP layer.

(13) The IP module passes the datagram to the Ethernet module where it is repackaged into an Ethernet frame including a header and trailer. The header will contain properties including the source address and destination address that was just acquired from the ARP module.

(14) The Ethernet frame is now ready to ship. It is placed on the network and picked up by host D's Ethernet interface.

	•	A tuple, or ordered set of values is can be used as a networking term. The 5-tuple references the five fields necessary to identify a TCP connection. These fields are: payload type, source port, destination port, destination IP address and source IP address.

A user working on a laptop has both an email connection and a web connection open simultaneously, by opening a command prompt and typing netstat the user will see a printout of all active network connections. The user would see the following on the laptop:
Proto
Local Address
Foreign Address
State
TCP
128.103.104.105
18.19.20.21
Established
TCP
128.103.104.105
18.19.20.21
Established





And the same command run on the server would output a table like this:
Proto
Local Address
Foreign Address
State
TCP
18.19.20.21
128.103.104.105
Established
TCP
18.19.20.21
128.103.104.105
Established






	•	a) Distance vector protocols employ the distance and direction of a routing protocol to find the path to its destination. Some common column headers that may exist in a router using the RIPv2 protocol are: port, next hop IP address (which determines the next router that the packet will visit on its journey to its final destination), metric, destination network and mask.

b) For a large private enterprise network I would choose the OSPF (Open Shortest Path Protocol) protocol because of the advantages it has over the RIPv2 protocol. Firstly, when using the OSPF protocol there are no limitations on hop count. This improves speed and performance on the network. Secondly, OSPF uses IP multicast to send link-state updates this ensure less processing on the routers on the network. Lastly, OSPF has better load balancing than RIPv2.


	•	The UDP checksum pseudo header contains the source IP address, destination IP address, protocol number and UDP length. The checksum is computed using the IP address information, which presents a problem because this is in violation of the layered protocol rules, however it is necessary indicate that the UDP datagram has in fact been delivered.

	•	TCP includes functionality for both flow control and congestion control. Flow control is important because it prevents a sender from overloading a receiver with too many packets that it is unable to absorb. Congestion control is more in line with preventing a node from over whelming the network with packets. Both of these concepts are necessary to maintain an active network that is not saturated with too many packets.

	•	a) Network Address and Port Translation (NAPT) is a way to remap one IP address to another via modifying the network address information in the IP header contained within packets on their journey to their destination. A NAPT box contains a translation table with information such as an internal IP address, internal port number, destination IP address, destination port number, a translated source port, and a protocol type. The NAT box essentially takes the datagram and stores information about it in the table, then updates the header to make it appear that the source IP address is the NAT box itself.
b) Some limitations that may arise from my implementation are firstly some basic connectivity issues. NAT provides a basic IPv4 connections but fails to integrate with more advanced features that are now possible such as built-in security, larger address space, and more support for Quality of Service(QOS). A more pressing issue however is the loss of significance of the source IP address and port number. Basically, the destination device does not know the true origin of the incoming packets, which presents a serious security flaw in this configuration.

	•	a) In order to support IPv6 all of the devices on the network need to be capable of supporting IPv6. However, IPv6 devices are assembled using a new process called dual stack that allows IPv6 and IPv4 to run alongside each other simultaneously. Its mainly a software and firmware issue and less of a hardware issue to support IPv6. The biggest software one needs to install is the modem firmware upgrade for DOCSIS 3.0 which is the IPV6 specification for cable modems. With this in place, and an ISP that supports IPv6, your existing IPv4 configuration should be able to support Internet Protocol Version 6.
b) According to the results from www.testipV6.com my network at work does not support IPv6.
These were the results of my test:
	•	Your IPv4 address on the public Internet appears to be 143.115.159.57
	•	Your Internet Service Provider (ISP) appears to be Liberty Mutual Group 
	•	No IPv6 address detected [more info]
	•	You appear to be able to browse the IPv4 Internet only. 
	•	You will not be able to reach IPv6-only sites. To ensure the best Internet performance and connectivity, ask your ISP about native IPv6. [more info]
	•	Your DNS server (possibly run by your ISP) appears to have no access to the IPv6 Internet, or is not configured to use it. This may in the future restrict your ability to reach IPv6-only sites.
