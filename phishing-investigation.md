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
![Figure 1: Alert details showing phishing detection](phishing-1.png)
---

## Analysis
The investigation revealed multiple indicators consistent with a phishing infrastructure setup:

- The domain `letsdefwnd[.]io` demonstrates typosquatting behavior by closely resembling a legitimate domain  
- MX record configuration points to an external mail server (`mail.mailerhost[.]net`), indicating possible external email routing  
- This setup is commonly associated with phishing infrastructure or email redirection abuse  
- The email content and structure indicate social engineering tactics  
- The domain shows low reputation and characteristics of newly observed infrastructure  

No blocking action was triggered at the time of detection, but the activity was flagged as suspicious by the SOC rule engine.

---

## Threat Intelligence Analysis
The domain and related infrastructure were analyzed using threat intelligence sources:

- VirusTotal  
- AbuseIPDB  
- Cisco Talos  

Findings indicate:
- No confirmed malicious detections at the time of analysis  
- Low or limited reputation across multiple sources  
- MX record associated with external mail infrastructure  
- No verified legitimate business association identified  

This suggests the domain may be either newly registered or part of low-visibility phishing infrastructure not yet widely reported.

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
- No confirmed compromise was observed in the environment  
- No evidence of successful exploitation in logs  
- However, the infrastructure suggests potential phishing campaign preparation  

If exploited, this setup could enable:
- Credential harvesting  
- Email spoofing  
- Redirection of email traffic  

---

## Recommendations
- Monitor DNS and MX record changes for suspicious modifications  
- Block impersonating or lookalike domains at email gateway level  
- Implement email authentication controls (SPF, DKIM, DMARC)  
- Use threat intelligence feeds for proactive detection  
- Continuously monitor for similar domain patterns and anomalies  

---

## Conclusion
This investigation identified a domain impersonation attempt involving MX record manipulation. Although no active compromise was confirmed, the indicators strongly suggest potential phishing infrastructure preparation and warrant proactive monitoring and mitigation.
