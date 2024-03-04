# DNS Records
---
It is a distributed db storing resource records (RR)
RR format: `(name, value, type, ttl)`
Four types that we know of. Each type will determine the meaning of `name` and `value`
1. type = A
	- name is hostname
	- value is IP address
2. type = NS
3. type = CNAME (for finding canonical name)
4. 