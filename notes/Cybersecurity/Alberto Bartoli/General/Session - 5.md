
---
##### IOC Distribution
1. IoC must be deployed in security tools:
    - Border firewall
    - EDR/AV/firewall on each endpoint
    - DNS Server
    - Application-level firewall
2. **YARA** (*Yet Another Recursive Acronym*)
    - YARA is a rule-based language used to identify and classify malware by creating descriptions based on text or binary patterns
    - Indicator of Compromise (IOC) is a piece of forensic data used to detect an intrusion
	- YARA rules are used to create sophisticated IOCs for tasks like searching for files matching specific malicious patterns, creating signatures for security systems, or performing retroactive hunts on historical data
3. **SIGMA**

**TTP** - Tactics, Techniques, Procedures

##### Threat Intelligence
1. Information about malware campaigns
2. Distributed free/paid
3. Gathered through the analysis of various sources:
	1. Monitoring of threat actors activities
	2. Network telescopes / Honeypots
	3. Malware analysis
	4. Vulnerability assessments

##### STIX / TAXII
1. Structured Threat Information Expression
	- Language and serialization protocol for describing and exchanging cyber threat intelligence (IoC, YARA / SIGMA rules, ...)
2. Trusted Automated Exchange of Intelligence Information
	- *Application protocol* for the *communication* of *cyber threat information* in a simple and scalable manner

##### Static Vs Dynamic Malware Detection
1. Static analysis (AV)
	- Scan of **files/memory content** in search of **predefined signatures**
2. Dynamic analysis (AV/EDR)
	- Analysis of **execution events** in search of **predefined behaviors**

##### Malware Detection: Forensics
1. Analyze after the fact

##### Evasion (bypass)
1. Related to sensors
	1. **Perceptual** - Relevant information cannot be collected due to technological limitation
	2. **Configuration** - Relevant information is not collected due to configuration
2. Related to detection rules
	1. **Logical** - Relevant information has been collected but detection rules have a logical gap. No detection rule for the specific activity.
	2. **Classification** - Detection rules are volumetric or score-based. *Relevant information in the considered time interval is not enough to trigger the rule*.

##### Password-based attacks
1. Valid accounts
	1. Initial access
	2. Persistence
	3. Privilege escalation
	4. Defense evasion
	5. Lateral movement
	6. Very attractive to attackers - Detecting **legitimate access** with malicious purposes is **more difficult**
2. Obtaining passwords
	1. Reconnaissance
	2. Credential access
		1. Online guessing
			1. Brute force
		2. Stealing
			1. Clear text
			2. Not in clear text
				1. Non-invertible function stolen
				2. Not ready for immediate use