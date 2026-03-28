# 🛡️ ThreatScan — Outlook Email Security Add-in
**Built by Gritty | 7Networks Security**

ThreatScan is a post-delivery threat indicator tool for Microsoft Outlook. It analyzes delivered emails for phishing, social engineering, malicious attachments, and suspicious senders — giving users and IT staff actionable intelligence after an email lands in the inbox. It provides a 0–100 risk score with color-coded results and itemized threat findings.

---

## ✅ Features

| Feature | Status |
|---|---|
| Phishing keyword detection | ✅ Live |
| Social engineering language detection | ✅ Live |
| Suspicious link scanning (HTTP, IP, URL shorteners) | ✅ Live |
| Malicious attachment detection (.exe, .bat, .ps1, etc.) | ✅ Live |
| External sender warnings | ✅ Live |
| Sender display name spoofing detection | ✅ Live |
| 0–100 risk score with color ring | ✅ Live |

---

## 📁 Files

| File | Purpose |
|---|---|
| `taskpane.html` | Main add-in UI and scanning engine |
| `commands.html` | Required Office JS stub |
| `ThreatScanv1.xml` | Bare minimum manifest (deployed) |
| `ThreatScanv2.xml` | Full manifest with ribbon button |
| `icon-16.png` | Add-in icon 16x16 |
| `icon-32.png` | Add-in icon 32x32 |
| `icon-80.png` | Add-in icon 80x80 |

---

## 🔍 How the Risk Score Works

Every finding adds points to the score (capped at 100):

| Severity | Points | Examples |
|---|---|---|
| Critical | +30 | Phishing keywords, suspicious links, dangerous attachments, spoofed sender |
| Warning | +15 | Social engineering language, external sender, Reply-To mismatch |
| Info | +5 | HTTP links, attachments present |

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

*ThreatScan v1.0.0 · 7Networks Security*
