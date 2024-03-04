Cross-script request
- Use case: sometimes, you want to display another webpage item (like youtube window) in your own website
	- e.g. iframe, which is like a mini browser in your browser
		- only traffic between original site and iframe is considered cross site. Traffic between iframe site and same site is considered as same site
	- Uses Same Origin Policy (SOP) to allow or deny access

Same Origin Policy checking
- If document.domain in the link matches the website it is originating from, allow access to the said website
- origin = scheme, domain, port. Given http://google.com:80,
	- scheme = http
	- domain = google.com
		- Anything before the next slash
	- port = 80
- Could be too strict -- what else can we do?
	- Expand document.domain to allow everything till the base domain
	- For example, instead of www.example.com, set as example.com only to allow other websites like login.example.com
- Disallow different origin but subdomains are OK

Document.domain
- "who can have my room key"
	- can be relaxed, by making the document.domain = base domain
- Can be not set by the website
	- If not set, then it will be strict

CORS
- Add information to the header
- Need to add this when you do a cross site request to give information about self, unless the server relaxes the rules on domain
- **Preflight request?**
- Ability to make "credentialed" requests that are aware of HTTP cookies and HTTP Authentication information

CSRF:
- Problem: server cannot tell whether a request is same site or cross site without some help
- All cookies belonging to example.com will be attached to the request when a link is clicked?
	- Because it is the user who had clicked on the link, so browser will not check and just attach all cookies and headers (hence bypassing SOP)
- Steps
	- Attacker makes a malicious webpage that can forge a cross-site request to the targeted website
	- The victim also needs to be logged into the targeted website
- Problem: Without countermeasure, server cannot distinguish whether a request is cross site or same-site
- Solution:
	- Referrer Header: 
		- http Header field must identify the address of the web page from where the request is generated
			- Has privacy concerns because you can see the trail
	- Same-site cookies
		- Attach a cookie if a request was made from the same side, depending on the value of the attribute that determines how strict the policy is
	- Secret Token
		- Only one not dependent on the browser (i.e. server creates this mechanism)
		- Server embeds a random secret value inside each web page, hidden somewhere
		- Cross site requests cannot get the token as this is guaranteed by browsers (same origin policy > need to set the document domain properly)
		- **why does the different website cannot get the secret token because of SOP?**
			- This is done by either making the secret token attribute be "hidden", or set in a separate CSRF cookie that can only be accessed by same site request

#netsec 