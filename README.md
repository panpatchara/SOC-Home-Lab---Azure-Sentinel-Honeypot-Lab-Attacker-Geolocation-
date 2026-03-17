# SOC-Home-Lab---Azure-Sentinel-Honeypot-Lab-Attacker-Geolocation-

## 📌 Overview

This project simulates a real-world cyber attack scenario by deploying a publicly exposed Azure Virtual Machine as a honeypot to capture malicious login attempts.

Logs are collected and analyzed using Microsoft Sentinel to identify attacker behavior and visualize attack origins globally.

---

## 🧠 Objectives

* Deploy a honeypot VM exposed to the internet
* Capture real-world brute-force login attempts
* Analyze failed authentication events (Event ID 4625)
* Enrich attacker IPs with geolocation data
* Visualize global attack sources

---

## 🏗️ Architecture

* Azure Virtual Machine (Honeypot)
* Log Analytics Workspace
* Microsoft Sentinel (SIEM)
* Windows Event Logs

### Data Flow:

1. Attacker attempts login (RDP/SSH)
2. Event logs generated (Event ID 4625)
3. Logs ingested into Sentinel
4. KQL queries analyze attacker activity
5. IPs enriched with geolocation
6. Data visualized on attack map

![Architecture](architecture/honeypot-architecture.png)

---

## 🔍 Detection & Analysis

### KQL Query (Failed Logins)

```kql
SecurityEvent
| where EventID == 4625
| summarize count() by IpAddress, bin(TimeGenerated, 1h)
```

### Analysis Focus:

* Brute-force login attempts
* Repeated login failures
* Suspicious IP addresses

---

## 🌍 Geolocation & Visualization

* Extract attacker IP addresses
* Enrich with geographic data
* Display attack origins on map

![Attack Map](screenshots/attack-map.png)

---

## 🚨 Threat Insights

* High volume of brute-force attempts observed
* Attacks originate from multiple countries
* Common targeting of RDP services

---

## 📊 Tools & Technologies

* Microsoft Sentinel
* Azure Virtual Machine
* Log Analytics Workspace
* KQL (Kusto Query Language)

---

## 🧩 MITRE ATT&CK Mapping

* T1110 – Brute Force
* T1078 – Valid Accounts

---

## 📈 Key Skills Demonstrated

* SIEM monitoring and log analysis
* KQL query development
* Threat intelligence (IP geolocation)
* Attack pattern analysis
* Security monitoring in cloud environment

---

## 🚀 Future Improvements

* Integrate threat intelligence APIs (AbuseIPDB, VirusTotal)
* Add alerting rules in Sentinel
* Automate response (e.g., block IPs)
* Correlate with additional data sources

---

## 👤 Author

Panpatchara Naneplai
