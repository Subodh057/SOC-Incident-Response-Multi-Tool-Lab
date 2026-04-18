# Detection Rules (Honeypot Lab)

## 🧠 Overview

This file contains detection rules developed to identify attacker behavior captured by the honeypot.

---

## 🔴 Rule 1: Reconnaissance Detection

### Description

Detects basic system reconnaissance commands executed by an attacker.

### Query

```spl
index=main source="*honeypot.log" ("whoami" OR "id" OR "uname")
```

### Behavior Detected

* User identification
* System information gathering

---

## 🔵 Rule 2: Exploration Activity Detection

### Description

Detects directory and file system exploration commands.

### Query

```spl
index=main source="*honeypot.log" ("ls" OR "pwd" OR "cd")
```

### Behavior Detected

* File system navigation
* Directory listing

---

## 🟣 Rule 3: Sensitive Data Access

### Description

Detects attempts to access sensitive system files.

### Query

```spl
index=main source="*honeypot.log" "cat /etc/passwd"
```

### Behavior Detected

* Credential harvesting attempts

---

## 🟡 Rule 4: Suspicious Modification Activity

### Description

Detects file and directory creation activities.

### Query

```spl
index=main source="*honeypot.log" ("echo" OR "mkdir")
```

### Behavior Detected

* File creation
* Persistence setup

---

## 💣 Rule 5: Combined Behavioral Detection

### Description

Detects multiple suspicious activities indicating attacker behavior.

### Query

```spl
index=main source="*honeypot.log" ("whoami" OR "id" OR "uname" OR "cat /etc/passwd" OR "echo" OR "mkdir")
```

### Behavior Detected

* Multi-stage attacker workflow
* Post-compromise activity

---

## 🚨 Rule 6: Alert Classification Rule

### Description

Classifies detected activity into categories for better analysis.

### Query

```spl
index=main source="*honeypot.log"
| eval alert=case(
    match(_raw,"whoami|id|uname"),"Recon Activity",
    match(_raw,"cat /etc/passwd"),"Sensitive File Access",
    match(_raw,"echo|mkdir"),"Suspicious Modification"
)
| table _time alert _raw
```

### Behavior Detected

* Categorized attacker activity
* Structured alert output

---

## 🧠 Key Insight

Detection rules are based on behavioral patterns rather than specific attacker identity or tools.

---

## 📌 Conclusion

These rules provide a structured approach to detecting and classifying attacker behavior in a honeypot environment.

