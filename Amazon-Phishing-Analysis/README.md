# Phishing Email Analysis Report

## Summary
* **Subject:** [ACTION REQUEST] You have been red flagged for violating our terms
* **Sender (Display):** Amazon Help Center <amz@fareast.com.sg>
* **Real Sender IP:** 77.32.148.40 (Sendinblue Relay)
* **Verdict:** Malicious (Phishing / Brand Impersonation)

---

## Technical Findings
* **Authentication:** DMARC Failed (Domain Mismatch: `fareast.com.sg` vs `sendibt3.com`).
* **Tactics:** Impersonating Amazon to panic the user about account suspension.
* **Malicious Link:** Embedded links redirect to `chdgiei.r.bh.d.sendibt3.com` instead of Amazon.

---

## Indicators of Compromise (IoCs)
* **Sender IP:** `77.32.148.40`
* **Phishing URL:** `https://chdgiei.r.bh.d.sendibt3.com/...`

---

## Recommended Mitigation
1. Block domain `sendibt3.com` on the Web Gateway.
2. Delete the email from user mailboxes.
3. Reset credentials if the user clicked the link.
