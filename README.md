# 🛡️ ThreatScan — Outlook Email Security Add-in
**Built by Gritty | 7Networks Security**

ThreatScan is a post-delivery threat indicator tool for Microsoft Outlook. It analyzes delivered emails for phishing, social engineering, malicious attachments, and suspicious senders — giving users and IT staff actionable intelligence after an email lands in the inbox. It provides a 0–100 risk score with color-coded results and itemized threat findings.

---

## ✅ Features

| Feature | Status |
|---|---|
| Phishing keyword detection (Top 25) | ✅ Live |
| Social engineering language detection (Top 25) | ✅ Live |
| Suspicious link scanning (HTTP, IP, URL shorteners, typosquatting) | ✅ Live |
| Hidden href URL extraction (scans actual link destinations) | ✅ Live |
| Malicious attachment detection (.exe, .bat, .ps1, .iso, etc.) | ✅ Live |
| Brand impersonation detection (Microsoft, Google, Apple, PayPal, etc.) | ✅ Live |
| "Via" third-party sender relay detection | ✅ Live |
| Sender display name spoofing detection | ✅ Live |
| Non-US origin detection via IP geolocation | ✅ Live |
| 0–100 weighted risk score with color ring | ✅ Live |

---

## 📁 Files

| File | Purpose |
|---|---|
| `taskpane.html` | Main add-in UI and scanning engine |
| `commands.html` | Required Office JS stub |
| `ThreatScanv1.xml` | Bare minimum manifest |
| `ThreatScanv2.xml` | Full manifest with ribbon button (active) |
| `icon-16.png` | Add-in icon 16x16 |
| `icon-32.png` | Add-in icon 32x32 |
| `icon-80.png` | Add-in icon 80x80 |

---

## 🔍 How the Risk Score Works

Every finding adds weighted points to the score (capped at 100):

| Finding Type | Points |
|---|---|
| Malicious attachment | +45 |
| Brand impersonation | +40 |
| Sender spoofing | +40 |
| Suspicious links | +35 |
| Phishing keywords (1–2 hits) | +15 |
| Phishing keywords (3–5 hits) | +25 |
| Phishing keywords (6+ hits) | +35 |
| Non-US origin | +20 |
| Via third-party relay | +15 |
| Social engineering (1–2 hits) | +10 |
| Social engineering (3–5 hits) | +18 |
| Social engineering (6+ hits) | +25 |
| External sender | +5 |
| HTTP links | +5 |

**Combination multiplier:** When 3 or more threat categories are detected simultaneously, the score receives a 1.2× confidence boost.

**Social engineering escalation:** 3 or more social engineering hits automatically escalate from WARNING to CRITICAL.

| Score | Risk Level |
|---|---|
| 0 | ✅ CLEAN |
| 1–25 | 🟢 LOW RISK |
| 26–55 | 🟡 MODERATE |
| 56–80 | 🔴 HIGH RISK |
| 81–100 | 🚨 CRITICAL |

---

## 🔐 Permissions

This add-in uses **ReadItem** permission (minimum available):
- ✅ Reads the currently selected email only
- ❌ Cannot send, modify, or delete emails
- ❌ Cannot access other emails or folders
- ❌ Does not transmit data externally (all scanning is client-side)

---

## 📋 Version History

| Version | Date | Changes |
|---|---|---|
| v1.0.2 | 2026-04-01 | Added brand impersonation detection, "via" third-party sender detection, hidden href URL scanning, expanded suspicious link patterns, updated scoring weights |
| v1.0.1 | 2026-03-31 | Fixed headers not defined error, added getHeaders and getHtmlBody functions, fixed null safety in scanning engine |
| v1.0.0 | 2026-03-27 | Initial release — phishing keywords, social engineering detection, suspicious link scanning, malicious attachment detection, non-US origin detection, 0–100 risk score |

---

*ThreatScan v1.0.2 · 7Networks Security*
