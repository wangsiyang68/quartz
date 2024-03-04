# DNS Caching
---
Cache issues:
- Cache entries may be out-of-date
	- If name host changes IP address, it may not be known internet wide until all TTLs expire
	- Analogy: phone number changed but phonebook not updated
- Solution:
	- Have some update/notify mechanisms that follow proposed IETF standard (e.g. RFC 2136)
		- Server notify specific (i.e. close friends only) whenever their ip address change
#networks 