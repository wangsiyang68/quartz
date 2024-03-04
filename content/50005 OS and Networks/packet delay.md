# Packet Delay
---
![transmission and propagation difference](images/packet_delay.png)
Above is a picture of the delay encountered by packets when they are sent through routers. However, this is just one router. Packet may travel through many routers. Total delay is **summation** of nodal delays

## Processing delay ($d_{proc}$):
- Check for bit errors (by using the checksum in the packet header)
- Typically less than a milisecond

## Queueing delay ($d_{queue}$)
- waiting time for packet to get to the front of the queue for the ouptut
- depends on congestion level of router (as a result, the amount of waiting time is **most random** as compared to other delays)
- More details on queueing delay [[#Further discussion into Queueing Delay|below]]:

## Transmission delay ($d_{trans}$)
- Time taken to push whole packet from router to the **beginning** of the link
	- how fast can the router push the bit out (analogous to how fast the toll booth can process your car before sending it onto the highway)
- L/R, where L = packet length (bits) and R = link bandwidth (bps)
- limited by the rate of data transfer (e.g. megabit/gigabit ethernet)

## Propagation delay ($d_{prop}$) 
- time for packet to move from beginning to **end** of the link
- d/s where d = length of physical link and s = propagation speed in medium (usually set as 2/3 the speed of light in vacuum)
- Limited by the speed of light

**NOTE** transmission and propagation delay are different from each other 


## Further discussion into Queueing Delay
utilisation can range from 0 to 100%
Usually measured by comparing the average queueing delay against the traffic intensity (utilization)

if traffic intensity > 1, means handling more work than you can ever finish, therefore, average delay will be infinite

However, due to the exponential feature of the graph, as utilization nears 1, will be infinite queuing delay as well. Therefore, we should not be greedy and trying to use every bit of the link capacity (diminishing returns for increasing traffic intensity)
- A good utilization is roughly around **70%**

![queue delay](images/queue_delay.png)

#networks 