# Certification Authority
---
## Characteristics:
- Everyone knows the CA public key
	- Common knowledge that cannot be faked -- the CA public keys are burnt into web browsers, computers, etc
- Everyone trusts the CA
	- Trust that CA (e.g. Verisign, IMDA) will carry out stringent checks of the identity and sign correct public key

## Context
**How does this solve the MiTM attack?**
Charly's public key is known to everyone.
However, eve does not know charly's private key, so Eve cannot impersonate Charly

Note: still need to verify Charly/CA's identity, solution for that is to bootstrap somewhere
- However, this means that CA needs to sign all the messages

**Solution again:** 
Public Key Infrastructure (CA style)
Obedient society where everyone trust their boss and their intermediates (i.e. train of trust)

Problem:
if an intermediate CA has gone rogue, checks done by anyone below the intermediate CA will be compromised

Key Revocation list: a signed list of certificates that should not be trusted (i.e. a blacklist of certificates)

However, CAs are expensive to obtain

Other PKI: 
1) Web of Trust
	1) Decentralized: people sign each other's signatures
	2) Example: PGP
2) However, it is difficult to bookstrap such a system
3) Other problems
	1) If lost private key, cannot read old documents
	2) Key cannot be deleted because, when a key is submitted to a key server, it is forwarded to other systems

#foc