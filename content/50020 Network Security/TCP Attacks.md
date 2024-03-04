## Transport Layer
- some methods include the TCP   
    - the port concept lives in here
- Important to spoof the seq and ack number correctly, or else victim will drop the packets
    - sequence number and acknowledgement number is a random number
    - However, the seq and ack role is to ensure correct order of packets
    ![[Pasted image 20230925075027.png]]
    

## TCP attacks

- **SYN Flood**    
    - send many syn packets
        - Without ever trying to finish the syn-ack sequence
        - and faster than the server can process the tcp connection requests
        - A type of DOS attack
        - Solved with syn cookies
            - encode extra information in the seq/ack numbers
                - Server sends back hash of a set of specific details (client ip, port, server related key) to the client
                - Attacker only concerned with sending the opening attack, will not resend the ack of hash + 1
        - Also solved with flow control?

**Reset Attack**
- If attacker is able to be situated between victim and server, can constantly send RST packets to end the connection
- Possible because no network layer encryption, and TCP header remains unencrypted during the SSH encryption at Transport layer. Reset flag just needs to be changed in the TCP header
- Need to know the following:
	- Source ip, source port, dest ip, dest port, **Sequence number**
- On video-streaming connections, it is usually harder to just send spoofed reset, since the flow of packets from server is fast, making the sequence number go outdated quickly

- **Attacks on TCP Congestion control**
    - tcp congestion control is a way to maximise the bandwidth on the network by varying the speed of packets sent?
        - Leaves it vulnerable to Optimistic ACK Attack
        - No solutionn
        - but not easy to guess the acknowledgement number either
- **Session Hijacking**
    - Inject some code via the payload to establish a connection between the client and server 
	    - Enables further attacks (e.g. create Reverse Shell)
	    - inject data by setting sequence number to be x + delta, which results in the data in this packet being stored at the receiver's buffer at position x + delta
		    - if sending packet with x+1, then server might discard it if it processes another x+1 packet.
 -  To prevent:
	 - Encrypt the payload with a shared key, instead of sending it via plaintext in telnet
- **IP Spoofing**
    - can pretend to be someone else and send malicious flags (e.g. reset to end the connection between victim and server



Detecting sniffers
- ARP watch
- Passive vs Active

Port Knocking
- susceptible to replay attack
	- just copy whatever pork knocking attempts
	- Resolution time dependent knock sequence

Network Address Translation
- set local address to 192.168.x.x 
- When sending out data, translate address back to router address and then go from there

## UDP Attacks

UDP: can be still used if a certain packet loss and order is not too important, there are a few mitigations. Idea is to add in some TCP like functions into the Application data
- Application can set the packet order data in the data payload
- Can use extrapolation(?) to guess data of dropped packets

used for DOS attacks: Some strategies include:
1. Turning one packet into many (smurf packet)
	1. Or Fraggle Attack
2. Turning one packet into a zombie
	1. UDP ping pong attack 
		1. port 13 before it was patched, some time server behaviour, they dont even look at the packets data, just respond when a packet is received on this port
			1. Attack: assume there are two time servers A & B. By spoofing a packet to B that has the source IP of A, then B will respond to A, A to B, and so on and so forth
3. Turn small packet into a super large attack
	1. [UDP amplification attack](https://www.imperva.com/learn/ddos/ntp-amplification/)
	2. Idea: send a small packet that sends back a large sized packet in response

#netsec 