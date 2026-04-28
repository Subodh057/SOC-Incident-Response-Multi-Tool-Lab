🛡️ Incident Analysis Report (SOC)

1. What is happening

A SSH brute force attack was performed against the target system.

* Multiple failed login attempts observed
* High-frequency authentication requests in short time
* Single user account targeted repeatedly

⸻

2. Type of attack

* Classification: Credential Access / Brute Force
* Attacker intent:
    * Guess valid credentials
    * Gain unauthorized SSH access
    * Establish initial foothold

⸻

3. Severity level: HIGH

* Direct attempt to compromise authentication
* Repeated targeting of a specific account
* High likelihood of account takeover if successful

⸻

4. Evidence summary

* Log Analysis (SIEM):
    * Multiple “Failed password” entries
    * Same user and source IP repeated
    * Clear brute force pattern
* Network Analysis:
    * Repeated TCP connections to port 22
    * High traffic volume in short duration
* IDS Observation:
    * No alert triggered by default rules
    * Indicates limitation in detecting authentication-layer attacks

⸻

5. Recommended actions

1. Temporarily block or rate-limit source IP
2. Enforce strong password policy
3. Enable account lockout after failed attempts
4. Implement multi-factor authentication (MFA)
5. Monitor authentication logs for similar patterns
6. Tune IDS/SIEM rules for brute force detection

⸻

6. MITRE ATT&CK Mapping

* Tactic: Credential Access (TA0006)
* Technique: Brute Force (T1110)

Explanation:
This activity maps to T1110, where attackers attempt multiple password combinations to gain access to user accounts, commonly targeting services like SSH.

⸻

🔍 Summary

This incident represents a credential access attack via brute force, where the attacker attempts to gain unauthorized access through repeated login attempts. Detection was most effective at the log level, emphasizing the importance of SIEM-based monitoring