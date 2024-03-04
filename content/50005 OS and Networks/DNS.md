# DNS
---
An application layer protocol
- At this level so that the complexity is at network's edge 
- highly decentralized
	- Advantages: avoid centralized problems; e.g. single point of failure, traffic volume (single server becomes a bottlenecc), distant centralized database, maintenance

DNS provides multiple services
1. hostname to IP address translation
2. host aliasing
3. mail server aliasing
4. load distribution/load balancing
	- replicated web servers: many IP addresses correspond to one name
	- One of the technique to load balance is known is Round-Robin DNS, as described below:
		- If there are five IP addresses in round-robin DNS, a DNS query would only return IP address #1 for every sixth request. Because each IP address corresponds to a different server, this setup reduces each server's workload, making it less likely to become overwhelmed by requests.

## Structure
![images/dns](images/dns.png)
Highest level: Root DNS servers
Next highest level: Top Level Domain (TLD) servers
Third highest level: Authoritative DNS servers (belongs to each organization)
	- Provides authoritative hostname to ip mappings for organizations named hosts
	- But can also be maintained by organization or service provider (i.e. outsource)
...and so on

Decentralization occurs because each sub layer is responsible for its set of IP addresses:
- Root responsible for .com, .org, .edu, etc (TLD)
- Each TLD responsible for each subsection (e.g. .com responsible for yahoo.com, amazon.com)
- Each subsection responsible for its own set of IP addresses (e.g. amazon.com DNS server responsible for IP addr for `www.amazon.com`)

There exists an **optional** but often used layer: the Local DNS Name server
- Hence it does not strictly belong to hierarchy
- each ISP (residential ISP, company, university) can have one
- when host makes DNS query, query is sent to its local DNS server
	- It has a local [[DNS caching|cache]] of recent name to addr translation pair (which may be out of date)
		- Makes user DNS name resolution more efficient, since person A searching for xyz address will help person B get that pairing faster with the presence of the cache (i.e. dont need everyone to individually search for xyz addr individually)
	- So the Local DNS name server acts as a proxy

## Name Resolution
Two types of [[query]]: iterative and recursive
1. Iterated: local dns server repeatedly goes down the DNS hierarchy until it receives the IP address it needs
	- Consider the overhead saved if you have a local DNS server, the RTT required for local DNS server to get the IP address
2. Recursive:
	- Amount of RTT waited is the same for local DNS server, but workload distribution changed
		- Puts burden of name resolution on contacted name server
		- As a result, creates heavy load at upper levels of hierarchy
			- upper levels now responsible for returning the actual IP address

Some common tools: [[nslookup]], [[dig]]


## Reflections
DNS = behaves like a virtual memory that has certain design principles that are desirable
- Late binding: runtime (defer the translation until IP translation is needed)
- Allow many to one mappings
- Allow one to many mappings
 #networks 