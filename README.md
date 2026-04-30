# 🔍 Phishing Email Investigation (SOC L1 Project)

## 📌 Overview
This project simulates a real-world phishing attack investigation performed by a SOC L1 analyst.

## 🎯 Objectives
- Identify phishing indicators
- Analyze malicious URLs and attachments
- Correlate logs across multiple sources
- Detect potential compromise

## 🧪 Tools Used
- Splunk (SIEM)
- VirusTotal (URL/File Analysis)
- Any.Run (Sandbox Analysis)

## 📊 Investigation Steps

### 1. Email Analysis
- Detected spoofed domain (micr0soft-support.com)
- SPF/DKIM/DMARC failure

### 2. URL Analysis
- Suspicious domain (.xyz)
- Flagged in VirusTotal

### 3. Endpoint Analysis
- WINWORD.exe spawned PowerShell
- Encoded command execution

### 4. Network Analysis
- Outbound connection to suspicious IP (possible C2)

## 🚨 Findings
- Confirmed phishing attack
- Malicious macro-enabled document
- Evidence of command execution and external communication

## 🛡️ Response Actions
- Blocked malicious domain/IP
- Recommended credential reset
- Suggested endpoint isolation

## 📂 Project Files
- Logs: email, web, endpoint, network
- Splunk queries
- Investigation report

## 💡 Key Takeaway
Phishing detection requires correlation across email, endpoint, and network logs—not just email analysis.
