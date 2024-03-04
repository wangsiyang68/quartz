## Network Layer Recap:
ttl = gets decremented every time it reaches a router, to prevent packets from flying around forever

## Weaknesses

- Unencrypted Transmission
	- Eavesdropping is possible at any intermediate host during routing
- No source authentication
	- Sender can spoof source address, which makes it difficult to trace packet back to attacker during attacks like DOS
- No integrity checking
	- Anything in packet (header, payload) can be modified while en route to destination, which enables forgeries, redirections, MITM
- No bandwidth constraints
	- Can inject large number of packets to launch DOS attack
	- Can be easily done using broadcast addresses

Attacks

- Ping of death
    - ICMP specified must fit a single IP packet, but you can send a modified ping packet that exceeds max size (with IP fragmentation)
    - Can cause some OS to crash due to buffer overflow, since Ping packet is expected to have 64k bits
    - Can overflow into the OS yeet
- Smurfs
    - Amplify your ping by sending it to a large subnet
    - A type of DDoS
    - [ ] Ping a broadcast address using a spoofed source address, BUT what does this mean?
- DDoS
    - Many zombies target at the victim
    - Victim being the root, leaves are all the zombies
    - However, difficult to identify the zombie because the source IP
    - Approach
        - Assume that routers are truthful, and that each router will attach their IP addr so that i can trace the path (logging?)
            - Adds more information to the packet, which may make it super big
        - **Probabilistic marking?**
            - [ ] Uses limited bits in a packet that is not touched?
            - [ ] how does it calculate the probability? of what?


#netsec 