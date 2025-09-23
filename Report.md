# Phishing Sample 1 — Payment / Account Verification (Payment Service impersonation)

**Raw email:**

From: "Account Security" <security@paypal-secure-test.test>
To: prabhat.shinde@example.com
Subject: Immediate Action Required — Verify Your PayPal Account
Date: Tue, 23 Sep 2025 09:12:05 +0530
MIME-Version: 1.0
Content-Type: text/html; charset=UTF-8

<html>
<body>
<p>Dear Customer,</p>

<p>We noticed unusual activity on your PayPal account. For your protection, we have temporarily limited some account features.</p>

<p><strong>To restore full access you must verify your account within 24 hours.</strong></p>

<p><a href="http://malicious-site.test/paypal/verify">Verify Your Account Now</a></p>

<p>If you do not complete verification within 24 hours, your account will be permanently suspended.</p>

<p>Thank you,<br/>
PayPal Security Team</p>
</body>
</html>


---


## Content analysis & indicators

- Sender display name vs address: Display shows “Account Security / PayPal” but the domain is paypal-secure-test.test (not PayPal’s official domain).

- Emergency / scare tactic: “within 24 hours” + threat of suspension — classic pressure tactic.

- Generic greeting: “Dear Customer” (no personalization).

- Mismatched link destination: Anchor text suggests PayPal verification but the link points to malicious-site.test (a non-PayPal domain). Hovering would reveal       mismatch.

- No contact/branding details: Missing account-specific info (last 4 digits, partial name) that legitimate alerts often include.

- What to look for later in headers: Return-path mismatch, SPF/DKIM FAIL, originating IP not owned by PayPal.

## Suggested immediate actions

- Do not click the link.

- Save raw email (for header analysis).

- Report to your org/security team and mark as phishing.

- If credentials were used on such a page, change password immediately and enable MFA.


---


Phishing Sample 2 — Office Document / Credential Harvest (Corporate Office 365 impersonation)

**Raw email:**

From: "IT Support" <it-support@office365-help-test.test>
To: prabhat.shinde@example.com
Subject: New Secure Document Shared With You — Action Required
Date: Mon, 22 Sep 2025 16:43:21 +0530
MIME-Version: 1.0
Content-Type: multipart/mixed; boundary="----=_Part_12345_67890"

------=_Part_12345_67890
Content-Type: text/html; charset=UTF-8

<html>
<body>
<p>Hello Prabhat,</p>

<p>Your colleague has shared an important document with you. To view the document, please open the attached file and enable editing.</p>

<p><b>Note:</b> The document is protected. You must sign in with your corporate account to unlock the file.</p>

<p><a href="http://secure-office.test/auth">Open Document</a></p>

<p>Regards,<br/>IT Support</p>
</body>
</html>

------=_Part_12345_67890
Content-Type: application/msword; name="SharedDocument.docm"
Content-Disposition: attachment; filename="SharedDocument.docm"
Content-Transfer-Encoding: base64

[BASE64 PAYLOAD REDACTED — do NOT include real malware]
------=_Part_12345_67890--


---


## Content analysis & indicators

- Sender impersonation: Claims to be “IT Support” and Office365, but domain office365-help-test.test is fake.

- Attachment type: .docm (macro-enabled) — commonly used to deliver malicious macros. Legit orgs rarely send unexpected macro-enabled docs.

- Instruction to “enable editing” / “sign in”: Social engineering to trick user into enabling macros or entering credentials.

- Link to sign-in page: Points to secure-office.test (not microsoft.com or your company domain).

- Personalization attempt: Uses name once but could be automatically injected; doesn't prove legitimacy.

- What to check later in headers: Reply-To different from From, suspicious Received chain, DKIM/SPF failures.

## Suggested immediate actions

- Do not open the attachment or enable editing/macros.

- View raw message and attachment hash (if required) and upload to VirusTotal (optional).

- Report and quarantine the message.

- If you clicked/opened and enabled macros, disconnect and escalate to incident response.
