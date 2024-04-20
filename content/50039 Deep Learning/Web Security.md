Can use software isolation principles here too
- App must call a control layer to communicate to another app (i.e. indirect communication)
	- Known as sandboxing applications
- Same origin policy
	- Isolate web content

Tricking user to visit evil website
compromise a non evil website
intercept network comms

Guard Model for Web
- Some terminology:
- Principal: Origin
	- 
- Guard: Browser
- Resources:
	- DOM, Cookies, Data, etc
- Policy: same origin policy
	- one origin cannot write or read to different origin
		- Principle: Web app cannot access resources from another web app directly
		- Cannot read but can load into user file system?
	- Same -> Strict string matching
		- Cannot allow if incomplete subset

javascript can run with the primary origin, and access the cookies, since it runs with the same privileges of the domain

CORS (cross origin resource sharing) allows the whitelist of certain domains such that if they want to access source info, they can do so if their domain is in the whitelisted domains

cookies are only based on get request url
- only check the url in the browser

Idea:

In the domain, have suffix of the url domain
In the path, have prefix

Some cookie stuffing to evict valid cookies attack