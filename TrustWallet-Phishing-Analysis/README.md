# Phishing Email Analysis Report - Trust Wallet Impersonation

## Summary
* **Subject:** FWD: All unverified accounts will be suspended on 10/30/2022.
* **Sender (Display):** Trustwallet-Support <7wq1vg3kn9woejk4@emails.gorgias.com>
* **Real Sender IP:** 143.55.227.147 (Mailgun Relay)
* **Target:** emily.jenkins@potentialsecurity.net
* **Verdict:** Malicious (Crypto Phishing / Brand Impersonation)

---

## Technical Findings
* **Authentication:** DMARC Failed (Domain Mismatch: `emails.gorgias.com` vs `gorgias.io`).
* **Tactics:** Impersonating Trust Wallet to panic the user with account suspension threats.
* **Abused Services:** Exploited Gorgias helpdesk infrastructure and Mailgun relays to bypass basic security filters.
* **Open Redirect:** Used a legitimate domain (`usertest.sciquest.com`) as a redirector to mask the destination phishing page.

---

## Indicators of Compromise (IoCs)
* **Sender IP:** `143.55.227.147`
* **Redirector URL:** `https://usertest.sciquest.com/apps/Router/ExternalSiteTransition?url=...`
* **Final Phishing URL:** `https://drop-coin-availablenow.site44.com/`

---

## Recommended Mitigation
1. Block the phishing destination domain `drop-coin-availablenow.site44.com` on the Web Proxy/Firewall.
2. Delete the email from user mailboxes across the organization.
3. Reset seed phrases/credentials immediately if the target interacted with the phishing page.
