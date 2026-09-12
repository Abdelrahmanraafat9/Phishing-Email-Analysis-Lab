# Phishing Analysis Report - CyberDefenders (PhishStrike)

## Summary
* **Subject:** COMMERCIAL PURCHASE RECEIPT ONLINE 27 NOV
* **Sender:** ERIKA JOHANA LOPEZ VALIENTE <erikajohana.lopez@uptc.edu.co>
* **Target:** servicios.informaticos@fsfb.org.co
* **Payload Type:** Executable Malware via Direct Link (`install.exe`)
* **Verdict:** Malicious (Phishing / Malware Delivery / Compromised Educational Account)

---

## Technical Findings
* **Authentication Failures:** 
  * **SPF:** SoftFail (Sender IP `18.208.22.104` is not authorized by `uptc.edu.co`).
  * **DKIM:** Failed (No key found for signature).
* **Compromised Account Abused:** The email header shows valid Google/UPTC infrastructure, indicating an official educational email account (`@uptc.edu.co`) was likely hijacked to bypass reputation filters.
* **Malicious Link & Payload:** Instead of a legitimate PDF or document attachment, the "VIEW INVOICE DOCUMENT" link points directly to a raw executable file (`http://107.175.247.199/loader/install.exe`).
* **Tactics:** Financial lure (Fake Purchase Receipt of $625.000 pesos) combined with authority impersonation (Academic Credential Signature) to trick the target into executing the payload.

---

## Indicators of Compromise (IoCs)
* **Sender Domain:** `uptc.edu.co`
* **Suspicious Originating IP:** `18.208.22.104`
* **Malicious Payload Host IP:** `107.175.247.199`
* **Malicious URL:** `http://107.175.247.199/loader/install.exe`
* **Dropped File:** `install.exe`

---

## Recommended Mitigation
1. **Network Block:** Immediately block IP `107.175.247.199` and URL `http://107.175.247.199/loader/install.exe` on Perimeter Firewall / Web Proxy.
2. **EDR/Endpoint Sweep:** Search for host executions of `install.exe` across enterprise endpoints.
3. **Email Purge:** Delete the email from all internal user mailboxes matching Subject or Sender.
4. **External Notification:** Contact the security team at `uptc.edu.co` to report their compromised account (`erikajohana.lopez@uptc.edu.co`).
