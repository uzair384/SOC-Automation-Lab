# SOC-Automation-Lab
End-to-end SOC automation lab integrating Windows 10 + Sysmon, Wazuh SIEM, TheHive, and Shuffle.io. Detects Mimikatz activity, enriches alerts with SHA-256/VirusTotal lookups, auto-creates incidents in TheHive, and sends email notifications—demonstrating real-world blue-team detection and response.

# SOC Automation Lab

A fully automated Security Operations Center (SOC) lab showcasing end-to-end detection, enrichment, and incident response.

## Overview
This project demonstrates how to integrate **Wazuh**, **TheHive**, and **Shuffle.io** to detect malicious activity, enrich threat data, create cases automatically, and notify analysts.

## Architecture
- **Windows 10 VM + Sysmon** – Generates rich Windows event logs.
- **Wazuh Server (Ubuntu 22.04)** – Collects logs, applies custom rules, and raises alerts.
- **TheHive Server (Ubuntu 22.04)** – Manages incidents and cases.
- **Shuffle.io** – Automates hash lookups, case creation, and email notifications.

## Key Features
- Custom Wazuh rules to detect Mimikatz credential-dumping activity.
- Automatic SHA-256 extraction and VirusTotal reputation checks.
- Automated case creation in TheHive via API key authentication.
- Email alerting to SOC administrators.

## Setup Summary
1. Provision two DigitalOcean droplets (Wazuh and TheHive) and configure firewall rules.
2. Install and configure Wazuh Manager, Indexer, and Dashboard.
3. Install Java, Elasticsearch, Cassandra, and TheHive.
4. Enable Sysmon on a Windows 10 VM and configure Wazuh’s `ossec.conf` and `filebeat.yml`.
5. Create custom Wazuh rules for Mimikatz detection.
6. Build a Shuffle workflow:
   - SHA-256 extraction
   - VirusTotal lookup
   - TheHive case creation
   - Email alert

## Usage
- Execute a test with Mimikatz or similar Sysmon-logged activity.
- Wazuh captures the event and triggers the Shuffle workflow.
- The workflow enriches the alert, opens a case in TheHive, and emails the SOC analyst.

