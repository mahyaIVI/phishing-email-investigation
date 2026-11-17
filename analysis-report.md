# Phishing Email Investigation Report

**Analyst:** Mahya Mahdavi
**Date investigated:**
**Sample:** `sample-data/sample-email.txt` (synthetic, safe for training)
**Verdict:** ☐ Malicious / Phishing  ☐ Suspicious  ☐ Legitimate

## 1. Summary

_Write 2–3 sentences: what the email claims, who it pretends to be from, and what it wants the user to do._

## 2. Sender analysis

| Check | Finding |
|---|---|
| Display name | |
| Real sender address | |
| Domain — real or lookalike? | |
| Reply-To address | |
| Does Reply-To match the sender? | |

## 3. Header analysis

| Check | Finding |
|---|---|
| `Return-Path` | |
| `Received:` — where did it really come from? | |
| SPF result | |
| DKIM result | |
| DMARC result | |
| Unusual routing / free-mail provider? | |

## 4. Body analysis

- Greeting (personalised or generic?):
- Urgency / fear language:
- Spelling / grammar / formatting issues:
- What is it asking the user to do?
- Does the request make sense for this sender?

## 5. Link analysis — do NOT click the links

| Link text | Real URL (hover / expand) | Verdict |
|---|---|---|
|  |  |  |
|  |  |  |

- Checked on VirusTotal / urlscan.io? (result):
- Lookalike domain, extra subdomain, HTTP instead of HTTPS?

## 6. Attachment analysis — do NOT open it

| Field | Value |
|---|---|
| File name | |
| File type | |
| File size | |
| SHA-256 hash | |
| VirusTotal result | |

Red flags (`.html`, `.iso`, `.zip`, `.docm` / macro file, double extension, etc.):

## 7. Evidence

_Put annotated screenshots in `evidence/` and list them here, with personal data removed._

- Screenshot 1:
- Screenshot 2:

## 8. Verdict

**☐ Malicious / Phishing  ☐ Suspicious  ☐ Legitimate**

Why — list the evidence that supports this verdict:

1.
2.
3.

What would change the verdict:

## 9. Indicators of Compromise (IOCs)

Copy these into `iocs.txt` as well.

- Sender:
- Reply-To:
- Malicious domains / URLs:
- Attachment name + hash:
- IPs from headers (if any):

## 10. Recommended response

- [ ] Block sender / domain
- [ ] Report to IT / phishing mailbox
- [ ] Delete the email
- [ ] Warn the user
- [ ] If anyone clicked: reset password, check account activity, revoke sessions
- [ ] Other:

## 11. Limitations

- What this investigation could not prove:
- What you would check next with more access / tools:

---

## Worked example (synthetic — from the sample in this repo)

**Verdict: Malicious / Phishing**

- Sender display name is "Microsoft 365 Security", but the real address is `security-alert@micros0ft-support.net` — a lookalike domain (`micros0ft` with a zero), not `microsoft.com`
- Reply-To goes to a different address: `verify@micros0ft-support.net`
- SPF: fail. DKIM: fail. DMARC: fail
- Body: "Dear Customer" (generic), "Your account will be closed in 24 hours" (urgency), spelling errors, and a link labelled "Verify your account" that actually goes to `http://micros0ft-support.net/verify/login.html`
- Attachment: `Invoice_2026.docm` — a macro-enabled Word document, a classic malware carrier. Do not open it.
- IOCs: `security-alert@micros0ft-support.net`, `micros0ft-support.net`, `http://micros0ft-support.net/verify/login.html`, `Invoice_2026.docm`
- Response: block the domain, report it, delete it, warn the user. If anyone clicked, reset their password and check their Microsoft 365 sign-in activity.
