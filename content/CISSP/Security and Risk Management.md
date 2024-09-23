ISC2 Code of Ethics:
- The Canons - expected to appear at least once in the 100 qns
1.2: Objectives
- CIA Triad + Authenticity, Non Repudiation, Privacy, Safety
- OT/SCADA = a sort of valve that is involved in critical infrastructure security
1.3 Security Governance Principles
- Need to understand that security is a support function, so need to align whatever you do with the company goals. Means be less technical when explaining up

- Corporate Governance/ Security Governance: what is the governance committee for your company when it comes to cybersecurity?
	- For government, there is a manual called I8
	- Structure, Roles & Responsibilities
		- Senior Management
	3 types of controls, 7 types of categories
	- ISO Series
		- 27005 deals with risk
	- PCI DSS
		- Payment Card Industry
	- NIST
	- COBIT
		- Came up by ISACA
	- FedRAMP
		- Specifically to the US Govt
	- SABSA
	
	Cybersecurity Threat Landscape is always changing = Top dog mantra

1.4 Organizational Processes

1.5 Understanding Investigation Types
- Low to high: Administrative (internal), Civil, Regulatory, Criminal

1.6 Implementing Policies/Frameworks
- CSFv2.0  by NIST -- new version has G (for Govern) in front of a bunch of acronyms
- AICPA System and Organizations Control (SOC) Framework
	- Cloud service providers should subject themselves to a SOC 2 Type 2 report
	- SOC 1 is Financial
	- SOC 2 is Cyber
		- Type 1 is Quick and Dirty look, done within a month
		- Type 2 is more comprehensive, 6 to 12 months
- COSO ERM Framework

1.7 Business Continuity (Will come out in assignment)
- Business Impact Analysis
	- Determine the **Impact** of an event
		- So that when an incident happens, we just go ahead and implement the previously discussed plan
	- Need to differentiate between Business Continuity Plan and Disaster Recovery Plan
- RPO = How much data can you afford to lose. Recovery ...PO?
	- Amount of time between the last good backup and when the disruption event occurs
- RTO = Recovery Time Objective
	- Time required to recover critical IT systems. Note that it does not need to be ready for use yet
- WRT = Work recovery time
	- Need to test whether systems and data are still OK to use post attack
- MTD/MAD = Max Tolerable/Allowable Downtime

Candidate Screening and Hiring

1.9 Risk Management
- Four perspectives -- these are the perspectives that you need to consider when you are doing Risk Assessments
	- Assets - whats important to you
	- Outcome based or process based 
	- Vulnerability based
	- Threat based
- Construct Risk Scenarios -- instructor's suggested method
	- Create "what could go wrong" scenarios that have realistic and relatable view of risks based on the business context, system env and pertinent threats
	- Key Elements
		- Assets
		- Threat event
		- Vulnerability
		- Consequences - what is the direct result of the threat event that affects the business outcomes
		- Likelihood - based on threat intel
	- Need to define the risk appetite
	- Must find the owner for each risk. Important to have a fall guy that will be responsible when the risk becomes reality, so that there is someone account
		- Owner cannot be the CISO
	- Every risk must have a mitigation timeline -- should not drag indefinitely or a long time (e.g. a few years)
	- Response
		- Accept
		- Avoid
		- Transfer/share
		- Mitigate
	- Residual Risks
		- Remains after all security measures and controls have been implemented to mitigate the identified risks
			- Zero day exploits after patching all available patched that have been pushed out
			- Accept the residual risk because it is hard 
	- Approaches:
		- Qualitative Assessment (inferior)
			- Only take this when you have no choice, since it is not straightforward. E.g. Too new to have significant track record of experiences, too unique, lack of resources to do quantitative
			- Data cannot be tgathered in a reliable way
		- Quantitative
			- SLE (Single loss expectancy) 
				- AV * EF
			- ARO(Annual Rate of Occurrence)
			- ALE (Annual Loss Expectancy)
				- SLE X ARO
			- AV (Asset Value)
			- EF (Exposure Factor)
	- Security Control Categories
		- DLP (Data Loss Prevention)...and many more
	- Defense in Depth vs Zero Trust (Segmented access very miniaturized trust zones)
	- Monitoring and Measurement
		- EDR, XDR, 
		- SOAR (outdated), SIEM (splunk, elastic search)
		- Next Gen Firewalls (WAF, NGFW)
	- Key Risk Indicators (KRIs)