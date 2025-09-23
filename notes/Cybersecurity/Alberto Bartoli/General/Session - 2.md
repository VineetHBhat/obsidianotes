
----
##### Threat Model
- RCE - Remote Code/Command Execution - Related to Reverse Shell discussed in Session - 1
- Attacker can exploit a vulnerability for RCE

##### Infection chains
- Arbitrary execution of a file on target
- Adversary executes a command (using Reverse Shell) on target to download a file & then execute it
- In some cases, the download is an intermediate payload that downloads/configures the actual payload

##### Initial Access & Execution
- For initial access, tactics used are:
  - Phishing
  - RCE vulnerability

##### C2 Infrastructure (Command & Control)
- **Botnet** - a specific class of attack. Example: `Mirai` botnet
- How to maintain control if IP that the malware is talking to is block at the firewall?
- **IP fast-flux** - Each bot contains a predefined `N-BO` name. Attackers modifies IP-X in the DNS record for `N-BO`. Adversaries tend to use questionable registrars. But defenders could still block the name
- **Domain flux**
  - Each bot contains a *Domain Generation Algorithm* (DGA) that generates a new name deterministically every day
  - The adversary buys the names in advance
  - The defender has to discover a name every day & block it
  - OR defender will have to reverse engineer the bot & determine the future name that are not registered yet & buy those name to dismantle the botnet
  - Adversaries have improved DGA so it has become extremely difficult to dismantle the botnet
- **Emotet** - Contemporary/modern botnet
- **Torpig** - A very powerful botnet was taken over by defenders in 2009. DGA was first observed in Torpig. But after updating the bot through an additional C2 channel, the botmaster took back full control.

##### Security Policy
- Set of rules (explicit or implicit) that decide who can do what
- For each Account, Resource, what operations are allowed
- What can the malware do on the victims machines? kill processes, read memory, modify config?

##### Access Control
- Enforce security policy at Application level, OS level, Hardware level
- **Account** - Every identity in the system
- **Resource** - Every IT Object in the system. Example, file, socket, server config, account attributes, etc.
- Different rules have different **expressiveness** (Expressiveness in access control refers to a system's ability to define complex authorization policies using rich logical conditions, allowing for fine-grained control over resource access beyond simple user-based or role-based rules)
- The only way to access resources is by using system calls
- Every access to resources is guarded by the OS
- A process cannot access the memory of another process directly
- A process can invoke a system call for reading/writing the memory of another process

##### Access Control Lists
- Every process is owned by an account (Process <=> Account)
- Every resource is owned by an account (Resource <=> Account)
- Every resource has an ACL. Resource owner controls the resource ACL
- OS takes decisions only based on the requesting Account
- All Processes of the same account can execute the same operations (same access rights)

##### Groups & Privileges
- Accounts/Resources may be grouped
- ACL may be specified in terms of groups
- Every system call invocation by a process of a High Privilege account will succeed
- High Privilege Account can't access every memory address

**Principal** = Account + Operation + Resource
**ACE** = Access Control Entries

##### ACL in Smartphone OS
- Each installed app has an app-identifier
- **Principal** = \[Account, app-identifier]
- Data of an app can be isolated from other apps of the same OS account

##### Windows Standalone (not AD) ACL
- Access rights of an account "accumulate" over multiple ACEs & possibly inherited from other resources
- ACLs can Grant as well as Deny access rights. This can result in conflicting access rights that are hard to predict.
- A resource may be contained in another resource
- An ACE may be inherited by all the contained resources
- "Someone can do something they should not be able to do" because the actual security policy resulting from ACLs may not be the intended one