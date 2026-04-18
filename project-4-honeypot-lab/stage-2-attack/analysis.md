# Stage 2: Attacker Interaction Simulation (Honeypot)

## 🎯 Objective

To simulate realistic attacker behavior from a separate machine and capture interaction using a honeypot service.

---

## ⚙️ Attack Setup

* Honeypot deployed on a Linux system using Netcat on port 4444
* Attacker machine: Windows laptop on the same network
* Connection established using Netcat from attacker to target system

---

## 🔍 Attack Simulation

The attacker connected to the honeypot service and executed a sequence of commands mimicking post-compromise behavior:

### 🔴 Reconnaissance

* `whoami`
* `id`
* `uname -a`

---

### 🔵 System Exploration

* `ls`
* `pwd`
* `cd /tmp`

---

### 🟣 Sensitive Data Access

* `cat /etc/passwd`

---

### 🟡 Suspicious Actions

* `echo "hacked" > test.txt`
* `mkdir hidden_folder`

---

## 🔍 Observations

### 🟢 Captured Interaction (honeypot.log) in terminal and Splunk.

* All attacker commands were successfully recorded
* Sequential execution pattern observed

---

### 🔵 Network Activity (Wireshark)

* TCP connection established between two devices
* Source IP: attacker (Windows system)
* Destination IP: honeypot (Linux system)
* Full session visible via TCP stream

---

## 🧠 Analysis

The captured behavior closely resembles a real attacker workflow:

Reconnaissance → Exploration → Data Access → Persistence

The use of two separate machines enhanced realism, demonstrating actual network-based attack interaction.

The honeypot effectively captured attacker input without providing a real service, acting as a controlled monitoring environment.

---

## 📌 Key Insight

Honeypots can capture detailed attacker behavior even without implementing a full service, making them valuable for behavioral analysis and threat intelligence.

---

## 📌 Conclusion

The attack simulation was successfully executed and captured using a honeypot setup.

* Real network interaction was achieved
* Attacker commands were logged accurately
* Network traffic confirmed the connection

---

## 🔑 Key Learnings

* Honeypots provide visibility into attacker behavior
* Cross-platform attack simulation increases realism
* Network-level and interaction-level data complement each other
* Behavioral analysis is crucial for understanding attacker intent

