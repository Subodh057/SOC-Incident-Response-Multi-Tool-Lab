# Stage 4: Correlation & Timeline Analysis

## 🎯 Objective

To correlate evidence from multiple sources and reconstruct the SQL injection attack lifecycle.

---

## 🧠 Overview

Data from different tools was analyzed to understand the complete attack flow.

Sources used:

* Wireshark (network traffic)
* Server logs (`server.log`)
* Splunk (log analysis and detection)

---

## ⏱️ Attack Timeline

| Time | Event                                                   |
| ---- | ------------------------------------------------------- |
| T1   | Normal web traffic baseline established                 |
| T2   | Malicious HTTP request sent (URL-encoded SQL injection) |
| T3   | Request recorded in server.log                          |
| T4   | HTTP packet captured in Wireshark                       |
| T5   | Request decoded in Splunk using `urldecode()`           |
| T6   | Regex-based rule triggered → SQL Injection detected     |

---

## 🔍 Correlation Analysis

### 🟢 Network Evidence (Wireshark)

* HTTP request captured
* Encoded payload visible

---

### 🔵 Log Evidence (server.log)

* Full request recorded
* Includes encoded injection payload

---

### 🔴 Detection Evidence (Splunk)

* Request decoded
* SQL injection pattern identified using regex
* Alert generated

---

## 🧠 Analysis

The attack was successfully detected by correlating:

* Network-level visibility
* Server-side logging
* SIEM-based detection

Although the payload was URL-encoded, decoding allowed accurate identification of malicious input.

---

## 📌 Key Insight

Encoded inputs can bypass simple detection rules. Proper preprocessing (decoding) is required before applying detection logic.

---

## 📌 Conclusion

The SQL injection attack was successfully reconstructed and detected through multi-source correlation.

* Attack lifecycle clearly identified
* Detection validated across tools
* Behavior-based detection proved effective

---

## 🔑 Key Learnings

* Correlation improves detection accuracy
* Logs and network data complement each other
* Encoded payloads require preprocessing
* SIEM tools depend on correct data transformation

