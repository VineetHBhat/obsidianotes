
---
##### Open ID Connect
1. Identity linking
2. Log in on a site to authenticate on another site
3. Credentials are not shared with the service provider
4. `UserInfo` resource specified by OIDC. It has following attributes (*key-value* pairs)
	1. `Sub` - User identifier
	2. `Name` - User full name in displayable form
	3. `Email` - Preferred email
5. 3 key differences to OAuth
	1. Delegation $\equiv$ Login
	2. Authorization Grant lasts for a few seconds (User has authenticated now)
	3. Authorization code -> Refresh Token + ID Token containing `UserInfo`
6. `UserInfo` (claims) is actually contained within an `IDToken`
7. OIDC specifies
	1. Mandatory claims
	2. Optional claims
	3. Few claims
		1. `iss` - issuer
		2. `sub` - subject
		3. `aud` - audience
		4. `nonce` - one use
		5. `auth_time`
	4. Mandatory signature
	5. Optional encryption

##### CSRF or XSRF
1. Cross site request forgery
2. Prevention - Synchronizer Token as specified by OWASP
3. `SameSite` cookie - Enabled in browsers by default