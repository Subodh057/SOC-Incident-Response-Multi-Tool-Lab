# Attack Timeline (Honeypot Lab)

## 🧠 Overview

This timeline represents the sequence of attacker interaction with the honeypot.

---

## ⏱️ Timeline of Events

### 🟢 T1 — Setup

* Honeypot service started on port 4444

---

### 🔵 T2 — Connection

* Attacker connected from Windows machine

---

### 🔴 T3 — Reconnaissance

* `whoami`
* `id`
* `uname -a`

---

### 🔵 T4 — Exploration

* `ls`
* `pwd`

---

### 🟣 T5 — Data Access

* `cat /etc/passwd`

---

### 🟡 T6 — Modification

* `echo "hacked" > test.txt`
* `mkdir hidden_folder`

---

### 🚨 T7 — Detection

* Commands identified using Splunk detection rules

---

## 📊 Summary

Attack Flow:

Connection → Recon → Exploration → Data Access → Persistence → Detection

---

## 🔑 Key Insight

The honeypot enabled full visibility of attacker interaction, allowing detailed reconstruction of behavior and intent.

