General
- About injecting code into the server -- usually by masquerading code as data
- XSS therefore works by having the server attacking the clients. Client will trust whatever information that server sends without question, and server can therefore access whatever related cookies

Types of attacks:
- Non-persistent (Reflected) XSS Attack
	- What does it mean that a website is reflecting, or any reflection of any type?
	- Why does the client not process the malicious data as data but as code
		- There are data channels, but data that is in it can contain HTML markups/javascript code
		- If not sanitized by the server, then it will be sent to server
		- browser will see it and think is code and execute it as such
	- PROCEDURE
		- Client clicks on link with sus code as data
		- sus code sent to target
		- target return the page with sus code being run
- Persistent (Stored) XSS Attack
	- Attacker directly send their data to a target website

How to steal cookie?
- Variety of methods, i.e. print out cookies, send out cookies,

Three steps that we need to think about for the samy worm
- Add samy to other people's friend list without their consent
- Put a statement on other people profile without their consent
- Make javascript code produce a copy of itself
	- On execution, print out a copy of itself and put it on other people's profile

Countermeasures
- Filtering code out from input
	- Jsoup
- Encoding
	- `>` becomes gt and `<` becomes lt
- Content Security Policy
	- Ban Inlined code
- Securely allow inlined code with NONCE
	- Allow certain javascript codes only with a nonce 

Difference from [[Cross Site Request Forgery|CSRF]]:
- CSRF: origin from victim (need victim to click on link), steal cookies to masquerade as legit request from user
- XSS: origin from server, mixing data and code
	- Secret token does not work, since problem is with the server being compromised
	- COMPROMISE THE SERVER woo