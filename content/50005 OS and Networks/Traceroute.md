# Traceroute
---
## Real life
---
`traceroute` program will provide delay measurement from source to route
- Done using IP header information, which contains `TTL` (time to live) information, which prevents an infinite loop by specifying how long should a packet be available on the internet (i.e. how many hops?) 
	- Why need prevent this loop? This is to prevent ghost packets from existing in the network
- When TTL == 0, then the packet will be dropped, then "ICMP TTL exceed" message sent back local host. 
- Everytime router receives a packet, decrement by 1
- If packet is dropped, then will notify receipient/sender?
	- via ICMP (Internet Control Message Protocol)
	- Send shenme details? #todo
	- RTTi = Round Trip time

- Traceroute does a while loop
	- With increasing TTL value
- sent to an unused port
 
## Applications
- usually the first router receiving packet is a **gateway**/your own router
- The third value is usually an upper bound on the actual value
#networks 