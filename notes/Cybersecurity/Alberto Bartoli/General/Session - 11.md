
---
##### SSO (Single Sign On)
1. Intra-enterprise
2. Inter-enterprise
3. **Standards** for web-based interactions (HTTPS) - Inter-enterprise
	1. OAuth - Authentication and Authorization
	2. OpenID Connect (based on OAuth) - Authentication
	3. SAML ≈ OAuth
4. Many **implementations**. Ex. Google, Amazon, Microsoft, Okta, KeyCloak, etc
5. In principle, **interoperable** but not so in practice
6. Technology for **any protocol**
	1. Kerberos Realms - DC@Org-A issues a ticket for SP@Org-B
	2. Microsoft Entra - Web-IdP --> Internal-SP

##### OAuth - Functionality
1. Scope string
	1. Resource
	2. operations
	3. Access rights
2. OAuth defines how to transfer scope information but doesn't specify its meaning

##### Threat Model for OAuth
1. Threat Model - **Network Attacker**
2. Can't alter **any code / steal any information** on RO (Resource Owner), C (Client), RS (Resource Server)