# Stage 1: Reconnaissance Analysis (Port Scanning)

## 🎯 Objective

To identify exposed services on the target system and analyze reconnaissance activity using network traffic inspection and IDS monitoring.

---

## ⚙️ Attack Simulation

A SYN-based port scan was performed against the target system:

nmap -sS 192.168.1.82

This type of scan is commonly used by attackers to stealthily discover open ports without completing full TCP handshakes.

---

## 🔍 Evidence Collected

### 🟢 Wireshark (Packet Analysis)

* Captured multiple TCP SYN packets
* Packets were sent to different destination ports
* No complete TCP handshake (SYN → SYN-ACK → ACK) observed

👉 This behavior indicates a **SYN (stealth) scan**

---

### 🔴 Snort (Intrusion Detection)

* Default Snort rules did not explicitly detect the port scan
* Custom rule was implemented to detect SYN packet patterns on loopback interface
* The custom rule successfully triggered during the scan

👉 This highlights:

* Limitations of default IDS rules
* Importance of rule tuning in detection engineering

---

### 🟡 Nmap Results (Scan Output)

The scan revealed the following open ports:

* **22/tcp → SSH**
* **80/tcp → HTTP**

👉 These services represent potential attack vectors for further exploitation.

---

## 🧠 Analysis

The observed SYN packets across multiple ports confirm that the system was subjected to a **reconnaissance scan**.

The attacker attempts to:

* Identify active services
* Map the attack surface
* Prepare for further exploitation (e.g., brute force or web attacks)

While Snort did not detect the scan using default rules, Wireshark provided clear packet-level evidence. Detection was achieved through a custom rule, demonstrating the need for IDS customization.

---

## 📌 Conclusion

A SYN-based port scan was successfully simulated and analyzed.

* Wireshark confirmed reconnaissance behavior through packet patterns
* Snort required custom rule tuning for detection
* Nmap identified exposed services (SSH and HTTP)

This stage represents the **initial phase of an attack lifecycle**, where attackers gather information before launching targeted attacks.

---

## 🔑 Key Learnings

* Not all reconnaissance activities are detected by default IDS configurations
* Packet-level analysis is critical for accurate detection
* Custom rule development enhances IDS effectiveness
* Multi-tool analysis provides a more complete security picture

