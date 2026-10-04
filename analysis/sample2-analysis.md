# Phishing Email Analysis — Sample 2

## 1. Overview

This analysis examines a suspicious email presented as a Microsoft account security notification. The analysis considers the email headers, sender identity, authentication results, message content, social-engineering indicators, and embedded action URL.

**Classification:** Phishing — High Confidence

---

## 2. Email Metadata

| Field        | Observed Value                                                  |
| ------------ | --------------------------------------------------------------- |
| From         | `"Microsoft Account Team" <noreply@microsoftonline-verify.com>` |
| Return-Path  | `noreply@microsoftonline-verify.com`                            |
| Subject      | `[Action Required] Unusual sign-in activity on your account`    |
| Date         | Thu, 06 Feb 2026 17:14:18 +0000                                 |
| Recipient    | `jacobcookofficial@gmail.com`                                   |
| Content Type | `text/html`                                                     |
| X-Priority   | `1`                                                             |

### Initial Observation

The display name claims to represent the Microsoft Account Team, but the sender uses the domain:

`microsoftonline-verify.com`

This is not an official Microsoft domain and is therefore a significant impersonation indicator.

---

## 3. Header and Infrastructure Analysis

The message contains the following received-mail information:

`mail.microsoftonline-verify.com (vps-291847.contabo.net. [178.238.225.91])`

The infrastructure shown in the received header is inconsistent with the claimed Microsoft identity. The message appears to have originated from a third-party VPS hostname rather than infrastructure that would normally be expected for an official Microsoft account-security notification.

This observation should be treated as an indicator rather than standalone proof of malicious activity.

---

## 4. Email Authentication Results

The supplied headers report:

* **SPF:** Fail
* **DKIM:** Fail
* **DMARC:** Fail

### Email Authentication — Quick Reference

SPF, DKIM, and DMARC are email-security mechanisms used to help verify whether a message is genuinely authorized by the domain it claims to come from. **SPF** checks whether the sending server is authorized, **DKIM** verifies a cryptographic signature associated with the message, and **DMARC** checks domain alignment and defines how authentication failures should be handled. A `fail` result does not by itself prove that an email is malicious, but multiple failures are an important warning sign when combined with other phishing indicators.

---

## 5. Social-Engineering Indicators

The message uses several techniques commonly associated with phishing:

### Urgency

The subject begins with:

`[Action Required]`

The message also states that the account requires immediate attention.

This creates pressure for the recipient to act quickly rather than independently verify the message.

### Fear / Account-Security Theme

The email claims that unusual activity was detected on the recipient's Microsoft account.

It provides the following claimed activity details:

* Country/region: Russia
* IP address: `91.234.99.42`
* Date: February 6, 2026 4:32 AM UTC
* Platform: Windows 10
* Browser: Chrome 120.0

These details are presented by the email as evidence of suspicious account activity. They were not independently verified during this analysis.

### Brand Impersonation

The email uses:

* The name "Microsoft Account Team"
* Microsoft-style visual presentation
* A Microsoft logo reference
* Microsoft corporate address information
* Microsoft-style security terminology

These elements are designed to increase the credibility of the message.

---

## 6. Suspicious URL

The main call-to-action is:

`https://bit.ly/3vF9xKz`

The URL uses the `bit.ly` URL-shortening service.

A shortened URL hides the final destination from the recipient and makes it more difficult to determine where the link actually leads before clicking it.

**The URL was not opened or interacted with during this analysis.**

---

## 7. HTML and Content Observations

The message is formatted as HTML and contains a reference to an embedded image:

`cid:microsoft-logo`

The supplied email content does not include the complete MIME attachment data, so the actual embedded image cannot be independently examined from the material provided.

The message also includes the Microsoft corporate address:

`Microsoft Corporation, One Microsoft Way, Redmond, WA 98052`

This is another example of legitimate-looking information being used to reinforce the claimed identity.

---

## 8. Combined Indicators

The following independent indicators support the phishing assessment:

1. Microsoft impersonation through the sender display name.
2. Use of a suspicious non-Microsoft sender domain.
3. SPF authentication failure.
4. DKIM authentication failure.
5. DMARC authentication failure.
6. Received infrastructure inconsistent with the claimed Microsoft identity.
7. Urgency and account-security pressure.
8. Use of a shortened action URL.
9. Microsoft branding and corporate information intended to increase credibility.

The combination of these indicators is significantly stronger evidence than any individual indicator alone.

---

## 9. Classification Principle

SPF, DKIM, and DMARC failures are warning indicators, not standalone proof that an email is malicious.

An email should be classified as phishing when multiple independent indicators support that conclusion, and a malicious classification can be confirmed when there is reliable evidence of malicious behavior, such as credential harvesting, a malicious payload, or a confirmed malicious destination.

For this sample, the combination of authentication failures, sender-domain impersonation, urgency-based social engineering, suspicious infrastructure, and a shortened action URL supports a **high-confidence phishing classification**.

---

## 10. Recommended Defensive Actions

If this message were received in a real environment:

1. Do not click the embedded link.
2. Do not provide credentials or other sensitive information.
3. Verify the account alert through the organization's official website or application rather than through the email.
4. Report the message through the organization's phishing-reporting process.
5. Preserve the original email and headers for investigation.
6. If credentials were entered after interacting with the message, change the affected password immediately and investigate the account for unauthorized activity.

---

## 11. Conclusion

The analyzed message is assessed as **Phishing — High Confidence**.

The assessment is based on multiple independent indicators, including sender-domain impersonation, failed email authentication checks, suspicious infrastructure, urgency-based social engineering, Microsoft branding, and a shortened action URL.

No interaction was performed with the suspicious URL during this analysis.
