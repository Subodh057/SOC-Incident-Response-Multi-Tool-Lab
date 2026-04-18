# Attack Timeline (Project 3)

## 🧠 Overview

This timeline represents the sequence of events during the SQL injection attack simulation.

---

## ⏱️ Timeline of Events

### 🟢 T1 — Baseline

* Normal HTTP traffic observed
* No suspicious input detected

---

### 🔵 T2 — Attack Initiation

* SQL injection request sent:

  * `id=1%20OR%201=1`
  * `id=1%20UNION%20SELECT%20username,password`

---

### 🔴 T3 — Logging

* Request recorded in server.log
* Payload stored in encoded form

---

### 🔵 T4 — Network Capture

* Wireshark captured HTTP request
* Encoded payload visible

---

### 🟣 T5 — Decoding & Analysis

* Splunk decoded request using `urldecode()`

---

### 🚨 T6 — Detection

* Regex rule triggered
* SQL injection identified

---

## 📊 Summary

Attack Flow:

Request → Log → Capture → Decode → Detect

---

## 🔑 Key Insight

The attack was not immediately visible due to encoding, but proper decoding and correlation enabled successful detection.

