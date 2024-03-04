# nslookup command
---
``` shell
Davids-MacBook-Pro-2:~ david_yau$ nslookup www.csail.mit.edu

Server: 202.65.247.31
Address: 202.65.247.31#53

Non-authoritative answer:
www.csail.mit.edu canonical name = live-csail.pantheonsite.io. 

live-csail.pantheonsite.io canonical name = fe3.edge.pantheon.io. 

Name: fe3.edge.pantheon.io
Address: 23.185.0.3
```

Things to note:
- #53 refers to the socket number. this number is reserved for DNS sockets
- DNS Server is at 202.65.247.31
- Non-authoritative answer means that the IP address was fetched from the cache
- Web address and IP address is 
	- Name: fe3.edge.pantheon.io
	- Address: 23.185.0.3

#networks 