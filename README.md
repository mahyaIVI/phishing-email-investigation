# Phishing Email Investigation

A Tier 1 SOC investigation of a safe, synthetic phishing email — analyse the sender, headers, links and attachment, then write a verdict with evidence and IOCs.

**Author:** Mahya Mahdavi (mahyaIVI)
**Skills shown:** Email header analysis, phishing indicators, URL / domain checking, attachment triage, IOC extraction, incident write-up

## Scenario

A user reports a suspicious email claiming their Microsoft 365 account will be closed in 24 hours unless they "verify" it by clicking a link. Your job is to investigate it like a Tier 1 SOC analyst: prove whether it is phishing, and say what to do next.

**Do not use a real phishing email from your inbox for this lab.** Use the synthetic sample in `sample-data/sample-email.eml` / `sample-email.txt` — it is fake, safe, and made for training. Never click a link or open an attachment in a real suspicious email.

## How to investigate

1. **Sender** — display name vs real address, lookalike domain, Reply-To
2. **Headers** — `Received:`, `Return-Path`, SPF / DKIM / DMARC results
3. **Body** — urgency, generic greeting, spelling, what it asks you to do
4. **Links** — hover to see the real URL, do NOT click. Expand short links, check the domain on VirusTotal
5. **Attachment** — do NOT open it. Note name, type, size, hash. Check the hash on VirusTotal
6. **Verdict** — Malicious / Suspicious / Legitimate, with evidence, IOCs, and recommended response

## Files

- `analysis-report.md` — blank investigation report template, with a worked synthetic example at the bottom
- `sample-data/sample-email.txt` — the safe synthetic phishing email to analyse (plain text)
- `sample-data/sample-email.eml` — the same email in .eml format, so you can open it in a mail client / analyser
- `iocs.txt` — indicators of compromise from the sample (sender, domains, URLs, attachment hash)
- `evidence/` — put your annotated screenshots here, with all personal data removed

## What a good report shows

- A timeline of what you checked, in order
- Annotated evidence for each finding — not just "it looks phishing"
- A clear verdict, and what would change it
- IOCs a defender can actually use (block / search)
- Recommended response: block, report, delete, warn the user, and — if anyone clicked — reset password and check the account

## Tools (all free)

- A text editor / mail client to read headers
- VirusTotal (https://www.virustotal.com) — check URLs, domains and file hashes
- urlscan.io — check a URL safely, without visiting it yourself
- Google Admin Toolbox Messageheader (https://toolbox.googleapps.com/apps/messageheader/) — paste headers to read them easily

## Safety rules

- Never analyse a real phishing email on your work / personal machine with links clicked or attachments opened
- Never upload real personal data, real email addresses, or real credentials to GitHub
- All data in this repo is synthetic: `testuser@yourdomain.com`, `203.0.113.45`, `198.51.100.23` are TEST-NET addresses, and the domains are fake

## Detection limitations

- Header analysis alone cannot prove intent — a spoofed sender can pass some checks
- A clean VirusTotal result does not mean a link is safe — new phishing pages are often undetected for hours
- This lab uses one sample; real phishing varies by campaign, language, and target
