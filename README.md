# 📊 Security Event Investigation & Access Analysis (SQL)
## Overview
This repository documents a comprehensive SQL-driven investigation into corporate security events and Identity Access Management (IAM) audits. By querying raw login_attempts and employees datasets, I reconstructed attack timelines, identified geographic anomalies, and mapped user-to-asset relationships. This framework provides SOC analysts with a systematic way to bridge the gap between raw database logs and actionable security insights.

## 🛠️ Technical Stack
**Language:**  SQL (Structured Query Language)

**Concepts:** Relational Joins (INNER, RIGHT, LEFT), Time-Series Filtering, Wildcard Pattern Matching (LIKE/NOT LIKE), Window Functions (ROW_NUMBER)

**Security Frameworks:** MITRE ATT&CK (T1078 - Valid Accounts, T1110 - Brute Force)

**Environment:** Relational Database (RDBMS)

## 🕵️ Investigation Modules
### 1. Temporal Anomaly Detection
**Focus:** Identifying "Out-of-Hours" and suspicious timing patterns.

**After-Hours & Early Morning Hunting:** Isolated failed logins occurring after 6:00 PM and before 7:00 AM. These are high-fidelity indicators of automated brute-force scripts or unauthorized insider activity.

**Incident Timeline Reconstruction:** Targeted specific dates (e.g., May 8-11, 2022) to correlate login behavior with known security alerts.

**Sequential Activity Ranking:** Utilized ROW_NUMBER() to visualize the chronological flow of login events, aiding in the discovery of rapid-fire authentication attempts.

### 2. Geographic & Positional Filtering
**Focus:** Geo-fencing and organizational scoping.

**Geographic Anomaly Detection:** Filtered records to identify login attempts originating outside of Mexico (NOT LIKE '%MEX%'), isolating potentially malicious foreign IP sources.

**Department-Specific Audits:** Used wildcard filtering to scope investigations to sensitive departments like Finance and Sales, or to exclude IT during broad security update rollouts.

**Building-Level Scoping:** Filtered employee lists by physical location (e.g., East Building) for targeted physical security audits or asset inventory.

### 3. Identity-to-Asset Correlation (Joins)
**Focus:** Mapping the "Who" to the "What."

**Endpoint Accountability:** Executed INNER JOINS between employees and machines tables to verify which user is assigned to which physical device ID.

**Authentication Auditing:** Combined employees with log_in_attempts to identify which users have active login histories versus those who have never successfully authenticated.

**Provisioning Gap Analysis:** Employed RIGHT JOINS to find employees without assigned machines, highlighting potential gaps in HR-to-IT system synchronization.

## 🔓 Key Query Snippets
## 🧠 Skills Demonstrated
**Advanced Data Filtering:** Proficient in BETWEEN, IN, and NOT LIKE for high-precision log analysis.

**Relational Database Logic:** Expert at joining disparate tables to create a "Single Source of Truth" during an investigation.

**SOC Workflow Integration:** Mapping SQL output directly to NIST and MITRE standards.

**Audit Readiness:** Creating clean, maintainable, and reproducible query documentation for compliance reviews.

### Final Conclusion
This framework demonstrates the ability to transform raw data into a well-rounded toolkit for access monitoring. By bridging the gap between database administration and security operations, these queries enable rapid incident triage, accurate asset management, and effective threat hunting.
