# Recommendations & Reporting Steps

## For end users (quick checklist)
- Never click links in unexpected emails that ask for credentials or personal data.
- Hover over links to inspect the real URL; if it differs from the displayed domain, do not click.
- Check the sender's email address carefully — do not trust display names alone.
- Look for SPF/DKIM/DMARC pass flags in headers if possible; if they fail, be suspicious.
- If unsure, open the bank site in a browser manually (type the URL) rather than using links.
- Report the email via the email client's "Report phishing" feature and/or forward to the bank's official abuse address.

## For admins / SOCs
- Add sender domains to blocklist if confirmed malicious and use email security gateway to throttle similar messages.
- Enable/strict DMARC policy (p=quarantine or p=reject) for organizational domains.
- Use URL sandboxing and ATP (Advanced Threat Protection) for incoming links.
- Educate users with regular phishing drills and simulated phishing tests.
- If multiple users received the message, create an incident, capture headers, and do a takedown request via registrar and hosting providers.

## Reporting
- Report the phishing domain to abuse contacts (WHOIS) and to Google Safe Browsing / Microsoft SmartScreen / PhishTank.
- Notify the real bank's security contact with full headers and sample email (do not attach any clicked links — provide text only).
