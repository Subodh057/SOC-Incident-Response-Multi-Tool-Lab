# Stage 3: Detection Engineering for Honeypot Interaction

## 🎯 Objective

To develop detection rules based on attacker behavior captured by the honeypot.

---

## 🚨 Identified Indicators

The following attacker behaviors were observed:

### 🔴 Reconnaissance

* whoami (T1033 – System Owner Discovery)
*  id (T1033 → System Owner/User Discovery)
* uname -a (T1082 → System Information Discovery)

---

### 🔵 Exploration

* `ls`, `pwd`, directory navigation

---

### 🟣 Sensitive Data Access

* `cat /etc/passwd`

---

### 🟡 Suspicious Actions

* File creation (`echo`)
* Directory creation (`mkdir`)

---

## 🔍 Detection Rules

### 🔥 Recon Activity

```spl id="h7b2v3"
index=main source="*honeypot.log" ("whoami" OR "id" OR "uname")
```

---

### 🔥 Sensitive File Access

```spl id="o3t7n9"
index=main source="*honeypot.log" "cat /etc/passwd"
```

---

### 🔥 Suspicious Modification

```spl id="g8x4m2"
index=main source="*honeypot.log" ("echo" OR "mkdir")
```

---

### 💣 Combined Detection Rule

```spl id="f9w2k1"
index=main source="*honeypot.log" ("whoami" OR "id" OR "uname" OR "cat /etc/passwd" OR "echo" OR "mkdir")
```

---

### 🚨 Alert Classification

```spl id="p6l3q8"
index=main source="*honeypot.log"
| eval alert=case(
    match(_raw,"whoami|id|uname"),"Recon Activity",
    match(_raw,"cat /etc/passwd"),"Sensitive File Access",
    match(_raw,"echo|mkdir"),"Suspicious Modification"
)
| table _time alert _raw
```

---

## 🧠 Detection Strategy

Detection is based on identifying attacker behavior patterns rather than specific tools or identities.

Commands were categorized into different stages of attacker activity.

---

## 📊 Analysis

* Multiple behaviors indicate post-compromise activity
* Sequential commands increase confidence of malicious intent
* Classification improves understanding of attacker workflow

---

## 📌 Key Insight

Behavior-based detection is more effective than signature-based detection in interactive attack scenarios.

---

## 📌 Conclusion

Attacker behavior was successfully transformed into detection rules.

* Behavioral patterns identified
* Detection rules implemented in Splunk
* Alert classification enhances analysis

---

## 🔑 Key Learnings

* Honeypots provide rich behavioral data
* Detection should focus on actions, not identities
* Classification improves detection clarity
* SIEM tools can transform raw logs into actionable insights

