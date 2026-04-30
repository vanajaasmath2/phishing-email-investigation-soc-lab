# 🔍 Phishing Email Investigation Report (SOC L1)

## 🧾 Incident Summary
A suspicious email was reported by a user claiming to be a password reset notification. Initial triage identified indicators of a phishing attempt involving a spoofed sender, malicious URL, and macro-enabled attachment. Further investigation confirmed execution of a malicious payload and outbound communication to a potential Command & Control (C2) server.

---

## 🕒 Timeline of Events

| Time        | Event Description                          |
|------------|-------------------------------------------|
| 10:12 AM   | Phishing email delivered to user          |
| 10:15 AM   | User clicked malicious URL                |
| 10:16 AM   | Malicious document executed               |
| 10:17 AM   | PowerShell process triggered              |
| 10:17 AM   | Outbound connection to external IP        |

---

## 📧 Email Analysis

**Sender:** security@micr0soft-support.com  
**Recipient:** user1@company.com  
**Subject:** Urgent Password Reset  
**Attachment:** Password_Reset.docm  

### Findings:
- Spoofed domain detected (micr0soft instead of microsoft)
- SPF: Fail, DKIM: None, DMARC: Fail
- Presence of macro-enabled attachment (.docm)

### Conclusion:
The email is malicious and crafted to trick the user into executing a payload.

---

## 🌐 URL Analysis

**URL:** http://microsoft-login-alert[.]xyz  

### Findings:
- Newly registered suspicious domain
- Mimics legitimate Microsoft login page
- Associated with phishing activity

### Conclusion:
The URL is used for credential harvesting.

---

## 📎 Attachment Analysis

**File Name:** Password_Reset.docm  

### Findings:
- Macro execution observed
- WINWORD.exe spawned powershell.exe
- Encoded PowerShell command execution

### Conclusion:
The attachment is malicious and used to execute scripts on the victim machine.

---

## 💻 Endpoint Analysis

### Observations:
- Parent Process: WINWORD.EXE
- Child Process: powershell.exe
- Encoded command execution detected

### Indicators:
- Suspicious parent-child process relationship
- Evidence of macro-based execution

### Conclusion:
Endpoint shows signs of malicious activity triggered by the document.

---

## 🌍 Network Analysis

### Observations:
- Destination IP: 45.77.88.12
- Port: 443

### Findings:
- Unknown external IP
- Potential Command & Control (C2) communication

### Conclusion:
Compromised system attempted to communicate with attacker infrastructure.

---

## 📊 Log Correlation (SIEM)

### Findings:
- Email delivered to multiple users
- At least one user clicked the malicious link
- Endpoint logs confirm payload execution
- Network logs show suspicious outbound traffic

### Conclusion:
This is a confirmed phishing attack with successful execution.

---

## 🚨 Indicators of Compromise (IOCs)

- Malicious Domain: micr0soft-support.com
- Phishing URL: microsoft-login-alert.xyz
- Malicious File: Password_Reset.docm
- Suspicious IP: 45.77.88.12
- Process: powershell.exe (spawned by WINWORD.EXE)

---

## 🔗 Attack Chain

1. Phishing email delivered
2. User clicked malicious link
3. File downloaded and opened
4. Macro executed
5. PowerShell triggered
6. Outbound C2 communication initiated

---

## 🛡️ Response Actions

- Blocked malicious domain and IP
- Quarantined phishing email
- Reset affected user credentials
- Isolated compromised endpoint
- Escalated incident to SOC L2

---

## 📌 Final Conclusion

This investigation confirms a multi-stage phishing attack involving:
- Social engineering
- Credential harvesting
- Malware execution
- Command & Control communication

The attack successfully progressed beyond initial access, emphasizing the importance of layered security and log correlation.

---

## 💡 Key Takeaways

- Email analysis alone is not sufficient
- Correlating logs across multiple sources is critical
- Macro-enabled documents remain a major threat vector
- Early detection reduces impact significantly

---
