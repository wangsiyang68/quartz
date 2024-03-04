# Birthday Attack
---
Key idea: Given a message (m) and a hash function, I can generate another message (m') so that the m' is a collision (i.e. $H(m) == H(m')$)

Possible implementation of attack:
- Given a few "benign messages", attacker can generate a whole bunch of their hash messages
- Create variations of "malicious messages", and look for one that matches one of the "benign hash message"
	- Likely to find a pair given the birthday paradox
- Give victim a benign message to sign, then claim that victim signed the malicious message that has the same pair

#foc 