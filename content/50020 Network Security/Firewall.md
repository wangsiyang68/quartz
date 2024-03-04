Requirements of the firewall:
- All the traffic between trust zones should pass through firewall.
- Only authorized traffic, as defined by the security policy, should be allowed to pass through.
- The firewall itself must be immune to penetration, which implies using a hardened system with secured Operating Systems.

Terminology
- Actions to take:
	- Accept, Denied, Rejected (DROP and tell source)
- Ingress (Inspect incoming traffic), Egress (Inspect outcoming traffic)

Types of filters
- Packet Filter
	- Easiest/Most efficient
	- But cannot tell the whole story
- Stateful
	- Can allow more fine grained control
	- Need to store data about packets in storage
- Application/Proxy
	- Like Man in the Middle
	- Proxy can inspect data all the way up to the application level
	- Observe whats happening to proxy before proceeding with the connection

## Netfilter
- provide hooks for user to insert rules into the kernel code 
- Needed because firewall code is written in the kernel as it looks at kernel level information in the packets (anything below application level)
- Netfilter provides a way to organize the code nicely so that it is not saved all over the place in the computer
- Is a linux application

Different hooks deal with different types of packets, usually with forwarded packets or packets meant for the machine, as well as the outgoing or incoming packets

## Iptable
- Based on netfilter, make it more user friendly by allowing the user to implement rules from a single cli command
- Kernel part: Xtables
	- Xtables extends the functionality of the iptable tool by providing modules for handling specific types of packets and protocols.
		- Some other extensions: owner (to check the packet based on the owner name), conntrack (to help set up a stateful firewall)

There are **TABLES** and **CHAINS**
- Tables are like the actions to take
	- Top 3 tables include: filter, nat (src/dst address modification), mangle (packet content modification)
- Chain is like where you want to apply the action
	- Each chain corresponds to a netfilter hook