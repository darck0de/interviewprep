# SQL injection

## What is SQL injection

- Allows an attacker to interfere with the queries that an application makes to its database
- untrusted data is sent to an interpreter as part of a command or query

## Impact

- Read \ Write \ DELETE data
- DOS
- compromise the underlying server

## Mitigation

- parameterized queries (also known as prepared statements) instead of string concatenation within the query.
- stored procedures
- whitelisting / input validation
- least priviledge
- database hardening
- WAF

## Types

- In-band SQLi
    - Error Based
    - Union Based
- Inferential (Blind) SQLi
    - Boolean Based
    - Time-Based
- Out of Band

## How to detect

- Submitting the single quote character ' and looking for errors or other anomalies.
- Submitting Boolean conditions such as OR 1=1 and OR 1=2, and looking for differences in the application's responses.
- time delays when executed within an SQL query, and looking for differences in the time taken to respond.
---

# Broken Authentication

- Account registration attacks
- Account password reset attacks
- Weak Username and password - Brute force attacks
- Defautl creds attacks
- Session related attacks

## Imact
- Account takeover
- Access to sensitive data

## Mitigation
- Session 
	- timeout, non guessable session, new session post login
- Creds
	- remove defaults, 2FA, strong password policy, account lockout
- Two channels to share creds (mail/mobile)
---
# Sensitive Data Exposure

- man-in-the-middle
- steal keys
- not encrypting sensitive data
- weak key generation and management
- weak algorithm, protocol and cipher usage

## Impact
- EU-GDPR, HIPAA, PCI, Affects Brand Image(Goodwill) 

## Mitigation

- Data at rest
	- Full disk encryption or device
	- File-level encryption
	- Database Encryption (Transparent Data Encryption)
	- MDM (Mobile Device Management)
- Data in Transit
	- Email encryption using PKI (Public Key Infrastructure)
	- Managed File Transfer (MFT)
	- DLP (Data Leak Prevention)
	- TLS v 1.3 (Data in transit) with strong ciphers
- Data in Use
	- Identity management tools (2FA)
	- Conditional Access or Role Based Access Control (RBAC)
	- Masking
---
# XXE (XML External Entities)
Many older or poorly configured XML processors evaluate external entity references within XML documents

## Reason for XXE 

- SOAP based web services has **document type definitions (DTDs) enabled**
- SOAP prior to version 1.2
- SAML uses XML for identity assertions, and may be vulnerable.

## Impact
- LFI
- port scanning
- remote code execution
- Denial of service attacks (Billion Laughs attack)

## Mitigation
- Use JSON than XML
- Disable XML external entity and DTD processing in all XML parsers in the application
- Upgrade all XML processors and libraries in use (SOAP 1.2 or higher)
- whitelisting
- XSD validation
- WAF
---
# Broken Access Control
The authorization includes the execution rules that determine which functionality and data the user (or Principal) may access, ensuring the proper allocation of access rights after authentication is successful.

## Reason behind BAC
- Server side validation missing
- Role based access missing
- Missing of Tokens like JWT, CSRF

## Impact
- Privilege Escalation
- Account Takeover
- Affects CIA


## Mitigation
- Role-Based Access Control (RBAC)
	- Segregation of duties
	- least privileges
	- deny by default
- Rate Limiting
- Disable directory listing
- JWT tokens should be invalidated on the server after logout.

- Discretionary Access Control (DAC)
	- The owner of the information or any resource can change its permissions at their discretion (thus the name).
- Permission Based Access Control
	- "READ", "WRITE" and "DELETE"; "START", "STOP", and "REBOOT".
---
## Security Misconfiguration

## Reason
- insecure default configurations
- misconfigured HTTP headers
- verbose error messages containing sensitive information
- unnecessary services

## Impact
- complete system compromise

## Mitigation
- security hardening
- Custom error handling
- disable nnecessary ports, services
- delete default users
- change default settings
- Apply patches regularly
---
# XSS

## What is XSS
- a client-side code injection attack, it uses unsanitized user input in the output that it generates
## Impact
- cookie stealing, CSRF, phishing, website defacement
## Mitigation
- sanitize your input, Use escaping/encoding, httponly, Content Security Policy, HtmlSanitizer like library if html code need to present in output
## Types
- 1. Stored - Server side, stored in DB, impact wide, mitigation as above
- 2. Reflected - Client Side, usually GET request, impact limited, mitigation as above
- 3. DOM - Client Side, exploited in browser's DOM, Avoid methods such as document.innerHTML, document.url, document.location, document.referrer

---
# Insecure Deserialization

## Impact
- remote code execution attacks

## Mitigation
- not to accept serialized objects from untrusted sources
- integrity checks - digital signatures
---
# Using Components with Known Vulnerabilities

## Reason
- outdated and vulnerable libraries, frameworks, application servers, database technologies

## Impact
- RCE

## Mitigation
- Use retire.js to scan application for known vulnerabilities
- Know your versions of libraries, components and track CVE and NVD regularly
---
# Insufficient Logging & Monitoring

## Mitigation
- log Auditable events, such as logins, failed logins, access control failures, and high-value transactions
- logs should be generated in a format that can be easily consumed by a centralized log management solutions
- Establish effective monitoring and alerting
---
