Practical – Web Discovery Attack

## Scenario
- Joined FakeBank’s SOC team to investigate a SIEM alert.

## Alert Details
- Attack Type: Web Discovery Attack
- Method: Automated Directory Enumeration
- Target: Admin Panels
- Risk Level: Medium
- Source IP: 32.122.195.63
- Reputation: Malicious
- Previous Attacks: 47 incidents

## Attack Identification
- Attempted URLs: /admin, /administrator, /wp-admin, /login
- 404 and 403 responses confirmed automated scanning.

## Actions Taken
- Blocked source IP for 24 hours.
- Implemented rate limiting.
- Updated WAF rules.

## Key Takeaways
- Understanding web attacks.
- Investigating SIEM alerts.
- Applying defensive controls in a SOC.
