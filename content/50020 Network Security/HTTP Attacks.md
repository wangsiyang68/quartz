TLS optimization
- Has the 0-RTT which is encrypted with shared key if client is going to the server again
	- Vulnerable to replay attack of the encrypted 

What is the bad thing about HTTP?
- No TLS, no encryption?
HSTS?

Problems with HTTPS:
1. The upgrade from HTTP to HTTPS is sometimes blocked
	- Favicon??
2. Forged Certs
3. Mixed Content
	- Other links that are in http in the https website are usually blocked
	- However, links in http for forms are usually allowed, but no more lock
4. Side Channel Attacks
	- Peeking through SSL: If site is AJAX rich (i.e. many layers of forms), can measure time taken for interaction with the server to expose specific internal state of the page
	- Another side channel attack: https://youtu.be/skQNwd9Jij4