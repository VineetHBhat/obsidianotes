
---
##### Multi-factor authentication
1. Passwords are no longer sufficient
2. 2FA vs MFA. Sometimes used as synonyms
3. 2FA
	1. Something you know (password)
	2. Something you have (smartphone or security key)
4. Search: `google titan` OR `yubico security key`
5. Second factor
	1. Smartphone
		1. OTP SMS
		2. OTP Authenticator app
		3. Push notifications
	2. Security key
		1. USB
		2. NFC
		3. Bluetooth
6. Security key is much more secure than other methods
7. Thread Model - Adversary has <U,P> (this means Username & Password) - Solved by all kinds of MFA
8. Threat Model - Evil Proxy for specialized AiTM - This is called Real-time Phishing - Solved only by Security Key MFA

##### One time passwords
1. TOPT - $OTP(t) = ENCRYPT_K(t - T_0)$  // $T_0$ conventional zero time
2. Read the clock & encrypt the result
3. Threat Model - Stolen password - Solved
4. Threat Model - Real-time Phishing - Not Solved if user doesn't detect & accesses wrong URL
5. Threat Model - Vishing (Voice phishing) - Not Solved
6. OTP doesn't solve phishing, it just makes is more costly
7. Other realistic & not solved threat models for OTP SMS:
	1. Malware on smartphone - Read, forward, delete SMS
	2. SIM swap (fraudulent SIM change) - Phone number fraudulently taken by another SIM
	3. SMS routing attacks - SS7 (Signaling System 7) phone protocol weakness: SMS sent to Attacker
8. OTP Auth App solves above Threat Models
	1. Malware on smartphone - Auth App does not grant any "screenshot rights" to any other app
	2. SIM swap & SMS routing - OTP do not travel across phone network
9. Move away from the SMS and voice Multi-Factor Authentication (MFA) mechanisms
10. OTP has privacy implications - Phone number is used as an identifier for linking identities across different marketing databases

##### Security keys
1. Must be close to the browser - USB/Bluetooth/NFC
2. Security keys contain DNS Name, Username, Private Key, Public key
3. TOFU - Trust on First Use - We trust the service for the first time, i.e. for the first time we are not sure about the authenticity of the service
4. FIDO & FIDO2 - Open Standards - Protocol
5. Threat Model
	1. Adversary has <U,P> - Solved
	2. Real-time phishing - Evil proxy DNS name mismatch - Security Key doesn't sign challenge - Solved
	3. Attacker has valid certificate for S name - Browser can't discriminate between real & fake service - Not solved
	4. Attacker has malware on Browser device - Malware can alter/forge Browser/Security key traffic - Not solved

##### Push notifications
1. Smartphone must be close to the user
2. Every service has its own App where it sends notifications
3. Threat Model
	1. Adversary has <U,P> - Solved
	2. Real-time phishing - Not solved
	3. MFA Bombing - Adversaries may continuously repeat login attempts in order to bombard users with MFA push notifications, SMS messages, and phone calls, potentially resulting in the user finally accepting the authentication request in response to "MFA fatigue."

2FA **does not defend** against attacks during an authenticated session. 2FA is checked only at the beginning of a session.
- Stealing of authentication cookie
- Pass-the-hash / Pass-the-ticket

##### Password-less login
1. Trusted-device
	1. User has activated 2FA on Service S
	2. User may declare a certain device D-K is trusted & authenticates using password only on D-K
	3. Device proves knowledge of private key to S
	4. User proves knowledge of password to S
2. Password-less device
	1. User authenticates from D-K without any password
	2. D-K must have built-in authenticator like fingerprint reader, face recognition
	3. User proves biometric property to device & **not Service**
	4. No risk of disclosing password from password-less device!
3. Passkeys
	1. "Passkey for S stored on D-K" 
	2. D-K is trusted and password-less for service S
	3. Passkey ≈ KPRIV-DK
	4. In certain cases, passkey can be migrated to other (trusted) devices
	5. Not phish-able
	6. Used for authentication
	7. Never leave the device while Cookies are transmitted in every request
	8. Consequence - Downgrade attack - User doesn't consider the login page as suspicious

---
##### Vulnerabilities
- Palo Alto firewall issue - Unauthenticated remote command injection