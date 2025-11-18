
---
##### Vulnerability management
Two fundamental components
1. Vulnerability management
	1. Which systems
	2. Who is in charge
2. Vulnerability prioritization
	1. How to allocate defensive efforts to CVEs

#### Exploit Prediction
1.  Considered the "state of the art"
2. But it does have many limitations
3. Exploit Probability
	1. Vulnerability $CVE-i$
	2. $P(CVE-i, d) = \frac{\#\ Exploitation\ attempts\ of\ CVE-i\ in\ [d,d+30]}{\#\ Expolitation\ attempts\ of\ all\ CVEs\ in\ [d,d+30]}$
	3. Probability that $CVE-i$ will be exploited in the next 30 days
4. Worldwide (everywhere)
5. Approximated by collecting many TI feeds
6. Computed a posteriori
7. Exploit Prediction: Problem Definition
	1. Vulnerabilities that have been actually exploited worldwide in T
	2. Those with $P(CVE-i) \neq 0\ (on\ some\ day\ in\ [t_0,t_0+T])$
	3. We "compare" PatchedSet vs ExploitedSet
8. **Efficiency** (Precision) = $\frac{\#\ (Patched\ and\ Exploited)}{\#(Patched)}$
9. **Coverage** (Recall) = $\frac{\#(Exploited\ and\ Patched)}{\# (Exploited)}$
10. **Patching Effort** = $\#(PatchedSet) \equiv Patching\ Effort$
11. Coverage and Efficiency are relative indexes
12. Independent of Patching Effort
13. This state-of-the-art does take into account the "contextual risk"

##### Exploit Prediction Scoring System (EPSS)
1. $EPSS(CVE-i,\ d)$: Estimate of $P(CVE-i,\ d)$
2. API - https://www.first.org/epss/api
3. This value is provided in EUVD database by Enisa VD
4. Each CVE is represented by ~1400 features
5. EPSS is much better than CVSS
6. It is called a predictor, but there are strong indications that it is more like a summary of what is already happening & not a predictor.

##### Attack Economics & Attack Categories
1. Human-operated attack campaigns
	1. Depends on # targets
	2. Low value targets are **not** economically rational here
2. Automated attack campaigns
	1. Mostly independent of # targets
	2. Low value targets are economically rational here
	3. Extremely frequent
3. Financially motivated attackers - most common scenario
4. 4 attack categories introduced by Steven M. Bellovin
	1. Focus
		1. Targeted - (Information stealing, disruption) - (less frequent)
		2. Non-Targeted - (Money)
	2. Skill (Effort)
		1. High (Human operated)
		2. Low (Automated)
	3. ![[threat_matrix_1.png]]
	4. ![[threat_matrix_2.png]]
	5. ![[threat_matrix_3.png]]

##### Defender Mindset (Strategic Framework)
1. Automated - Opportunistic
	1. Basic security hygiene
2. Human-operated - Opportunistic
	1. Defender Resources Vs Attacker Resources
	2. Encourage attacker to change target
	3. Defense must appear good
	4. Penetration/Lateral movement should be expensive
	5. Defense in depth - Multiple independent layers
3. Human-operated - APT
	1. Very unlikely that Defender Resources > Attacker Resources
	2. No need to focus on this
	3. Cross finger & hope for the best
4. Suggestion: **Strong focus on opportunistic attackers**
