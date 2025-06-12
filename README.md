

# 🕵️‍♂️ Suspicious Activity Detection & Visualization Pipeline

## 🚀 Overview  
This project demonstrates a full detection pipeline that:

- Queries **Splunk logs via API** for specific Windows Event IDs (1, 3, 10, 11, 4624, 4625)  
- Applies custom **signatures** to detect suspicious behaviour (e.g., failed logins, PowerShell execution)  
- Enriches matches with **VirusTotal** (e.g., country, reputation, etc.)  
- Forwards the enriched data to **Elasticsearch (ELK stack)** for **visualisation in Kibana**

---

## 🛠️ Tools & Technologies  
- **Python** 🐍  
- **Splunk REST API** 🔎  
- **VirusTotal Public API** 🧪  
- **ELK Stack (Elasticsearch + Kibana)** 📊  
- **MITRE ATT&CK T1059.001 (PowerShell Execution)** ☠️

---

## 🔄 Workflow Diagram

        +---------------------+
        |   Splunk Server     |
        |   (Port 8089)       |
        +----------+----------+
                   |
                   v
        +----------+----------+
        |   Python Script     |
        | (Query + Detection) |
        +----------+----------+
                   |
                   v
        +----------+----------+
        | VirusTotal API      |
        |  (Log Enrichment)   |
        +----------+----------+
                   |
                   v
        +----------+----------+
        | Elasticsearch (ELK) |
        | (Log Ingestion)     |
        +----------+----------+
                   |
                   v
        +---------------------+
        |   Kibana Dashboard  |
        | (Visualisation View)|
        +---------------------+

---

## ⚡ Event IDs Queried
- `1` – Process creation  
- `3` – Network connection  
- `10` – WMI activity  
- `11` – File creation  
- `4624` – Successful logon  
- `4625` – Failed logon  

---

## 💡 Notable Features
- Host-only adapter configuration to allow host-to-VM Splunk API access  
- Automatically detects when Splunk query jobs are complete (via SID polling)  
- Dynamically parses logs and flags potential threats  
- Enriched logs include country origin, detection ratio, and malware classification  
- Logs are pushed live into Kibana with real-time visibility  

---

## 🎯 MITRE Detection Use Case

This project includes simulation of suspicious PowerShell activity:

- **T1059.001** – PowerShell command execution via Atomic Red Team  
- Logs are caught and flagged using custom detection logic  

---

## 🎥 Demo Preview  
> *Watch the full breakdown [here](https://www.linkedin.com/posts/silas-cybersec_cybersecurity-blueteam-soc-activity-7338914679345299456-Bsi0?utm_source=share&utm_medium=member_android&rcm=ACoAAFHCqjQBCBsazDmLmi-A3AQpYFgkGfGXLrs)*  
Includes live trigger tests, detection signatures, enrichment preview, and dashboard in action!

---

## 🙌 Wanna Build Something Similar?

Feel free to reach out if you're planning to build something along these lines — happy to connect and collaborate!
