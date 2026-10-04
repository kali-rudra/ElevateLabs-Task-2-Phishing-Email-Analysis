# ElevateLabs Internship — Task 2

## Phishing Email Analysis

### Objective

Analyze a suspicious email to identify phishing indicators, examine its email headers and content, and document the findings using a structured security-analysis approach.

### Sample Analyzed

* **Sample:** `sample2-Redacted.txt`
* **Claimed sender:** Microsoft Account Team
* **Subject:** `[Action Required] Unusual sign-in activity on your account`
* **Initial classification:** **Phishing — High Confidence**

### Key Indicators Identified

* Sender domain impersonates Microsoft but does not use an official Microsoft domain.
* SPF authentication failed.
* DKIM authentication failed.
* DMARC authentication failed.
* The message uses urgency and account-security concerns to influence the recipient.
* The email contains a shortened `bit.ly` action URL that obscures the final destination.
* Microsoft branding and corporate information are used to increase credibility.
* The received-mail infrastructure is inconsistent with the claimed Microsoft identity.

### Analysis

Detailed examination of the email, including header analysis, authentication results, social-engineering indicators, and classification reasoning, is documented in:

`analysis/sample2-analysis.md`

### Evidence

Supporting evidence is stored under:

`evidence/screenshots/`

This includes the Google Admin Toolbox header-analysis result showing the SPF, DKIM, and DMARC failures.

A sanitized text representation of the email source is also provided as:

`sample2-Redacted.txt`

The recipient address in the source has been redacted before publication.

### Classification Principle

SPF, DKIM, and DMARC failures are warning indicators, not standalone proof that an email is malicious. An email should be classified as phishing when multiple independent indicators support that conclusion, and a malicious classification can be confirmed when there is reliable evidence of malicious behavior, such as credential harvesting, a malicious payload, or a confirmed malicious destination.

For this sample, the combination of authentication failures, sender-domain impersonation, urgency-based social engineering, and a shortened action URL supports a **high-confidence phishing classification**.

### Safety Note

The suspicious URL in the sample was not opened or interacted with during analysis. The email source is provided strictly for defensive cybersecurity education and analysis. The embedded URL should not be opened, resolved, or otherwise interacted with.
