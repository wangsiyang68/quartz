**Penetration Testing**
- consists of the focused and targeted assessment to identify, evaluate and report on technical vulnerabilities that may affect an organisation
	- external perimeter network
	- web applications
	- internal network
	- mobile application
cloud blurs the boundary between external and internal network

social engineering/phishing attack

AGAIN **CIA** is important remember that A is for Availability

**Red Teaming Exercises**/Tasks in a step by step processess
- Persistence (trying to ccess the internal network)
- Privilege escalation (escalate priviledges to root by compromising user accounts)
- Credential access (trying to get the password)
- discovery (gather info about the domain, network)
- lateral movement (move within the network by exploiting remote services)
- collection (collect data and input from compromised devices)
- exfiltration (encrypt and exfiltrate data via scheduled transfers )

steps:
recon
weaponize
deliver
exploit
install
control: setup command and control
execute

difference between red teaming and pen testing:
- in red teaming. only the higher ups know of the exercise, the company's security team will not know of it. element of surprise!
- adds physical penetration and social engineering 

payload generation:
a payload is malware that the threat actor intends to deliver to the victim.

**AV**s and **EDR**s (AntiVirus and EndPointResponse) look for the "known bad" by inspecting for static signatures into the code that is going to be executed or by looking for beahvioral signatures, such as meterpreter callbacks. Thus, difficult to deliver payloads through these obvious method

solution:
obfuscating and encoding a payload to make it look like a random set of characters that will not make the AV or EDR feel sussy 

deadbox forensics
- autopsy 

analyse logs -- need to selectively choose the most important logs in an image

good resources for cyber security
immersivelab
portswigger
#foc 