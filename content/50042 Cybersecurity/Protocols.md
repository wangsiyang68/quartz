# Protocols
---
Context: How to attempt passive eavesdropping IRL?

Things that can read traffic:
- WiFi access point
- Your ISP
- Other ISPs that forward your traffic (core routers)
- Infrastructure on the receiver side

How to protect: use TLS protocol for sending data

Recap of [[layering#Layering diagram|TCP/IP model]]:
- At the second layer, the Dest MAC addr is referring to the MAC addr of the gateway (e.g. router)
- When up and about sending the packet, will hop on the third layer by looking at the IP address

## ARP Spoofing attacks
ARP spoofing attack: (i.e. update Alice and Bob cache with MiTM MAC addrs)
1. Router need to send packet to IP address xx.xx.xx.xx
2. Router asks: yo who has IP address xx.xx.xx.xx, what is ur MAC address?
3. Any machine can reply, Hi, I have IP address xx.xx.xx.xx, MAC address is as follows: xxxxxxxxxxxx
4. Router saves the IP address information, and sends packet to MAC address xxxxxxxxx

Problem: Step 4 is too naive
- However, note that ARP spoofing is only for within hosts in the same local area network
	- To spoof out of the LAN, can spoof again one more time that you are the receiving router for another LAN #todo what does this exactly mean? how to do?

Solution : TLS security scheme
	- TLS starts with a handshake, in which capabilites are exc
	- Operation modes in TLS
		  - RSA, DHKE, ephermeral DHKE (short lived), Elliptic curve DH and ephermal ECDH
	- Encryption modes: Block (aes & AES in CBC -MAC or 3DES)
SIKE: Transport Layer Security works in the **Application layer**

Where to use:
- As TLS is application level, each application has to set up its own session
- It is up to the application what to send

## Needham-Schroeder Protocols
---
Needham-Schroeder (NS) protocol is used to define the steps used when trying to send encrypted messages over an insecure network. It involves Alice, Bob and a server that Alice and Bob both trust. It can be symmetric or asymmetric mode. The symmetric mode forms the base for the Kerberos protocol, which is used in many places. 

**Symmetric mode**
Description:   
[![File:Symetric Needham-Schroeder-Protocol – linear.svg](https://upload.wikimedia.org/wikipedia/commons/thumb/4/4b/Symetric_Needham-Schroeder-Protocol_%E2%80%93_linear.svg/424px-Symetric_Needham-Schroeder-Protocol_%E2%80%93_linear.svg.png)](https://upload.wikimedia.org/wikipedia/commons/4/4b/Symetric_Needham-Schroeder-Protocol_%E2%80%93_linear.svg)
#todo but what are the purposes of each arrow? why need to send B to trusted server?
Naive NS symmetric has been shown to have weaknesses (**Replay attack**)
- Especially when the same kAB/shared key has been used repeatedly, then kAB/shared key would have gone "stale"
	- Server is responsible for choosing good kAB #todo what are the properties of kAB?
- Fix: To include a **timestamp** in the message to be encrypted by the key

**Asymmetric mode**
Description: Server knows everyone's public key, and everyone knows the server's public key. The protocol exchanges public keys between Alice and Bob, and lets them know of each other's identities

Naive NS asymmetric has been shown to have weaknesses (**MiTM attack**)
- If Alice contacts Eve, Eve can re-use NA, which is the challenge sent to Eve by Alice when they were trying to setup communication
	- Eve uses Alice as a "Decryption Service", by using Alice's "old challenge"
	- Alice will not realize that Eve re-used NA, and Bob will believe that Alice established a connection
- Fix: Add Bob's identity into the challenge response
#foc