# Secure Email application 
---
1. Type 1: Ensure secrecy of message (only sender and receiver can decipher)
	- Use the symmetric key to encrypt the message, and encrypt the symmetric key using $K_b$ so that only Bob can decipher the message.
2. Type 2: Ensure authentication and integrity of message (only Alice could have written the message, and that it was not tampered with)
	- Send (message, $K_b$(H(m))), where K is Bob's public key 
3. Type 3: Ensure secrecy, authentication and integrity
	- Create (message, $K_b$(H(m)))
	- Then use the symmetric key to encrypt the above packet, and encrypt the symmetric key using $K_b$ so that only Bob can decipher the message

#networks