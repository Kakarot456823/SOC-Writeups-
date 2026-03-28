# SOC Phishing Email Investigation – Domain Impersonation Case

## Incident Summary
A phishing email was identified targeting a user through domain impersonation and MX record manipulation. The objective of the attack was suspected credential harvesting via a fake authentication flow.

## Environment
Platform: LetsDefend SOC lab  
Alert Type: Phishing / Domain impersonation (MX record abuse detection)  
Severity: Medium  

---

## Incident Details
- Event ID: 304  
- Rule: SOC326 – Impersonating Domain MX Record Change Detected  
- Sender: no-reply@cti-report.io  
- Recipient: soc@letsdefend.io  
- Domain: letsdefwnd[.]io  
- MX Record: mail.mailerhost[.]net  
- Device Action: Allowed  

---

## Analysis
The investigation revealed multiple indicators consistent with a phishing infrastructure setup:

- The domain `letsdefwnd[.]io` closely resembles a legitimate domain, indicating **typosquatting**
- MX record configuration points to an external mail server (`mail.mailerhost[.]net`)
- This suggests potential redirection or control of email routing for malicious purposes
- Email content and structure indicate **social engineering tactics**
- The domain shows characteristics of newly observed or low-reputation infrastructure

No blocking action was triggered at the time of detection, but the activity was flagged as suspicious by the SOC rule engine.

---

## Threat Intelligence Analysis
The domain and related infrastructure were analyzed using threat intelligence sources:

- VirusTotal  
- AbuseIPDB  
- Cisco Talos  

Findings:
- No strong malicious detections reported at time of analysis
- Low or limited reputation across platforms
- MX record associated with external mail infrastructure
- No verified legitimate business association identified

This suggests either:
- A newly created domain  
- Or a low-profile phishing infrastructure not yet widely reported  

---

## Indicators of Compromise (IOCs)

### Network IOCs
- Domain: letsdefwnd[.]io  
- MX Record: mail.mailerhost[.]net  

### Email IOCs
- Sender: no-reply@cti-report.io  
- Recipient: soc@letsdefend.io  

### Detection IOCs
- Event ID: 304  
- Alert Type: Domain impersonation via MX record change  

---

## Impact Assessment
- No confirmed compromise observed
- No evidence of successful exploitation in logs
- However, infrastructure indicates possible preparation for phishing activity

If exploited, this type of configuration could enable:
- Credential harvesting
- Email spoofing
- Redirection of email traffic

---

## Recommendations

- Monitor DNS and MX record changes for suspicious modifications  
- Block impersonating or lookalike domains at email gateway level  
- Implement email authentication controls:
  - SPF  
  - DKIM  
  - DMARC  
- Use threat intelligence feeds for proactive detection  
- Continuously monitor for similar domain patterns and anomalies  

---

## Conclusion
This investigation identified a domain impersonation attempt involving MX record manipulation. Although no active compromise was confirmed, the indicators strongly suggest potential phishing infrastructure setup.

The case demonstrates SOC analyst responsibilities including alert triage, domain investigation, threat intelligence correlation, and IOC extraction.
