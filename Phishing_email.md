# 1) Phishing Email no.1:

Return-Path: <bounce@paypal-secure-test.test>
Received: from unknown (HELO smtp-out.attacker-host.test) (198.51.100.25)
	by mx.yourmailprovider.test (Postfix) with ESMTPS id HJKL1234XYZ
	for <prabhat.shinde@example.com>; Tue, 23 Sep 2025 09:12:06 +0530 (IST)
Received: from smtp-out.attacker-host.test (localhost [127.0.0.1])
	by smtp-out.attacker-host.test (Postfix) with ESMTP id OUT1234567
	for <prabhat.shinde@example.com>; Tue, 23 Sep 2025 03:12:04 +0000 (UTC)
Received: from compromised-web01.attacker.test (unknown [192.0.2.55])
	by smtp-out.attacker-host.test (Postfix) with ESMTP id RELAY98765
	for <prabhat.shinde@example.com>; Tue, 23 Sep 2025 03:11:58 +0000 (UTC)
From: "Account Security" <security@paypal-secure-test.test>
Reply-To: phish@attacker.test
To: prabhat.shinde@example.com
Subject: Immediate Action Required — Verify Your PayPal Account
Date: Tue, 23 Sep 2025 09:12:05 +0530
Message-ID: <20250923031205.abc123@attacker-host.test>
MIME-Version: 1.0
Content-Type: text/html; charset="UTF-8"

Authentication-Results: mx.yourmailprovider.test;
	spf=fail (sender IP is 198.51.100.25) smtp.mailfrom=paypal-secure-test.test;
	dkim=permerror (bad signature) header.d=paypal-secure-test.test;
	dmarc=fail action=reject header.from=paypal-secure-test.test

Received-SPF: fail (mx.yourmailprovider.test: domain of paypal-secure-test.test does not designate 198.51.100.25 as permitted sender) client-ip=198.51.100.25; envelope-from=paypal-secure-test.test
X-Originating-IP: [198.51.100.25]
X-Mailer: PHPMailer 6.4.1
X-Spam-Status: Yes, score=9.6 required=5.0
Return-Path: <bounce@paypal-secure-test.test>

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

