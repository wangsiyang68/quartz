- Sit between application and transport layer
- to protect the integrity and privacy of the contents in transport layer

Problems:
1. MITM
	1. Not dissimilar to how you used to block certain sites by rerouting them to 127.0.0.1 in the file in etc/hosts/ 
	2. To combat: need to check if host name of returning page is the expected/requested host name

Creating a simple HTTPS server

- TLS client vs TLS server
	- TLS client does not need to supply CA certificate
	- Client in charge of initiating handshake, server in charge of receiving it
	- servers need to know where all related certs are. also need to know where private key is, 