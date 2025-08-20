**

# General (42 hours) Sep-Dec 2025

|   |   |
|---|---|
|Number of hours|Topics|
|8|- Course presentation. CIA Triad. Attacks: motivations and targets. Attacking an organization. MITRE ATT&CK. Overview of some Tactics: Initial access, Execution, Persistence, Command and Control, Discovery, Lateral movement, Privilege escalation<br>    <br>- Overview of Tactics: Exfiltration, Impact. Remarks on defense. Understanding MITRE ATT&CK.<br>    <br>- Security policy. Operating system protection. Accounts and resources. Principle of least privilege. Cybersecurity and economics<br>    <br>- Temporary privilege elevation. Linux and Windows mechanisms. Access control lists. Linux and Windows. Access control model based on principals (accounts, executable, authentication). Smartphone access control. Windows integrity levels.<br>    <br>- Understanding Access Control and Principle of Complete Mediation.|
|8|- Reverse shells. Infection chains. Execution with Command and scripting interpreters. MITRE ATT&CK mapping of common scenarios for Initial Access and Execution<br>    <br>- Phishing and sending domains categories. Techniques for persistence and privilege escalation: setuid, web shells, scheduled tasks, DLL hijacking<br>    <br>- C&C in botnets. Domain Generation Algorithms. Advanced initial access techniques: trusted relationship and supply chain compromise. Malware detection: Indicators of Compromise<br>    <br>- Malware detection scenarios. Threat intelligence. Antiviruses|
|8|- Threat models. Password-based attacks. Online guessing: password guessing, password spraying, credential stuffing. Detection and reaction<br>    <br>- Stealing password storage. Secure password storage: hashing, hashing and salting. Password cracking attacks.<br>    <br>- MFA: second factors and threat models. Linking and login. One time passwords with SMS and authenticator app: user experience and implementation outline. Real-time phishing and voice phishing.<br>    <br>- Security keys: linking and login. Smartphone push notifications. Trusted devices and passwordless login.|
|8|- Command injection vulnerability: Case study (Palo Alto Network 2024). Memory corruption vulnerability case study (Heartbleed). General lessons on vulnerabilities. Memory corruption bugs and vulnerabilities. Memory management. Examples of exploitation by overwrite.<br>    <br>- Intrinsic issues in software vulnerabilities. Issues in cybersecurity testing.|
|8|- Vulnerabilities: definition, public databases. Injection categories. Common Weakness Enumeration (CWE). Common Vulnerabilities and Exposures (CVE). Common Vulnerabilities Scoring System (CVSS). CVSS base score and full score. Definition of base score and limitations. Issues in quantifying security of a software artifact. Vulnerability lifecycle: ideal case. Issues in patch development. EOL software. Vulnerability disclosure processes.<br>    <br>- Zero-day vulnerabilities. Issues in patch management. Issues in vulnerability prioritization. Vulnerability management. Asset management.<br>    <br>- Exploit Prediction Scoring System (EPSS). Effectiveness in exploit prediction: EPSS, CVSS, heuristics. Vulnerability management in organizations. Asset management|
|2|- Automated attacks and Attack economics. Financially-motivated attackers and Advanced Persistent Threats. Threat matrix<br>    <br>- Defensive analysis of threat matrix. Economical issues. Q&A|

  

# Specific (28 hours) Jan-Apr 2026

|   |   |
|---|---|
|Number of hours|Topics|
|14|Service authentication in Windows and in Windows networks. NTLM authentication<br><br>  <br><br>NTLM Attacks: pass-the-hash. Password cracking. AiTM (Adversary in the middle). NTLM Relay attacks. Forced authentication and Coerced authentication. Techniques for obtaining AiTM capabilities (outline). Signing and sealing (outline).<br><br>  <br><br>Kerberos: introduction. Service tickets. Almost-Kerberos. Signing and Sealing<br><br>  <br><br>Weak keys and Full Kerberos. TGS and TGT. Replay attacks and defenses. Usage of Kerberos in Windows environments for interactive logon and for network logon. Password cracking attacks. Kerberoasting and AS-REP roasting<br><br>  <br><br>Lateral movement. Use of alternate authentication material. LSASS content and risks in remote administration practices. Outline of ACL management of Active Directory objects. Pass the hash, Overpass the hash, Silver ticket, Golden ticket. AD Attack paths: Certified pre-owned, Shadow credentials.<br><br>  <br><br>U2U abuse. Domain policy modification.|
|4|OAuth / OpenID connect / SAML / SPID|
|8|- Memory corruption bugs and vulnerabilities. Memory management. Examples of exploitation by overwrite.<br>    <br>- Buffer overflow. Safe input library. Attacker-controlled variables and safe string library. Stack frames. Stack smashing. Examples of buffer overflow in data region and in heap region. Outline of defensive strategies for preventing memory safety vulnerabilities<br>    <br>- O.S. mitigations: ASLR, data execution prevention. Compiler mitigations: stack canary, pointer authentication.|
|2|- IDOR vulnerability prevention in webapps. Introduction to web security testing: BURP. Example of IDOR in OWASP Juice Shop.|

  
**