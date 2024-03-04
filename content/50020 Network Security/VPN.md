Two ways to do IP tunnelling:
1. IP Layer
2. Transport Layer
## IP Layer
- IPSec Tunnelling (At the IP layer)
	- Put IP packet as the payload of a new IP packet
	- New IP packet header is now the IPsec header
	- Done entirely in the kernel
		- Not desirable as it is cumbersome and dangerous to modify the kernel
	- Data Encryption (**ESP**), Authentication (**AH**), Key Exchange (**IKE**)
	- Authentication Header
		- Zero out the mutable fields
		- Has a SecParamIndex which indicates the mode of encryption?
		- Seq# has defence against replay attack
			- Have a sliding window of acceptance
			- If it is outside of the said bounds (too early, reject)
			- If it is outside of said bounds by too much, verify if it is FR (how tho)
			- Dont want the sliding window to be too small, will likely miss alot of packets
			- Receiver only will set the size of the window! not the sender
		- Create Security Association in IKE the same as the Shared Secret ?
		- IKE Phase 1: Creating the Shared Secret
		- IKE Phase 2: PFS or no PFS?
			- Forward Secrecy only: crack a session key, then the rest of the subsequent key is broken
				- Keys for IPSec SA is derived from IKE shared secret
			- PFS: If one key is broken then the previous and future are not broken
				- This will require new nonce values and new DH key exchange
## TLS/SSL Tunneling
- Make the whole IP packet into the payload of a new TCP packet
- Attach a new IP header (destination is vpn server, source is my machine)
- Setting up Routing tables so that you know where to route packets to
	- Selected networks (e.g. 10.0.8.0/24) should be routed to the TUN virtual interface

#netsec 