# Internet
---
The internet is a inter-connection of many networks

Components:
- End Systems (hosts) 
	- A computing device to run stuff (e.g. PC, server, wireless laptop, smartphone)
	- They are on the edge of the graph
- Communication Links
	- Like the edges of the graph
	- Can be made of fiber, copper, radio, satellite
	- Transmission rate: bandwidth (like width of the "data" highway)
- Routers
	- like computers, but their purpose is to connect hosts to destinations (servers)
	- Store and foward: routers wait for all bits in a packet to arrive before sending it out. This is why [[Packet Delay]] is additive.

One of the most popular APIs: socket API

## Packet
It is made up of the **header** (control information, i.e. parity byte/checksum), and **payload** (where data is being stored uninterrupted). The payload is uninterpreted by routers/midpoints
#networks