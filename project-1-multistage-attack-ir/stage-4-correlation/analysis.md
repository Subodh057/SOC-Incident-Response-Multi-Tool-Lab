# Stage 4: Incident Correlation & Attack Timeline Analysis

## 🎯 Objective

To correlate all stages of the simulated attack and construct a complete attack timeline using evidence from multiple tools.

---

## 🧠 Attack Overview

The attack was conducted in a controlled lab environment using two devices within the same local network:

* Attacker Machine: Mac
* Target Machine: Ubuntu Laptop (192.168.1.82)

The attack followed a multi-stage progression from reconnaissance to post-exploitation activity.

---

## 🔗 Attack Chain

### 1. Reconnaissance (Stage 1)

* SYN-based port scan performed using Nmap
* Open ports identified: 22 (SSH), 80 (HTTP)
* Wireshark confirmed scanning behavior

---

### 2. Brute Force Attack (Stage 2)

* Hydra used to perform SSH brute force attack
* Multiple failed login attempts recorded in `auth.log`
* Splunk analysis confirmed repeated authentication failures

---

### 3. Initial Access (Stage 3)

* Successful SSH login established
* Session opened for user `subodh-awasthi`
* Access gained from attacker machine within same network

---

### 4. Post-Exploitation Activity (Stage 3)

* System enumeration performed (`whoami`, `id`, `uname -a`)
* Sensitive file accessed (`/etc/passwd`)
* Privilege escalation attempts (`sudo -l`)
* Suspicious file created (`/tmp/backdoor.sh`)

---

## 🕒 Attack Timeline

| Time | Activity                              |
| ---- | ------------------------------------- |
| T1   | Port scanning activity detected       |
| T2   | Multiple failed SSH login attempts    |
| T3   | Successful SSH authentication         |
| T4   | Execution of reconnaissance commands  |
| T5   | Persistence attempt via file creation |

---

## 🔍 Tool Correlation

| Tool      | Role                                           |
| --------- | ---------------------------------------------- |
| Wireshark | Network-level traffic analysis                 |
| Snort     | Limited IDS detection                          |
| auth.log  | Primary evidence of authentication activity    |
| Splunk    | Log analysis and attack pattern identification |

---

## 🧠 Analysis

The attack demonstrates a typical multi-stage intrusion:

1. Information gathering (Recon)
2. Credential attack (Brute Force)
3. Unauthorized access
4. System exploration and persistence

The correlation of logs and network data provides a complete view of attacker behavior across different stages.

---

## 📌 Conclusion

A complete attack lifecycle was successfully simulated and analyzed.

* Each stage of the attack was identified and correlated
* Logs and network data were combined to build a full incident timeline
* The project demonstrates real-world SOC investigation workflow

This highlights the importance of multi-layered monitoring and correlation in detecting and understanding cyber attacks.

---

## 🔑 Key Learnings

* Attacks occur in multiple stages, not isolated events
* Correlation of tools provides deeper visibility
* Log analysis is critical for detecting authentication attacks
* Network analysis supports but does not replace log-based detection
* Understanding attack flow is essential for effective incident response

