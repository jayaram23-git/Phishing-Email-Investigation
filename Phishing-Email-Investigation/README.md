# Phishing Email Investigation

## Objective

Investigate a simulated phishing email to identify malicious indicators, analyze email authentication results, and determine whether the email is legitimate or malicious.

## Investigation Scope

The investigation covered:

- Sender and domain analysis
- Email header analysis
- SPF, DKIM, and DMARC
- Suspicious URL analysis
- Social engineering techniques
- Indicators of Compromise (IOCs)
- Final investigation verdict
- Recommended SOC response actions

## Key Findings

- Suspicious lookalike sender domain: `micros0ft-support.com`
- SPF authentication: **FAIL**
- DKIM authentication: **NONE**
- DMARC authentication: **FAIL**
- Suspicious account-verification URL identified
- Urgency and threat-based social engineering detected
- Multiple Indicators of Compromise identified

## Tools and Concepts

- Email Header Analysis
- SPF
- DKIM
- DMARC
- IOC Identification
- Phishing Detection
- Social Engineering Analysis
- SOC Investigation Methodology

## Investigation Result

**Verdict: PHISHING EMAIL — MALICIOUS / HIGH RISK 🚨**

The email was classified as a phishing attempt based on the suspicious sender domain, authentication failures, suspicious URL, social engineering techniques, and identified IOCs.

## Recommended SOC Actions

- Do not click suspicious links.
- Do not provide credentials.
- Report the email as phishing.
- Block or monitor identified malicious indicators.
- Search email and security logs for similar activity.
- Check whether other users received the same email.
- Investigate affected accounts if credentials were submitted.

## Project Structure

```text
Phishing-Email-Investigation/
│
├── README.md
│
├── email-sample/
│   ├── sample-phishing-email.txt
│   └── sample-email-headers.txt
│
└── analysis/
    └── phishing-analysis.md
