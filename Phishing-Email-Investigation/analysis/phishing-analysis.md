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
