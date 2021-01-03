CSCI S-40 Communication Protocols and Internet Architectures
Homework 1
Brendan Murphy

	•	A cyclists carries 3 USBs containing a total of 192 gigabytes. In terms of digital storage, 1 gigabyte equals 8000 megabits. Therefore the cyclist is carrying 1,536,000 megabits through traffic at a rate of 20 kilometers per hour. Given this calculation, it takes 10,240 seconds to transmit the same amount of data over a communications line that operates at 150 megabits per second. 
 
This is calculated as follows: 1,536,000 Mb/150 megabits per second  =  10,240 seconds (170.7 minutes roughly)
 
In 10,240 seconds, the courier can ride a distance of approximately 56.83 kilometers.  This is calculated as follows: 20 km per hour = .00555 km per second .00555 km per second  x  10,240 seconds =  56.83 kilometers. Therefore, for a distance of up to 56.83 kilometers, the cyclist carries the data faster.  After that distance has lapsed, the courier is still carrying (transmitting) the same amount of data, but the communications line has now transmitted more data.



	•	I am viewing a web page on the course website from a computer located on the fourth floor of an office building in downtown Boston. The page loads painfully slow at my current download rate of 24.13 Mbps, which is just north of the United States average. I am viewing the page using a browser called Google Chrome, which is accessing the page through the HTTP protocol, an application-level protocol. The application layer then communicates with the internet protocol using the transmission control protocol, which is a transport layer protocol. Next, the network layer takes messages received from the transport layer and places them into a payload with a header. The data link layer takes the payload with the header and packages it up with its own header in a process called encapsulation, and then passes the payload to the physical layer.

 The router must then take this message and determine where to send it. It looks at the destination IP address and sees that it is a server located on Harvard’s campus. The packet is sent through a series of routers until it reaches the Harvard network, where it can access the server. When the packet reaches the final router in the path, it creates an ethernet frame and places it onto the local area network. The frames are converted to 1s and 0s and sent across the network. The encapsulation process takes place again, but in reverse order in a process called de-encapsulation. The messages are received (hopefully) in this process thanks to the network topology between my computer and the server at Harvard.


	•	Join 3 IETF mailing lists: 
	•	HTTP-use;
	•	 101-Newcomers
	•	 Proxies

	•	Whenever sequenced data is sent into a network, it does not necessarily get received in the same order that it was sent in. The sliding window protocol receives data out of order and rearranges that data, and when the beginning of the data arrives the window slides to the next position to receive more data. A well-tuned sliding window protocol improves overall network flow by ensuring that the network is completely saturated with packets at all times, because the sender is able to send multiple packets without waiting for an acknowledgement.

Sliding window with a window size of 3:


send data 1
send data 2
send data 3	receive data 1 send ack 1
	receive data 2 send ack 2
	receive data 3 send ack 3

receive ack 1
receive ack 2
receive ack 3

















Error control is needed for both data transmission errors and procedural errors. The sliding window protocol can handle errors efficiently by sending error indications back to the sender and requesting it retransmission of the lost packet.


Sliding window with a window size of 3 handling error:

send data 1
send data 2
send data 3
                                                                                                                        receive data 1 send ack 1
                                                                                                                          
                                                                                                                        data 2 not received
                                                                                                                     
                                                                                                                         receive data 3 send ack 3
                                                                                                                         requests resend data    



receive resend 
request

resend data 2
                                                                                                                        

                                                                                                                         receive data 2 send ack 2
















	•	The computer in my home is connected to the internet via an Ethernet cable connected to a cable modem. Modem is a shortened way of saying 'modulates and demodulates' as this is the primary purpose of the device when handling data signals. Data coming from the network to the user is called downstream, conversely data from the user to the network is called upstream. These channels are separated using Frequency Division Multiplexing (FDM). FDM is a technique used to split the total bandwidth of a communication bandwidth into non-overlapping bands. For example, the coaxial cable used to bring TV and internet into my home has a bandwidth of about 1000 MHz, but the pass band of each television channel is only 6 MHz resulting in a tremendous amount of free space for additional channels and data.

To transmit data over the cable network, my computer takes advantage of a transmission method called Time-Division Multiplexing (TDM). In this case my modem transmits a packet to the head-end and requests space to transmit. Precise scheduling of packet transmission is necessary to get high utilization and good power control to avoid any system failures. TDM is a form of multiplexing that dates back to the late 19th century where its original intention was telegraphy systems, however its primary use today is in telephony systems.

In contrast to a coaxial cable network, a DSL network or Digital Subscriber Line (originally called a digital subscriber loop) is used to transmit internet services through traditional phone lines. It was originally thought to be impossible to transmit data through twisted pair telephone cables, however, this was proved possible thanks to a phone line in the United Kingdom that was able to support the transmission of 4 MHz of data between a BBC broadcast station and a transmission station ten miles away. Although DSL is a less popular means of internet service in 2018, 90% of the United States can access DSL thanks to the impressive phone line infrastructure that has been in place since the growth of AT&T and other massive telephone conglomerates.

	•	Answers to question 6 below
	•	A Virtual Circuit or VC is used to describe the connection between a host and a packet switching network. The connections appears to be physical and discreet, however is actually a shared pool of circuit resources used to support multiple users.
	•	The difference between connection-oriented communication and connectionless communication is the in a connectionless communication two devices can talk to each without any kind of security handshake. This is beneficial for devices like walkie talkies and fm radio. The downside is that because no security is in place like in a connection-oriented network its makes it possible to have data stolen because there is no security protocols between the devices on the network.
