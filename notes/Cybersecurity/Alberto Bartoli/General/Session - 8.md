
---
##### Vulnerabilities - CVE
1. Common Vulnerabilities and Exposures - CVE
2. Official reference - CVE MITRE - Github repo
3. Practical reference - NIST - webapp
4. Very handy - cvedetails - webapp browsable by many criteria
5. EUVD - European Union Vulnerability Database - Has added the EPSS score
6. Each CVE record is composed of
	1. CVE-ID - CVE-YYYY-*NNNN..NN* - Unique identifier of the vulnerability
	2. Textual description & links
	3. CPE - Common Platform Enumeration - Vendor, System, Version in standard format
	4. CWE - Common Weakness Enumeration - Type of mistake(s) in standard taxonomy
7. Each entry (CVE) is composed of
	1. Injection type
	2. Impact type
	3. Attack complexity
	4. Each expressed in predefined categories
	5. Distilled in a single severity score \[0, 10\]
	   *CVSS - Common Vulnerability **Scoring** System*

##### Injection categories
1. Based on user action
	1. User action required
	2. No user action required
2. Based on target proximity
	1. Local
	2. Remote
		1. Authenticated
		2. Not-authenticated

##### Worm-able Vulnerabilities
1. Exploit that propagates itself automatically
2. No user action required -- No authentication on remote target

##### Vulnerability Vs Exploit Vs Injection
1. Actual exploit of a vulnerability requires all 3 steps
	1. Vulnerability discovery - Difficult
	2. Exploit creation - Very Difficult
	3. Exploit injection in vulnerable system
		1. Local/Remote
		2. User/No User
		3. Varying levels of difficulty
2. Exploitable Vulnerabilities $\subset$ Vulnerabilities $\subset$ Bugs
3. POC Exploits created as a prof that a certain vulnerability can be exploited. These are publicly available & can be modified to actually exploit a vulnerability