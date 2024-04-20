Context:
- To verify email origin, safeguarding content, and ensuring sender integrity

Techniques
- Sender Policy Framework (**SPF**)
	- whether the post office (DNS address of mail server) is within the trusted list
	- However, it only authenticates the envelop sender (return-path) and not smth else
- DomainKeys Identified Mail (**DKIM**)
	- However, does not authenticate the sender's identity directly, and does not handle failures
- Domain-based Message Authentication, Reporting and Conformance (**DMARC**)
	- Leverages both of the first two techniques
		- Have junk, quarantine, none
	- There are two modes of reporting: aggregate and forensic
		- Aggregate report to tell u one time how much spam u get
		- Forensic report to give u a status report per spoofed email
	- Challenge: cannot detect if the malicious mail server is hosted on a legitimate cloud service (e.g. amazon)
		- Effective, but usually will be detected by the cloud provider after some time.

Lack of c