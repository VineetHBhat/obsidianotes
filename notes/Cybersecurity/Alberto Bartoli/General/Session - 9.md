
---
##### TOCTOU
1. Time-of-Check Time-of-Use (TOCTOU) Race condition
2. CVE related to Microsoft Windows Cloud Files Mini-filter

##### CVE
1. Maintained by a consortium of organizations called CNA (Common Numbering Authority)
2. Vulnerabilities are published using below process:
	1. Submission by researcher
	2. Analysis by CNA
	3. Insertion in CVE
3. Zero-days: Vulnerabilities only known to attackers & not listed in the database
4. Contains vulnerabilities related to widely used products only
5. Sometimes, vulnerabilities of "widely used" products are not given any CVE. (Relatively common in cloud services)
6. Powerful vendors sometimes:
	1. Claim it is a feature
	2. Quietly modify the system to fix the vulnerability
	3. Quietly modify the documentation
	4. Quietly modify the default configuration

##### Common Vulnerability Scoring System (CVSS)
1. Vulnerability severity depends on:
	1. Impact
	2. Difficulty of developing an exploit
	3. Difficulty of injection
	4. When there will be a patch
	5. What workarounds meanwhile
2. Standard for quantifying severity by means of a single number (score)
3. Score in range 0-10. Discretized in 5 categories
4. Input:
	1. 8 categorical features part of the CVE
	2. Focus only on ≈ Impact + Injection (Our categories for Impact and Injection were different)
5. Processing:
	1. Translate categories to numbers
	2. Arithmetic formulas + IF-THEN-ELSE
6. Quantitative does not necessarily mean Objective & Meaningful
7. CVSS estimates severity of a vulnerability but is not a measure of the actual risk provoked by that vulnerability
8. Immutable
	1. Does not depend on existence of exploit / patch
9. Independent of the context
	1. Does not depend on the specific environment where the vulnerable system is placed
10. Above is referred to as the **CVSS Base Score**
11. Very few CVEs are actually exploited. CVSS is not a good predictor of which vulnerabilities will be actually exploited

##### CVSS Full Score
1. One can define these additional input values and obtain the full score CVSS
	1. Temporal Score Metrics
		1. Exploit Code Maturity
		2. Remediation Level
		3. Report Confidence
	2. Various Environmental Score Metrics
2. Not particularly useful / used

##### Known Exploited Vulnerabilities (KEV)
1. CISA maintains a free public catalog of KEV
2. Approximately 1 every 250 of newly published vulnerabilities (0.4%)
3. You may think of it as:
	1. CVE
	2. Filtered by threat intelligence information
4. Every predictor you can think of turns out to be
	1. "Low" precision: You worry about many vulns unnecessarily
	2. "Low" recall: You wrongly neglect many vulns

**Google Project Zero** - Public disclosure of vulnerabilities

