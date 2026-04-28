⸻

🛡️ Incident Analysis Report (SOC)

1. What is happening

A SYN-based port scan (stealth scan) was performed against the target system.

* Multiple TCP SYN packets sent across different ports
* No full TCP handshake completed
* Behavior indicates reconnaissance activity to identify open services

⸻

2. Type of attack

* Classification: Reconnaissance / Port Scanning
* Attacker intent:
    * Discover exposed services
    * Map attack surface
    * Identify entry points for exploitation

⸻

3. Severity level: MEDIUM → HIGH

* Reconnaissance is an early attack phase
* Open services (SSH, HTTP) increase risk
* Detection required custom tuning → indicates potential monitoring gaps

⸻

4. Evidence summary

* Packet Analysis:
    SYN packets observed without full handshake → stealth scan behavior
* IDS Detection:
    Default rules did not detect scan
    Custom rule successfully triggered → highlights detection engineering importance
* Scan Results:
    * 22/tcp → SSH
    * 80/tcp → HTTP

⸻

5. Recommended actions

1. Monitor and rate-limit suspicious scanning activity
2. Harden exposed services (SSH, HTTP)
3. Implement stronger IDS rules for reconnaissance detection
4. Correlate logs across network and host-level monitoring
5. Track source IP behavior for repeated scanning attempts

⸻

6. MITRE ATT&CK Mapping

* Tactic: Reconnaissance (TA0043)
* Technique: Network Service Discovery (T1046)

Explanation:
The SYN scan aligns with T1046, where attackers probe network services to identify open ports and running applications before launching targeted attacks.

⸻

🔍 Summary

This activity represents the reconnaissance phase of an attack lifecycle, where the attacker is gathering information about exposed services. Detection required custom tuning, highlighting the importance of adaptive IDS strategies