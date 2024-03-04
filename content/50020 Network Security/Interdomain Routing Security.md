## BGP Protocol introduction
Main Purpose of BGP protocol is to disseminate AS routing information to the whole world 
- Border Gateway Protocol
- Running on top of TCP, in the application layer
- In contrast, Interior Gateway Protocol
	- IP protocol in the network layer
- Shortest path not the main concern
	- Cost of the path is the main concern
		- Some **autonomous systems** (AS) work together, others are in competition
- Goals
	- Secure message exchange between **neighbours**, the regular CIA stuff
- BGP Speakers are repeatedly disseminating information of what networks are they able to reach
	- BGP Update
		- Advertise Prefix
		- Receiving AS will also send the information to the next links
			- Information is selected based on some criteria so that the best route is saved
			- Do not inform AS neighbours after you in the path of the path since they know a shorter path
	- BGP Withdraw
		- Another type of message to send, to inform neighbours that you cannot reach that AS
- Internal BGP
	- Needed for big AS with multiple BGP speakers
	- Synchronize for each other
- IGP
	- To inform internal routers of the routing information from the BGP speakers
	- There are two different standards
		- OSPF
		- Routing information Protocol (RIP)

## Path Selection Algorithm
- Can consider other criteria, e.g.: local preference weight
	- Useful in cases to avoid data from coming through backups (lower bandwidth, lower speed)
	- Achieve the same effect by artificially lengthen the path by appending same AS number
Internet consist of many autonomous systems. AS could have many networks
- What is the different between the two?

BGP overlapping specific rule 
- Also known as de-aggregation
- Load balancing
- allows a client to reach a closer network, but if cannot reach, can still go the headquarters
	- **What if i request for a specific network address that matches that of the further away network?**

IP Anycast
- Allow multiple machines to have the same IP address
**- Is stateless, what does it mean and what are the consequences?**
	- is it because the signposts can change at anytime?

## Autonomous Systems
AS types 
- Stub 
	- One single ISP
- Multihomed
	- Connected to multiple AS
	- Can connect to internet via these AS
- Transit
	- Can connect to many different ASes
	- Stub and Multihome dont allow packets to flow through one AS to another (Transit service)

Peering
- Connecting to neighbouring AS via a BGP speaker
- Privately at Data Centers
- Publicly at Internet Exchange Point/Providers

## BGP Security Vulnerabilities
- Confidentiality
	- Eavesdropping the messages on the BGP sessions by tapping on the links between neighbours
	- Can infer business relationship
	- But it is difficult cuz
		- Sometimes one physical link only
		- Sometimes run over IPSec (encrypted)
- Integrity
	- Tampering with the message (insert, delete, modify, replay messages)
	- Delete: neighbour doesnt learn new route
	- Modify/Insert: neighbour learn bogus route
		- Remove: Imagine a route 701 > 3715 > 88. Remove 3715. Can make the AS path look shorter since 88 looks closer to internet core. Difficult to tell 
		- Insert: Imagine a route 701 > 88. 
			- Insert 3715 in between. When 3715 AS sending packets to 88, it will realize that recommended route is an infinite loop, and refuse to use that loop. Now we have DOS attack
			- Insert 3715 at the end. Now can do MITM without being caught by the filtering approach. **How?**
	- Missing/Inconsistent route
		- Resulting a "cold potato" situation, where the packets stay unnecessarily long inside an AS
	- But is difficult
		- Because you need to be at the right place
- Performance
	- Denial of service
		- Overload link between the routers by sending lots of data packets
			- Easy to do 
			- But also easy to defend
		- Send bogus TCP packets (since BGP is run on top of TCP)
			- Send FIN/RST to close the session or conduct SYN flooding
			- Use the same methods to defend against them. Otherwise,
				- Can conduct filtering to block packets from unexpected neighbours
				- **Exploit the IP TTL Field as an effective filter**
					- Because BGP speakers are usually one hop apart
					- Third party hard to spoof packet remotely, need to be one hop away

## Fundamental Issue: Origin Authentication
- Problem: Prefixes claims are not actually verified, i.e. who is the actual owner is not checked.
	- Those AS that are closer to the AS with bogus claim will be redirected to the AS with bogus claim
- Consequences
	- Blackhole: Denial of service
	- Snooping: Traffic can be analysed by someone else
	- Impersonation: Traffic sent to bogus places
- To solve: but it is hard to debug
	- Hard to detect in the first place
		- Real origin AS does not detect the problem
		- Victim may not have loss of connectivity, just performance degradation
- Problem #2: Sub-Prefix Hijacking
	- Claim a subset of a Class A/B/C address
	- Everyone will now redirect to bogus AS due to longest prefix matching rule
		- Where traffic should be redirected to the AS with the longest matching prefix 
		- Example: Pakistan Youtube fake broadcasting message
			- Youtube originally announcing /22 route
			- Pakistan announces /24 route, its more specific
			- Youtube starts to announce more specific /25 routes (subsets) so that it can win the fake broadcasting message attack (it was /24)
	- Method to Hack:
		- Hijacking AS need to have router with eBGP session(s)
- Problem #3: Spamming
	- Form a bidirectional TCP connection to a mail server
	- Send spam email
	- Get revenue from clicks
	- To do:
		- Dont use the real IP address
		- Hijack unused unallocated address block in BGP
			- What does it mean to hijack? Is it the same as before, to bogusly claim that you are the network block?

## Improving BGP security
-  Address attestations
	- Claim the right to originate a prefix
	- Checked through delegation chain like ICANN
- Route attestations
- S-BGP can validate ... **what**?
- Incrementally Deployable schemes?
## Data Plane attacks
- Control Plane
	- **What is this?**
- Data Plane
	- Data should be sent along the routes as defined by the Control plane
	- However, there is nothing guaranteeing this
	- Attack: Drop packets in the data plane. Can choose to do so selectively also, so that it is harder to detect
- Adversary needs to control a router along the path, so that the traffic flows through the attacker too

## Difficulty in upgrading BGP
BGP to S-BGP kinda hard because of
- Complete, accurate registries
	- E.g., of prefix ownership
- Public Key Infrastructure
	- To know the public key for any given AS
- Cryptographic operations
	- E.g., digital signatures on BGP messages
- Need to perform operations quickly
	-  To avoid delaying response to routing changes
- Difficulty of incremental deployment
	- Hard to have a “flag day” to deploy S-BGP

BGP is huge and complex bro
