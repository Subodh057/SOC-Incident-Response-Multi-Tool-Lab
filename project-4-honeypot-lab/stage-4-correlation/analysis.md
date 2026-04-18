# Stage 4: Correlation & Incident Timeline Analysis (Honeypot)

## 🎯 Objective

To correlate captured data from multiple sources and reconstruct the attacker interaction timeline.

---

## 🧠 Overview

Data from different tools was analyzed to understand the attacker behavior:

* Honeypot logs (`honeypot.log`)
* Network traffic (Wireshark)
* Detection results (Splunk)

---

## ⏱️ Attack Timeline

| Time | Event                                             |
| ---- | ------------------------------------------------- |
| T1   | Honeypot service started on port 4444             |
| T2   | Attacker connected from Windows machine           |
| T3   | Recon commands executed (`whoami`, `id`, `uname`) |
| T4   | System exploration (`ls`, `pwd`)                  |
| T5   | Sensitive file accessed (`cat /etc/passwd`)       |
| T6   | Suspicious modifications (`echo`, `mkdir`)        |
| T7   | Commands recorded in honeypot.log                 |
| T8   | Detection rules triggered in Splunk               |

---

## 🔍 Correlation Analysis

### 🟢 Connection Evidence

* TCP session established between attacker and honeypot

---

### 🔵 Interaction Evidence

* Commands captured in honeypot.log
* Sequential attacker workflow observed

---

### 🔴 Detection Evidence

* Behavior classified using Splunk rules
* Alerts generated based on activity type

---

## 🧠 Analysis

The attack demonstrates a typical post-compromise workflow:

Reconnaissance → Exploration → Data Access → Persistence

The honeypot successfully captured the full interaction without providing real system access.

Correlation across multiple tools validated the attack and improved detection confidence.

---

## 📌 Key Insight

Interactive honeypots provide deeper visibility into attacker behavior compared to traditional log-based monitoring.

---

## 📌 Conclusion

The attacker interaction was successfully reconstructed and analyzed.

* Full attack lifecycle identified
* Detection validated through correlation
* Behavior-based detection proved effective

---

## 🔑 Key Learnings

* Correlation is essential for accurate incident analysis
* Honeypots capture valuable attacker behavior
* Multiple data sources improve detection accuracy
* Behavioral analysis provides deeper insight than static logs

