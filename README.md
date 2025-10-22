# Task 2 — Phishing Email Analysis (Bank KYC / Account Block Scam)

**Author:** Shivas — Cybersecurity Student & Intern
**Note:** This repository contains a *sample phishing email* I analyzed for the internship Task 2. The sample is fictional and used only for educational purposes (to learn how to detect and report phishing). Do not use any part of this for malicious activity.

---

## Objective
Analyze a sample phishing email that impersonates a bank (KYC/Account Block scare) and document phishing indicators, header anomalies, link analysis, and recommended mitigation actions.

This submission includes:
- the full sample email (text)
- header analysis with SPF/DKIM/Return-Path/Received checks (simulated for learning)
- findings and prioritized mitigation
- placeholders for screenshots (Wireshark-like evidence is not applicable; however, screenshots of the email and header analysis should be added)

---

## Repo structure
```
task2-phishing/
├── README.md
├── phishing_email_sample.md
├── header_analysis.md
├── findings.md
├── recommendations.md
├── artifacts/
│   └── raw_email.eml        # (sample raw email file)
└── screenshots/
    └── README_ADD_IMAGES.txt
```

## How I completed the task
1. Created a realistic phishing email sample that mimics a bank's urgent KYC/account block notice.
2. Analysed the message headers and body to find spoofing indicators: mismatched From vs envelope-from, suspicious Return-Path, SPF fail, misleading links, urgent tone, and typos.
3. Wrote a findings document listing the indicators and severity.
4. Wrote recommended mitigation and reporting steps for both users and administrators.
5. Packed everything into this repo for submission.

Add your screenshots (email view + header analyzer results) into `screenshots/` before pushing to GitHub.
