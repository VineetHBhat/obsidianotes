
---
##### Application Resources
1. Mail/Web server is not defined in OS
2. Access decision must be taken by the application (Mail/Web server)
3. For a Web Server;
  - Resource is URL
  - Account is username of authenticated session
  - Resource is requested using HTTP request
4.  Identities/Resources of the application server may have nothing to do with Identities/Resources of the OS

##### Complete mediation
- Every access to every object must be checked for authority
- Saltzer and Schroeder (1974)

##### Reference Monitor
1. A reference monitor is a fundamental security concept for access control, defined by three core requirements:
   - It must be always invoked (complete mediation)
   - Tamperproof
   - Small enough to be fully analyzed and tested (verifiable)
2. It is a hypothetical, abstract component responsible for **enforcing access control policies** by **intercepting and validating every request** from a subject (like a user or process) to access an object (like a file or resource)
3. While ACLs provide the rules for access, the **reference monitor is the mechanism that enforces those rules**, acting as a constant security checkpoint before any action is allowed

##### IDOR
1. Insecure Direct Object Reference
2. A web application security vulnerability where a user can access objects (like files or database records) they are not authorized to see by directly manipulating input parameters, such as IDs in URLs, without proper access control checks
3. Attackers exploit this by changing an ID to view another user's data or perform unintended actions.
4. This vulnerability is a significant concern and was highlighted in the OWASP (Open Web Application Security Project) Top Ten for web application security risks

##### Discretionary Vs Mandatory Access Control (DAC Vs MAC)
1. DAC
   - Resource owners manage resource ACLs
2. MAC
   - Allow defining and enforcing global requirements
   - Take precedence over DAC
3. Real OS and cloud services support a mix of them

##### Access Control = Authorization ≠ Authentication

##### Principle of Least Privilege
1. Every program and every user of the system should operate using the least set of privileges necessary to complete the job
2. It also reduces the number of potential interactions among privileged programs to the minimum for correct operation, so that unintentional, unwanted, or improper uses of privilege are less likely to occur
3. Saltzer and Schroeder (1974)

##### Temporary Privilege Elevation (Basic Idea)
1. Executable F:
   - Created by an account A-H with high privileges
   - Marked with "elevation"
2. Process P owned by an account different from A-H:
   - Creates P1 that executes F
   - P1 has "elevated privileges"
3. Rationale:
   - A-H has encoded certain actions in F
   - A-H trusts that F can be executed safely with high privileges
4. Linux implements this using `suid`

##### Temporary Privilege Elevation (Linux)
- Linux has Real & Effective UID for processes (Professor mentioned that there are actually 3 UIDs associated with processes)
- Access control decisions are taken based on Effective UID
- `sudo` changes the Effective UID to `root`

##### In Linux, each process is associated with 3 different types of UIDs
- **Real User ID (RUID)**: UID of the user who actually launched the process. It reflects the true owner of the process & remains constant throughout its lifetime.
- **Effective User ID (EUID)**: This UID is used by the OS to determine the permissions and access rights a process has when interacting with system resources (files, devices, etc.). The EUID can be changed during a process's execution, for example, when a set-user-ID (SUID) program is executed, allowing it to temporarily gain the privileges of the file owner. 
- **Saved Set-User-ID (SUID)**: This acts as a backup of the EUID before any changes occur. It allows a process to revert to its original effective UID when needed, ensuring it can regain its initial privileges after performing operations that required elevated privileges

##### Temporary Privilege Elevation (Windows)
- Windows recently added `sudo` for `Administrator` group (needs to be enabled)
- User Account Control (UAC)
- Executable F:
  - Owned by Administrator
  - Marked with `AsInvoker` / `RequireAdmin`
- When `RequireAdmin`:
  - `AutoElevate` True: No explicit consent, no credentials
  - `AutoElevate` False: Explicit consent, credentials
- Temporary Privilege Elevation does not change account
- Every process has two tokens
  - **Limited** - Administrator groups and most privileges removed
  - **Full** - All groups and privileges
- Every process uses the limited token
- A process uses the full token only when executing files with `requireAdministrator`

##### Temporary Privilege Elevation Summary
- Linux - Change to account with more privileges
- Windows - Change privileges of the account
- Elevation triggered by an executable - It must be checked very carefully
- Windows - Auto-elevation (no user consent / no credentials) only on Microsoft-approved executables

