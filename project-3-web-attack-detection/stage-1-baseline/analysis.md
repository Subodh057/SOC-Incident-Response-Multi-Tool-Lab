# Stage 1: Baseline Web Traffic Analysis with Splunk Integration

## 🎯 Objective

To establish normal web traffic behavior and integrate server logs into Splunk for analysis.

---

## ⚙️ Setup

* Python HTTP server deployed on port 8000
* Server logs redirected to `server.log`
* Logs ingested into Splunk
* Traffic generated using curl and browser

---

## 🔍 Observations

### 🟢 Server Logs

* HTTP GET requests recorded in `server.log`
* Normal requests with status code 200

---

### 🔵 Splunk Analysis

* Logs successfully ingested into Splunk
* Queries displayed HTTP request entries
* No abnormal query parameters observed

---

### 🟡 Network Traffic (Wireshark)

* HTTP GET requests observed
* No suspicious patterns detected

---

## 🧠 Analysis

The system exhibits normal web traffic behavior.

Requests are simple and do not contain malicious input.

Splunk successfully centralizes log data, providing structured visibility into web activity.

---

## 📌 Conclusion

Baseline web traffic has been successfully established and monitored using both network and log analysis tools.

---

## 🔑 Key Learnings

* Splunk requires proper log sources for meaningful analysis
* Server logs provide visibility into HTTP requests
* Baseline behavior is essential before detecting web attacks

