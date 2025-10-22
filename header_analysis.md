# Header Analysis (simulated / example)

Below is a reconstructed sample of the critical header lines and an explanation of why each is suspicious.
This header is a *simulated example* meant to teach how to read and interpret real headers.

```
Return-Path: <bounce@notify-secure-mail.com>
Received: from mailrelay.example.net (mailrelay.example.net [203.0.113.45])
    by mx.google.com with ESMTP id x7si12345qkb.2025.10.20.09.19.54
    for <user@example.com>; Mon, 20 Oct 2025 09:19:54 +0530 (IST)
Received-SPF: fail (google.com: domain of support@bank-secure.com does not designate 203.0.113.45 as permitted sender) client-ip=203.0.113.45;
Authentication-Results: mx.google.com;
    spf=fail (google.com: domain of support@bank-secure.com does not designate 203.0.113.45 as permitted sender) smtp.mailfrom=support@bank-secure.com;
    dkim=neutral (message not signed by a recognized domain) header.d=none;
    dmarc=fail (p=none) header.from=bank-secure.com
From: "SBI Bank" <support@bank-secure.com>
Reply-To: account-security@secure-notify.com
Message-ID: <20251020.9i2a3.example@mailrelay.example.net>
MIME-Version: 1.0
Content-Type: text/plain; charset=UTF-8
```

## What to look for and why these headers are suspicious

- **Return-Path vs From mismatch**: The `Return-Path` (bounce address) and `From` domains are different from official bank domains. Attackers often use third-party mail relays and set a return-path that doesn't match the claimed sender.
- **Received-SPF: fail**: SPF failed because the sending IP is not authorized by `bank-secure.com`. Legitimate bank mail should pass SPF or use proper DKIM signatures.
- **DKIM neutral / absent**: No DKIM signature from the bank domain; banks typically sign transactional e-mails.
- **DMARC fail**: DMARC failing indicates the message fails alignment checks — another red flag.
- **Reply-To different from From**: Replies go to `account-security@secure-notify.com` instead of the bank's domain — common trick to harvest replies.
- **Untrusted relay IP**: `203.0.113.45` is not associated with the bank; reverse DNS or WHOIS will likely show a different owner.

## Quick header-check steps (tools)
- Copy full headers and paste into: https://mxtoolbox.com/EmailHeaders.aspx or https://toolbox.googleapps.com/apps/messageheader/
- Look for `spf`, `dkim`, `dmarc` results and `Received` chains.
- If SPF/DKIM/DMARC show FAIL or NONE and other fields mismatch, treat as phishing.
