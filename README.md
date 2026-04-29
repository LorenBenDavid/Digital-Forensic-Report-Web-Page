# Digital Forensic Investigation Report
### NIST CFReDS — Data Leakage Case | PC Disk Image Analysis

> A fully self-contained, interactive web report presenting a complete digital forensic investigation of the NIST CFReDS Data Leakage case — built for both technical analysts and non-technical readers.

![HTML](https://img.shields.io/badge/HTML-Single%20File-orange?style=flat-square&logo=html5)
![CSS](https://img.shields.io/badge/CSS-Inline-blue?style=flat-square&logo=css3)
![JS](https://img.shields.io/badge/JavaScript-Vanilla-yellow?style=flat-square&logo=javascript)
![License](https://img.shields.io/badge/License-Educational-green?style=flat-square)

---

## Overview

This project is a single `forensic_report.html` file that presents the complete findings of a digital forensics investigation into the **NIST CFReDS Data Leakage Case** — a publicly available forensic exercise in which an employee named *Iaman Informant* stole confidential project files and attempted to cover their tracks.

The report is designed to be readable by **anyone**, including non-technical users, while still containing the full technical depth expected of a professional forensic report. All 40 investigation questions (Q1–Q40) are answered and documented.

---

## The Case

| Field | Detail |
|-------|--------|
| **Suspect** | Iaman Informant |
| **Account** | `informant` on `INFORMANT-PC` |
| **OS** | Windows 7 Ultimate SP1 |
| **Active Period** | March 22–25, 2015 |
| **Files Stolen** | 24 confidential project files |
| **Exfiltration Methods** | Google Drive · USB Flash Drive · CD-R |
| **Anti-Forensic Tools** | Eraser 6.2 + CCleaner |
| **Conspirator** | `spy.conspirator@nist.gov` |
| **Disk Image Format** | DD (raw) |
| **Hash Verified** | MD5 + SHA-1 ✅ |

---

## Report Sections

| # | Section | Key Content |
|---|---------|-------------|
| 0 | **Hero Header** | Stats dashboard: active days, files stolen, exfiltration methods, recovered emails |
| 1 | **Case Overview** | Plain-language explanation of data leakage + full suspect profile card |
| 2 | **System Information** | Hash verification, partition table, OS details, timezone & network config |
| 3 | **User Accounts** | All 4 accounts with logon counts, last logon timestamps, and significance notes |
| 4 | **Timeline of Events** | Color-coded vertical timeline across all 4 days (normal / suspicious / anti-forensic) |
| 5 | **Web Searches & Browser History** | Categorized search keyword chips + key visited URLs table |
| 6 | **Email Communications** | Chat-style email thread with 4 forensically recovered deleted emails |
| 7 | **Applications & Anti-Forensic Tools** | Installed apps table + Eraser & CCleaner deep-dive + execution timeline |
| 8 | **Data Exfiltration Methods** | Detailed breakdown of all 3 exfiltration vectors with evidence |
| 9 | **File Renaming** | All 24 original → disguised filename mappings |
| 10 | **Evidence Summary Table** | Searchable Q1–Q40 quick-reference with color-coded severity badges |
| 11 | **Glossary** | 24 technical terms explained in plain language |

---

## Features

### Visual & Interactive
- **Dark forensic aesthetic** — inspired by real investigation dashboards (`#0d1117` background, GitHub-style palette)
- **Scan-line texture** overlay on hero header via CSS `repeating-linear-gradient`
- **Blinking cursor** animation on the main title
- **Color-coded timeline** with glowing dots (blue = normal, red = suspicious, amber = anti-forensic)
- **Chat-style email thread** with deleted emails shown in red with recovery badges
- **Evidence chips** categorized by severity (red / amber / gray)

### Functionality
- **Fixed navigation bar** with smooth-scroll to all sections
- **Active section highlighting** in the nav as you scroll
- **Reading progress bar** at the top of the page
- **Collapsible sections** — click any section header to expand/collapse
- **Sortable tables** — click any column header to sort ascending/descending
- **Live search filter** on the Q1–Q40 Evidence Summary table
- **Dark / Light mode toggle**
- **Back-to-top button** (appears after scrolling)

### Technical
- **100% self-contained** — single HTML file, zero external JavaScript dependencies
- **Responsive design** — works on desktop, tablet, and mobile (hamburger nav on small screens)
- **Print stylesheet** — clean black-on-white output when printing to PDF
- **Accessible** — semantic HTML5, ARIA labels, keyboard navigation, WCAG AA contrast, proper heading hierarchy

---

## Tools Used in the Investigation

| Tool | Purpose |
|------|---------|
| **Sleuth Kit (CLI)** | Disk image analysis, file system parsing, partition examination |
| **hivexsh** | Windows Registry hive analysis (SAM, SYSTEM, SOFTWARE, NTUSER.DAT) |
| **python-evtx** | Windows Event Log parsing for logon/logoff events |
| **pypff** | Outlook OST/PST email file analysis and email recovery |
| **SQLite3** | Browser history analysis (Chrome), Google Drive database recovery |
| **python3** | Automation, parsing, and data extraction scripts |

---

## Key Findings Summary

### The 4-Day Attack Timeline

```
Day 1 (Mar 22) — Setup
  └── OS installed, IE11 downloaded, Office 2013 installed

Day 2 (Mar 23) — Planning
  ├── 8+ suspicious searches: "data leakage methods", "how to leak a secret", "anti-forensics"
  ├── Browsed company network drive \\10.11.11.128\secured_drive
  ├── Opened 2 confidential files, renamed 4 with innocent names
  ├── Installed Google Drive
  └── Emailed Google Drive links to conspirator (later deleted)

Day 3 (Mar 24) — Exfiltration
  ├── Renamed 20 more secret files
  ├── Connected 2 USB flash drives (SanDisk Cruzer Fit)
  ├── Burned 4 Mastered CDs + 1 USB-style CD with 17 files
  └── Wrote resignation letter

Day 4 (Mar 25) — Cover-Up
  ├── Installed Eraser → ran secure file deletion
  ├── Installed CCleaner → cleaned traces → uninstalled CCleaner
  ├── Printed resignation letter to XPS format
  └── Final shutdown at 11:31
```

### Evidence That Survived the Cover-Up

Despite the use of Eraser and CCleaner, the following evidence was recovered:

- **4 deleted emails** recovered from the Outlook `.ost` file, including Google Drive links
- **Google Drive database WAL files** retained upload history after the main DB was deleted
- **Thumbcache** contained previews of 6 PowerPoint files — proving they were viewed
- **Prefetch files** confirmed execution of Eraser and CCleaner
- **USN Journal ($UsnJrnl)** logged all file rename operations with original names
- **ShellBag registry entries** confirmed USB folder browsing
- **LNK shortcut files** confirmed which files were opened and when

---

## File Structure

```
Digital-Forensic-Report-Web-Page/
├── forensic_report.html                   # Complete self-contained report
├── README.md                              # This file
└── PRD_DataLeakage_Forensic_Report.md     # Original product requirements document
```

---

## How to View

1. Clone or download the repository
2. Open `forensic_report.html` in any modern browser (Chrome, Firefox, Safari)
3. No server, no install, no dependencies required

```bash
git clone https://github.com/LorenBenDavid/Digital-Forensic-Report-Web-Page.git
cd Digital-Forensic-Report-Web-Page
open forensic_report.html   # macOS
# or
start forensic_report.html  # Windows
```

---

## Disclaimer

This report was created for **educational purposes** as part of a digital forensics coursework assignment. The case is based on the [NIST CFReDS](https://cfreds.nist.gov/) public dataset, which is freely available for forensic training and research.

No real individuals were investigated. All named accounts and email addresses in this report are part of the NIST exercise dataset.

---

## Author

**Loren Ben-David**  
April 2026

---

*© 2026 Loren Ben-David. All rights reserved.*
