# Stage 2: SSH Brute Force Attack Analysis

## 🎯 Objective

To simulate and detect a brute force attack targeting SSH authentication using log analysis and network monitoring tools.

---

## ⚙️ Attack Simulation

A brute force attack was performed using Hydra:

hydra -l subodh-awasthi -P passwords.txt ssh://192.168.1.82

This attack attempts multiple password combinations to gain unauthorized access to the SSH service.

---

## 🔍 Evidence Collected

### 🔵 Splunk (Primary Detection)

Authentication logs (`auth.log`) were imported into Splunk for analysis.

Observations:

* Multiple "Failed password" entries detected
* High frequency of login attempts within a short time
* Same user (`subodh-awasthi`) targeted repeatedly
* Same source IP (`192.168.1.82`) observed across attempts

👉 This clearly indicates brute force behavior.

---

### 🟢 Wireshark (Network Evidence)

* Captured repeated TCP connections to port 22 (SSH)
* High volume of packets in a short time frame
* Multiple connection attempts without successful authentication

👉 Confirms network-level brute force activity.

---

### 🔴 Snort (IDS Observation)

* Default Snort rules did not generate specific alerts for the brute force activity
* Highlights limitation of IDS in detecting application-layer authentication attacks

---

## 🧠 Analysis

The repeated failed login attempts observed in authentication logs confirm a brute force attack pattern.

The attacker systematically attempted multiple passwords against a single user account in rapid succession.

Splunk proved to be the most effective detection tool in this stage, as it directly analyzes authentication logs where such attacks are recorded.

Wireshark provided supporting evidence at the network level, while Snort showed limited visibility due to its focus on network signatures rather than authentication events.

---

## 📌 Conclusion

The system experienced a simulated SSH brute force attack.

* Splunk successfully identified the attack through log analysis
* Wireshark confirmed repeated SSH connection attempts
* Snort did not detect the attack, highlighting detection limitations

This stage demonstrates the importance of log-based monitoring (SIEM) for detecting authentication attacks.

---

## 🔑 Key Learnings

* Brute force attacks are best detected through log analysis rather than network IDS
* SIEM tools like Splunk provide critical visibility into authentication events
* IDS tools may not detect application-layer attacks without proper rule tuning
* Multi-tool correlation enhances detection accuracy

