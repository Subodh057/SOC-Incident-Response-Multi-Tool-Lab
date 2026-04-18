# Stage 1: Honeypot Setup & Baseline Interaction

## 🎯 Objective

To deploy a simple honeypot service and capture basic interaction.

---

## ⚙️ Setup

* Netcat used to open port 4444
* Incoming data redirected to `honeypot.log`
* Local connection used for baseline testing

---

## 🔍 Observations

### 🟢 Connection

* TCP connection successfully established

---

### 🔵 Captured Data

* Basic input messages recorded:

  * hello i am attacker
  

---

### 🟡 Network Activity

* TCP packets observed on port 4444
* Data transfer visible in Wireshark

---

## 🧠 Analysis

The honeypot successfully captured incoming interaction.

At this stage, only normal (non-malicious) input was observed.

This baseline will be used to compare against attacker behavior in later stages.

---

## 📌 Conclusion

Honeypot setup is functioning correctly and capable of capturing interaction data.

---

## 🔑 Key Learning

* Honeypots rely on open ports to attract connections
* Interaction logging provides visibility into user behavior
* Baseline behavior is necessary before analyzing attacks

