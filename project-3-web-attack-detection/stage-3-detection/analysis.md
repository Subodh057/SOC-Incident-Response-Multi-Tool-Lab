# Stage 3: Detection Engineering for Web Attacks

## Objective

To develop detection rules for identifying SQL injection attempts using Splunk.

## Identified Indicators

The simulated attack used URL-encoded SQL injection payloads, including:

* `id=1%20OR%201=1`
* `id=1%20UNION%20SELECT%20username,password`

After decoding, the payloads become:

* `id=1 OR 1=1`
* `id=1 UNION SELECT username,password`


## MITRE ATT&CK Mapping

* Tactic: Initial Access (TA0001)
* Technique: Exploit Public-Facing Application (T1190)
* Tactic: Collection (TA0009)
* Technique: Data from Information Repositories (T1213)

## Detection Rule

The most effective detection rule was:

```spl
index=main source="*server.log"
| eval decoded=urldecode(_raw)
| regex decoded="(?i)(or\s+1=1|union\s+select)"
| eval alert="SQL Injection Detected"
| table _time alert decoded _raw
```

## Detection Strategy

Detection was based on two steps:

1. Decode URL-encoded HTTP requests
2. Apply regex-based pattern matching to the decoded request

This approach was necessary because the original server logs stored the payload in encoded form.

## Analysis

Simple string matching failed because the attack payload was URL-encoded in the log source.

Detection became successful only after:

* transforming the request using `urldecode(_raw)`
* applying case-insensitive regex matching

This demonstrates the importance of preprocessing log data before writing detection logic.

## Conclusion

SQL injection attempts were successfully detected in Splunk using decoded request analysis and regex-based rules.

This stage shows that reliable web attack detection often depends on correctly handling encoded input before applying signatures or patterns.

## Key Learnings

* Encoded payloads can break simple detection rules
* Preprocessing logs is critical for accurate detection
* Regex-based detection is more flexible than raw string matching
* Web attack detection should focus on decoded request content

