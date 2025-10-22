# Findings — Phishing Indicators (Human-style write-up)

**Summary:** The email is a classic bank impersonation phishing message. It uses urgency ("account will be blocked"), domain mismatches, and spoofed headers to trick the recipient into clicking a malicious link.

## Key indicators found (with explanation)

1. **Display name impersonation**  
   - The message shows "SBI Bank" as the display name, but the sender email is `support@bank-secure.com`. Display names are easy to fake.

2. **Mismatched domains (link and sender)**  
   - The verification link points to `https://sbi-security-update.com/verify?uid=ABCD1234` — not an official SBI domain. Hovering the link shows a different domain than expected.

3. **Urgent language / deadline**  
   - "Click within 24 hours" and threat of account suspension are designed to short-circuit careful thinking.

4. **Reply-To / Return-Path anomalies**  
   - `Reply-To` and `Return-Path` point to unrelated domains, indicating the attacker owns those addresses.

5. **Header authentication failures**  
   - SPF: FAIL, DKIM: absent/neutral, DMARC: FAIL in the example header. Real bank emails should pass these.

6. **Poor grammar / simple errors (if present)**  
   - The example is fairly clean, but many phishing emails contain subtle grammar or spacing errors. This is still a risk marker.

7. **Generic greeting**  
   - Uses "Dear Customer" instead of user-specific info — phishing often avoids personalized data.

8. **No TLS indicator / unexpected attachments**  
   - There are no attachments here (good), but the URL itself is suspicious and the site likely not using the official certificate chain.

## Severity assessment (prioritized)
- **High**: Mismatched domains + SPF/DKIM/DMARC fails + malicious link.
- **Medium**: Urgent call-to-action and Reply-To anomalies.
- **Low**: Generic greeting and potential minor language issues.

## Action taken / recommended immediate steps for recipient
1. DO NOT CLICK the link.
2. Mark as phishing in your email client (Report to provider).
3. Forward full headers to your bank's official abuse/security email.
4. Delete the email after reporting.
5. If you clicked the link, change passwords and notify the bank immediately.
