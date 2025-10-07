
---
##### Privilege Escalation
1. Abuse Elevation Control Mechanism (*from MITRE framework*)
2. Example: `setuid` & `setgid`, bypass User Account Control, `sudo` & `sudo` caching, elevated execution with prompt, etc.
3. `lolbas-project.github.io` for Windows & `gtfobins.github.io` for Linux list privilege escalation for incorrectly configured binaries.

**APT** - Advanced Persistent Threat

##### Persistence: Web Shell
1. Adversaries may backdoor web-servers with web-shells to establish persistent access to systems
2. A Web shell is a Web script that is placed on an openly accessible Web server to allow an adversary to access the Web server as a gateway into a network
3. A Web shell may provide a set of functions to execute or a command-line interface on the system that hosts the Web server
4. Web shell traffic is Hidden within web server traffic & Generated only while web shell is being accessed
5. Only the Attacker is aware of the existence of the web shell
6. Unusual URLs on a web server can be spotted in theory......very hard in practice
7. Web shell may remain unnoticed for very long periods

##### Persistence: Scheduled Task/Job
1. Adversaries may abuse task scheduling functionality to facilitate initial or recurring execution of malicious code
2. Utilities exist within all major operating systems to schedule programs or scripts to be executed at a specified date and time. Example `crontab` on Linux & `schtasks` on windows.

##### Persistence & Privilege Escalation: Dynamic Link Library (DLL) Abuse
1. Corresponding terminology in Linux is **Shared Object (.so)**
2. Library used by a program but not contained in the executable file
3. Stored in a file with `.dll` extension
4. Can be loaded in the process memory in two ways:
   - **Load time**: executable contains name of DLL and info "load time"
   - **Run time**: program invokes system call with name of DLL
5. Operating system:
   - Allocates (virtual) memory in the process
   - Locates file containing DLL
   - Maps file content to process (virtual) memory (and a lot of other complex details)
6. DLL search order hijacking

##### Initial Access: Trusted Relationship
1. Organizations often grant elevated access to second or third-party external providers in order to allow them to manage internal systems as well as cloud-based environments
2. Adversaries may breach providers who have access to intended victims
3. Access through trusted third party relationship abuses an existing connection that may not be protected or receives less scrutiny than standard mechanisms of gaining access to a network
4. In Office 365 environments, organizations may grant Microsoft partners or resellers delegated administrator permissions
5. By compromising a partner or reseller account, an adversary may be able to leverage existing delegated administrator relationships, in order to gain administrative control over the victim tenant

##### Initial Access: Supply Chain Compromise
1. Adversaries may manipulate products or product delivery mechanisms prior to receipt by a final consumer for the purpose of data or system compromise
2. Supply chain compromise can take place at any stage of the supply chain including
   - Manipulation of development tools
   - Manipulation of a development environment
   - Manipulation of source code repositories (public or private)
   - Manipulation of source code in open-source dependencies
   - Manipulation of software update/distribution mechanisms
   - Compromised/infected system images (multiple cases of removable media infected at the factory)
   - Replacement of legitimate software with modified versions
   - Sales of modified/counterfeit products to legitimate distributors
   - Shipment interdiction
3. Usually malicious additions to legitimate software
4. Usually distributed to a very broad set of consumers and then additional tactics to specific victims
5. Sometimes popular open source projects that are used as dependencies in many applications

##### Threat Model
1. If there is an adversary in the network:
   - *TCP provides*: No Secrecy, No Authentication, No Integrity
   - *TLS guarantees*: secrecy, server authentication & integrity
2. If adversary has installed a malware in a client, TLS *doesn't guarantee* secrecy, server authentication & integrity
3. What TLS can provide? It DEPENDS on the Threat Model
4. **Threat Model**
   - Set of Attacker capabilities ("what the Attacker can do"). Within the "network attacker" or "malware"?
   - FUNDAMENTAL Concept in cybersecurity
5. Reasoning about "security of a system" does not make any sense. You must always reason in terms of "security of a system with a specified **threat model**" 

##### Threat Model: Network Attacker
1. Observe
2. Observe and Communicate
3. Man In The Middle (AiTM) (Adversary in the middle)

##### Threat Model: Compromised endpoint
1. Attacker can execute some actions on some endpoint(s)
2. Realistic?
   - Vulnerabilities
   - Stolen credentials
3. Attacker can:
   - Read some information
   - Read every information
   - Execute some existing procedure
   - Execute arbitrary code

##### Threat Model: Others
1. Physical access. "If a bad guy has physical access to your computer, it is not your computer anymore"
2. Insider
3. Supply chain compromise

##### Threat model for organizations
1. "**Assume breach**", i.e., Some credentials(s) compromised, Can run software on many internal computers, Full control of some internal computer(s)
2. Only realistic model for organizations today
3. Lots of (bad)implications. In most cases, it can download a description of everything (except for credentials): accounts, groups, resources, ACLs
4. In most cases, it can steal credentials on computers it controls
5. You are assuming a certain threat model. Forget about how the Attacker can arrive there. There are usually a lot of complex ways. You would get confused and miss the focus. Just take it for granted

##### Detection: Malware
1. Identification of malicious software
2. Typically done on endpoints
3. Detection before or during execution
4. Focus on prevention
5. Usually done with Antivirus (Locally operating agent)
6. Detection based on:
   - Signature-based analyses
     - Content patterns known to be malicious
     - Execution patterns known to be malicious
   - Behavioral heuristics
     - Execution patterns typical of malicious sw

##### Detection: Attack
1. Identification of malicious or suspicious activities
2. Typically done by correlating events from different sources
3. Detection usually after the fact
4. Focus on:
   - Visibility (Monitoring)
   - Detection of suspicious behavior
   - Response (Investigation and Remediation)
5. Example: Silver Ticket Attack
6. Usually done with EDR (Endpoint Detection & Response)
7. EDR continuously streams events to a **central platform**
   - Alerts for further analysis by operators
   - Automatic local actions when high confidence

##### Response Capabilities: Anti Virus
1. Focus on prevention
2. Mostly automatic actions
3. Quarantine / Delete detected files

##### Response Capabilities: EDR
1. Focus on: Visibility (Monitoring), Detection of suspicious behavior, Response (Investigation and Remediation)
2. AV + Support for remote investigation and containment
   - Kill malicious processes
   - Isolate endpoint

##### Attack Detection: SIEM
1. Security Information Event Management (SIEM)
2. Centralized system for log management: Collection, Aggregation, Correlation, **Real-time Analysis**
3. Rules for:
   - Alerts → Events that indicate anomalous activity
   - Alarms → Alerts that indicate security incident

##### Indicators of Compromise (IoC)
1. Specialized organization: Identifies a new piece of malware or a new attack campaign
2. Discovers and distributes information for its identification (or IoC): File names, File contents (hashes), Contacted IPs / Domains, etc.
3. Every organization may use IoC to:
   - Block malicious traffic / code execution
   - Determine an intrusion has occurred
   - Associate discovered activity with a known threat actor
4. IoC must be deployed in security tools:
   - Border firewall
   - EDR/AV/firewall on each endpoint
   - DNS Server
   - Application-level firewall