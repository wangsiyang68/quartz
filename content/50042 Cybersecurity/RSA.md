# RSA Encryption
---
## Key Idea 
Allows for sending of messages securely without a shared secret key between Alice and Bob. Builds on DHKE, but modifies it by making it very difficult to find the power in the Discrete Logarithm Problem, as it is based on another hard problem, which is prime factorization

## Steps
1. Create the initial values 
	1. Create the n by multiplying two big primes p and q
	2. Calculate phi(n) by multiplying phi(p) and phi(q) (phi(prime) = prime - 1)
	3. Choose the e such that it is coprime with phi(n)
	4. Calculate d where d is the inverse of e (i.e. $d * e  = 1\ mod \ phi(n)$) **NOT mod n!!!**
2. Encrypt the data
3. Decrypt the data

## Proof of correctness
$m = c^{d} = m^{ed} = m^{phi(n)+1}\ mod \ n$

In the log construction:
de = k phi(n) + 1 for some k (this is just finding an inverse d)
therefore, 
$m = m^{k * phi(n)+1}\ mod \ n$
$m = m* m^{k * phi(n)}\ mod \ n$
$m = m * 1^{k}\ mod \ n$
$m = m$

## Usage 
However, encryption and decryption is slow.
Therefore, RSA is usually not used to create encrypt messages. However, in real life, it can be used to for Digital Signatures.

## Problems
Textbook/Naive RSA is also malleable (i.e. the buy100 and buy999 attack) #todo Why?
- Solution: use optimal asymmetric encryption padding (OAEP), where padding with r (a one time random number). It is a Feistel network with a secure G and H hash functionss.

## Questions
why do we need to calculate phi(n)?
- Because we want the property that m^de = m mod n. However, a product cannot be prime
- However, according to Euler's totient function: $alpha^{phi(n)} = 1 \ mod \ n$
- Therefore, we satisfy the property stated in first bullet point

## Weaknesses
**Signature** = a message that has been encrypted with private key (i.e. $m^d\mod\ n$)
**d** is private key
**e** is public key

### Naive Digital Signatures:
Alice encrypt with private key, then send OG message with signature to Bob

Attack 1: Multiply two or more signatures together = generate valid message
Attack 2: "Reverse engineering", calculate s first given public key e, message will not make sense but still s is a "valid" message

Solution:
Hash the message first, then get the signature of the hash value
Alice sends the message and the signature
Bob needs to get the h first (do H(m)), then check if $h = s^e\ mod \ n$

Why it works:
Attack 1: H(ab) != H(a) * H(b)

### Mixing RSA operation modes
**NOTE**: do not use the same private-public key pair for encryption/decryption and digital signature purposes 
Heres why: 
1. Attacker can send known ciphertext c, and then ask CA bob to sign it.
2. Since $c = m^e\ mod \ n$ , then signing it will reveal m (c is a message that is signed with a public key)

### MiTM 
Previously, it is a passive hacker. But we can also have an active Man in the Middle Attack

For example, Eve can actively compromise the shared session keys (by replacing the a and b). Note that this does not mean that Eve has solved the large prime factorization problem, but has created the "illusion" that Alice and Bob are having the same shared secret (wrong) that is not known to anyone else (also wrong)

**Note**: that this requires attacker to intercept and drop message

**Solution**: [[Certification Authority]]
#foc

