# Stage 2: SQL Injection Attack Simulation

## 🎯 Objective

To simulate SQL injection attacks and analyze their visibility across network and log sources.

---

## ⚙️ Attack Simulation

Malicious HTTP requests were generated using curl:

* `id=1 OR 1=1`
* `id=1 UNION SELECT username,password`
* `id=1--`

---

## 🔍 Observations

### 🟢 Server Logs

* Injection payloads recorded in `server.log`
* Full query parameters visible

---

### 🔵 Splunk Analysis

* Logs ingested into Splunk
* SQL injection patterns successfully detected using queries

---

### 🟡 Network Traffic (Wireshark)

* HTTP requests captured
* Injection payloads clearly visible in packets

---

## 🧠 Analysis

The attack payloads were clearly visible due to unencrypted HTTP traffic.

Both network-level and log-level analysis confirmed the presence of malicious input.

---

## 📌 Conclusion

SQL injection attacks were successfully simulated and detected using multiple tools.

---

## 🔑 Key Learnings

* HTTP allows full visibility of attack payloads
* Logs provide structured detection capability
* SQL injection can be identified through simple pattern matching

