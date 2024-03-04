# Dig command
---
Sample output of a dig command:
Usual dig command
```Shell
(base) siyang@siyang-Swift-SF314-41G:~/Obsidian$ dig MX mit.edu

; <<>> DiG 9.16.1-Ubuntu <<>> MX mit.edu
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 55858
;; flags: qr rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 0, ADDITIONAL: 1

;; OPT PSEUDOSECTION:
; EDNS: version: 0, flags:; udp: 65494
;; QUESTION SECTION:
;mit.edu.			IN	MX

;; ANSWER SECTION:
mit.edu.		57	IN	MX	100 mit-edu.mail.protection.outlook.com.

;; Query time: 3 msec
;; SERVER: 127.0.0.53#53(127.0.0.53)
;; WHEN: Mon Aug 01 12:42:22 +08 2022
;; MSG SIZE  rcvd: 87
```

dig command with extra options like +noedns
``` shell
Davids-SUTD-Powerbook-2018:~ david_yau$ dig +noedns @ns1-proddns.glbdns.o365filtering.com mit-edu.mail.protection.outlook.com
; <<>> DiG 9.10.6 <<>> +noedns @ns1-proddns.glbdns.o365filtering.com mit- edu.mail.protection.outlook.com
; (1 server found)
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 33606
;; flags: qr aa rd; QUERY: 1, ANSWER: 2, AUTHORITY: 0, ADDITIONAL: 0
;; QUESTION SECTION: ;mit-edu.mail.protection.outlook.com. IN A
;; ANSWER SECTION:
mit-edu.mail.protection.outlook.com. 10 IN A 104.47.41.36 mit-edu.mail.protection.outlook.com. 10 IN A 104.47.42.36
;; Query time: 223 msec
;; SERVER: 104.47.29.42#53(104.47.29.42) ;; WHEN: Sun Apr 14 19:36:15 HKT 2019
;; MSG SIZE rcvd: 155
```

Key points to note:
- the key is the domain (`mit.edu` in this case)
- `MX` refers to an email service
- The flags section contain useful data:
	- qr = Query
	- rd = Recursion Desired
	- ra = Recursion Available
	- aa = Authorative Answer

#networks 