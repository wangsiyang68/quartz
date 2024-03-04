network packet encapsulation is dependent on?

Internet layers

- Mac address are physical and exists on level 2 (link)
- IP address lives in the network level (level 3)
- routers have a mac table that exists at the network level (?) to check where to send the packet next if necessary
- Port numbers live on the transport layer

arp poisoning is done with ******************************gratuitous arp replies******************************

broadcast storm by creating a logic/cable loop > results in network DOS?

## ARP characteristics
- Since ARP is on the link layer,
	- ARP cache poisoning attack must be done on the local network!
	- Cannot be carried out via remote

## Promiscuous Mode
- network interface cards by default only copy packets that match its MAC address to a buffer in the kernel
- However, when in promiscuous mode, NIC can pass every frame received from the network into the kernel
- Therefore you need sudo permission to read all the packets

## Raw sockets in C
- offer more flexibility in the packets received (can see what is the header and modify it)

### Exercise 1
![[Pasted image 20230925072435.png]]
- Problem
	- not found because no such name with a NIC
- Solution
	- use ipconfig to find the name related to the NIC

### Exercise 2
![[Pasted image 20230925072508.png]]
- Solution:
	- we have specified it to be not promiscuous mode (setting it to 0 in argument)

About decoding the frames received

- Need to be careful about header length and accessing it correctly so that the subsequent decoding of the message doesnt mess up

#netsec

#netsec 