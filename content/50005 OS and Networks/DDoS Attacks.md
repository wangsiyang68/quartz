# DDoS Attack
---
Method 1: Bombard root servers with traffic
- Idea: affect everyone
	- However, not successful to date:
		- Many computers serving up 1 server
		- Traffic FIltering (firewall)
		- Local DNS servers cache IPs of TLD servers, allowing server bypass

Method 2: Send queries with spoofed source address: target IP
#todo how does it work?
- Solution: run DNS over TCP despite the high cost
- Require amplification???????????

Method 3: Redirect attack
- Idea intercept the query and send bogus replies to DNS server, which caches my malicious IP address as the translation for the address
- Also known as DNS poisoning
- A prominent example is to block undesired websites by government
	- Redirect: press casino.io, but imda redirect me to a page
	- Drop packet: refuse the translation from url to ip address
	- Ban the IP address: check each IP address of the packet whether 8.8.8.8 (google's url) is there
		- However, high cost so most likely just sample a few packets then drop them = still results in bad experience of traversing websites
	

#networks 