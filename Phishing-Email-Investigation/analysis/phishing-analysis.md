# Phishing Email Investigation

## 1. Sender Analysis

### Sender Address

**From:** Microsoft Account Security <security-alert@micros0ft-support.com>

### Finding

The sender domain `micros0ft-support.com` appears suspicious.

The domain uses **"micros0ft"** instead of the legitimate spelling **"Microsoft"**, replacing the letter `o` with the number `0`.

This is a common **lookalike/typosquatting technique** used in phishing emails to make a malicious domain appear legitimate.

### Verdict

**Suspicious Sender Domain**
## 2. Email Authentication Analysis

### SPF — Sender Policy Framework

**Result:** FAIL ❌

The SPF check failed because the sending server was not authorized to send emails for the domain `micros0ft-support.com`.

**Finding:** The email may have been sent from an unauthorized mail server.

---

### DKIM — DomainKeys Identified Mail

**Result:** NONE ❌

No DKIM signature was found in the email.

**Finding:** There is no DKIM signature available to help verify the sender's domain or message integrity.

---

### DMARC — Domain-based Message Authentication, Reporting & Conformance

**Result:** FAIL ❌

The email failed DMARC authentication for the domain `micros0ft-support.com`.

**Finding:** The email did not pass the required sender authentication and domain alignment checks.

### Authentication Summary

| Check | Result | Finding |
|---|---|---|
| SPF | ❌ FAIL | Unauthorized sending server |
| DKIM | ❌ NONE | No digital signature found |
| DMARC | ❌ FAIL | Authentication/alignment failure |

### Overall Finding

The failed SPF and DMARC checks, combined with the absence of DKIM, are strong indicators that the email is suspicious and may be part of a phishing or spoofing attempt.
## 3. Suspicious URL Analysis

### URL Identified

`http://microsoft-account-security.example.com/verify`

### Findings

- The URL uses **HTTP instead of HTTPS**, so the connection is not encrypted.
- The URL uses an account-verification theme, which is commonly used in phishing attacks.
- The link creates a sense of urgency because the email asks the user to verify the account within 24 hours.
- The URL should be treated as suspicious and should not be opened without safe analysis.

### Risk

**Potential Credential Phishing**

The link may attempt to direct users to a fake login or account-verification page designed to collect credentials.

### Safety Action

**Do not click the suspicious URL.** Analyze suspicious links using approved security tools or an isolated sandbox environment.

### Verdict

**Suspicious URL — Potential Phishing Link 🚩**
## 4. Social Engineering Analysis

### Techniques Identified

| Technique | Evidence | Risk |
|---|---|---|
| Urgency | "within 24 hours" | High |
| Threat | "account will be permanently suspended" | High |
| Impersonation | Claims to be Microsoft | High |
| Credential Targeting | Requests account verification | High |
| Suspicious Link | External verification URL | High |

### Findings

The email uses multiple social engineering techniques to pressure the recipient into taking immediate action.

The attacker creates a sense of urgency and fear by threatening account suspension. The email also impersonates a trusted organization and directs the user to a suspicious verification link.

### Verdict

**Social Engineering Indicators Detected 🚩**

The combination of urgency, threats, impersonation, and a suspicious verification link strongly supports the classification of this email as a phishing attempt.
## 5. Indicators of Compromise (IOCs)

The following indicators were identified during the investigation:

| IOC Type | Indicator | Description |
|---|---|---|
| Domain | `micros0ft-support.com` | Suspicious lookalike domain |
| Sender Email | `security-alert@micros0ft-support.com` | Suspicious sender address |
| Return-Path | `bounce@micros0ft-support.com` | Suspicious return address |
| URL | `http://microsoft-account-security.example.com/verify` | Potential credential-phishing URL |
| SPF | FAIL | Sending server not authorized |
| DKIM | NONE | No DKIM signature found |
| DMARC | FAIL | Authentication/alignment failure |

### IOC Assessment

These indicators collectively support the classification of the email as a **phishing attempt**.

The suspicious domain, authentication failures, social engineering techniques, and potentially malicious URL should be investigated and monitored by the SOC team.
## 6. Final Investigation Verdict

### Classification

**PHISHING EMAIL — MALICIOUS / HIGH RISK 🚨**

### Key Evidence

The investigation identified multiple phishing indicators:

1. Suspicious lookalike sender domain.
2. SPF authentication failure.
3. No DKIM signature.
4. DMARC authentication failure.
5. Suspicious account-verification URL.
6. Urgency and threat-based social engineering.
7. Impersonation of a trusted organization.
8. Multiple Indicators of Compromise (IOCs).

### Recommended SOC Actions

- Do not click the suspicious URL.
- Do not provide credentials or other sensitive information.
- Block or monitor the suspicious domain and URL.
- Report the email as phishing.
- Search security logs and email systems for similar messages.
- Check whether other users received the same email.
- If credentials were submitted, reset the affected account credentials and investigate for unauthorized activity.

### Final Conclusion

Based on the sender analysis, email authentication results, suspicious URL, social engineering techniques, and identified IOCs, the email is classified as a **phishing attempt**.

**Final Verdict: Malicious / High Risk**
