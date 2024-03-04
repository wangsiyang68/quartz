Problem: difficult for user to run their own PKI system, so there is only one way authentication (ie the client authenticate that server Certification is real)
Therefore, there is no way for client to tell whether the public key he has received from server is legit or not

Need to verify common name > or else attacker can create its own chain of trust that is actually not exactly legit

MITM via proxy > assume that you are able to get the browser to accept a self signed Cert from attacker

CASE STUDY
- Comodo
	- Approval
- DigiNotar
	- Private key of CA was compromised
- Use poor algorithm (MD5, SHA-1)
- Human
	- not checking the common name (apple.com in cyrllic)