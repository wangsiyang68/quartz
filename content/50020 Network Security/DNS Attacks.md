## [[DNS]] refresher
- Note that iterative starts at the root server and then local dns server will work its way down to more specific servers
	- Put burden on the local dns server
- For recursive, the root server is responsible for returning the result
	- Put burden on the servers near the root of the tree
- dig
	- if the DNS server is not specified, it will look at the local DNS server

## Attacks
- DoS
	- overwhelm servers so that the server cannnot respond to legit requests
- Spoofing (Attacking the correctness of the DNS server)
	- Provide fraudulent IP address to victims, tricking them to communicate with a machine that is different from their intention
		-  IF HAVE root privileges on victim
			- use malicious dns server as machine local dns server
			- add fake records
		- IF NOT, but am on the LAN
			- can try to spoof a reply before the actual response comes back
			- Actual (late) response will be discarded
			- Need to flush the local cache in the network before attacking, so that you have a chance to impersonate the local cache
		- IF REMOTE
			- cannot access the transaction ID either
				- transaction ID links the query to answer, need to be same for machine to accept response
			- Need to guess the **SOURCE PORT NUMBER** and **TRANSACTION ID**
				- i.e. when targeting the local dns server, query a URL to it that it doesn't know. Spoof the reply, but need to guess where is local dns is receiving the reply, and guess the transaction ID to place a fake entry in the local dns server
				- ALSO note that while guessing by brute force, you are racing against the actual reply (cache effect)
					- TO COUNTER CACHE EFFECT: KAMINSKY 
						- Idea: use a fake address to eventually impersonate the dns server returning the answer -> Re-binding
						- Fake address will force the local dns server to keep asking the outside DNS server 
						- Need to keep asking another fake address
KEY:
How is the DNS packet constructed?


What can you do as a malicious DNS Server replying to clients?
- You can fake data in the other sections
	- If additional data has data about a domain that is out of zone, then that will not be believed by the DNS server
	- Further domain names can be accepted as answers in the Authority section
		- However, additional data about that further given domain name will be cached but not used
		- further domain names will not be accepted as extra entries in Authority section

**REVERSE DNS LOOKUPS**
- HOW DOES IT WORK?
	- Will reverse the IP address first, then append the root server that is given in the query
- ATTACKS
	- Context: want to restrict access based on IP address?
	- If attacker sends a reverse dns lookup, the server will eventually reach back to your server
	- Attacker can now reply with whatever they want

**SOLUTION**
use DNSSEC
- Extension to DNS
- All answers from DNSSEC protected zones are digitally signed
- Builds chain of trust using dns zone hierarchy 

TLS/SSL Solution
- Private-Public key to defeat DNS cache poisoning attacks
- Encrypt data transmitted so that it is secure

**OTHER ATTACKS**
DNS Rebinding attack
First step: Get the client to accept malicious code by visiting attacker website
Second step: Spoof the IP address of your domain url into an IP address that is within the local network, because the server for the local network usually only trust code that originated within the same network
- The victim will usually ask for the IP address of the url again because you have set the ttl for that domain to be supershort
Goal: Get malicious code in the victim machine to be trusted by the target server in the same network

#netsec
