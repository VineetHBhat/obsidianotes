
---
##### Password stealing (Slides are restructured after previous lesson)
1. Password stolen in clear text
	1. Threat Model - Execution + C&C + Account with sufficient privileges
		1. Input capture
		2. Insecure storage
	2. Threat Model - Ability to observe network traffic + C&C
		1. Network sniffing
2. User stores
	1. Stealing password storage of applications like web browsers, password managers
		1. Credentials are stored in encrypted format
		2. Key may be read from process memory
		3. Browser
			1. Key can be obtained by any process associated with the user or the SYSTEM account
		4. Password Manager
			1. Key is not stored anywhere
			2. Key is derived from a master password typed on the keyboard (INPUT CAPTURE)
3. O.S. Stores
	1. Windows
		1. SAM (Security Account Manager)
		2. Account definition + Passwords
	2. Linux
		1. `/etc/passwd` - Account definitions
		2. `/etc/shadow` - Passwords
	3. Windows Server
		1. SAM for local users
		2. NTDS for all identities of the organisation
	4. Passwords are usually stored as non-invertible function of PWD
	5. Not ready for immediate use
		1. Further offline attack techniques necessary for attempting to obtain PWD
	6. Windows systems
		1. You can use the non-invertible function of the PWD (!)
		2. Further offline attacks for attempting to reconstruct the PWD are not needed
4. Server stores
	1. Service S may be structure to use accounts
		1. Local OS
			1. S uses NTLM protocol to get local users from machine trying to authenticate
		2. Defined & managed by S itself (usually in a database table)
			1. If passwords are stored in clear text in database or any file => Catastrophe

##### Password guessing
1. Guessing attacks are usually not targeted
2. Keep in mind that Not in a dictionary - Not common - Not default - Not reused from a breached site is **much more important** than 7 digits - 3 special symbols - 2 uppercase
3. Threat Model - Attacker is able to execute authentication protocol with victim machine. Requires much smaller capabilities.
4. Online guessing
	1. Brute force
	2. Used for Initial Access or Lateral Movement post compromise
	3. Password of any account is enough
	4. Password dictionaries available online are used
	5. Common passwords - `github default password list`
5. Password spraying
	1. Use of single or a small list of common passwords against many different accounts
	2. Usually more efficient & harder to detect
6. Credential stuffing
	1. Use of breached credential dumps to gain access to target accounts through credential overlap (same username across different organisations)
	2. Accounts can be compromised by taking advantage of the fact that users tend to use the same passwords across personal & business accounts