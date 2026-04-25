[README.md](https://github.com/user-attachments/files/27055585/README.md)
# 🧾 GST Invoice App

> A zero-dependency, single-file GST-compliant invoice manager — built with React, runs entirely in the browser.

![HTML](https://img.shields.io/badge/HTML-Single%20File-orange?style=flat-square&logo=html5)
![React](https://img.shields.io/badge/React-18-blue?style=flat-square&logo=react)
![License](https://img.shields.io/badge/License-MIT-green?style=flat-square)
![Offline](https://img.shields.io/badge/Offline-Ready-brightgreen?style=flat-square)
![No Build](https://img.shields.io/badge/Build%20Step-None-lightgrey?style=flat-square)

---

## 📌 Background

A client in the **port & shipping services industry** was managing all their invoices in Excel. Their system couldn't run heavy ERP software, and cloud-based tools were overkill. They needed something:

- That runs on any device, including older machines
- Works without internet after the first load
- Produces proper **GST Tax Invoices** ready to print or share as PDF
- Exports to Excel for their accountant

The result: one `.html` file. Download it. Open it. Done.

---

## ✨ Features

### 🧾 Invoicing
- GST-compliant Tax Invoices — **SGST+CGST** (intra-state) and **IGST** (inter-state) with auto-calculation
- **Auto invoice numbering** in `NNN/MM/YY-YY` format (serial / month / fiscal year), resets every April
- Billing party + separate Consignee support
- Vessel / Ship name, Port of Service, Job No., PO No., E-Way Bill fields — built for port & logistics workflows
- Reverse charges, insurance, freight, rounding off
- Multi-currency support with exchange rate
- Custom remarks / notes section

### 🖨 Print & Export
- **A4 print** — Original + Duplicate on one job, no extra clicks
- **PDF export** via html2pdf
- **Excel Summary** — 3 sheets: Invoice Summary, Line Items, GST breakup
- **Full Excel Report** — every field, one row per item (great for accountants)
- **JSON backup** — full data export, re-importable

### 💾 Storage & Backup
- **3-layer storage**: IndexedDB (primary) → localStorage (mirror) → optional linked local JSON file
- **Auto-backup** on every save — JSON file downloads automatically
- **Merge import** — restore from any backup without overwriting existing data
- Up to **4-step undo**

### 🎨 UI
- Dark mode (persisted)
- Logo upload — appears on invoice header and in Excel exports
- Party & vessel **autocomplete** — learns from your own invoice history
- Configurable date format: `DD/MM/YYYY` or `YYYY-MM-DD`
- Fully responsive — works on mobile and tablet

### 📡 Offline
- Service Worker caches CDN scripts on first load
- After that, works **completely offline**

---

## 🚀 Getting Started

**No installation. No npm. No build step.**

```
1. Download invoice_app.html
2. Open in Chrome, Edge, or Firefox
3. First open needs internet (loads React + libs from CDN)
4. After that — fully offline
```

On first launch:
1. Go to **⚙ Settings**
2. Fill in your company name, address, GSTIN, PAN, bank details
3. Upload your logo
4. Hit **＋ New Invoice**

---

## 🏗 Tech Stack

| Layer | Technology |
|---|---|
| UI Framework | React 18 (UMD build, no bundler) |
| JSX Transpiler | Babel Standalone |
| PDF Export | html2pdf.js |
| Excel Export | SheetJS + custom OOXML builder (styled .xlsx) |
| Storage | IndexedDB + localStorage |
| Offline | Inline blob Service Worker |
| Styling | Vanilla CSS with CSS custom properties |

Everything is loaded from CDN on first use and cached by the Service Worker. Zero local dependencies.

---

## 📁 Repo Structure

```
invoice_app.html    ← The entire app (~3000 lines, self-contained)
README.md
```

---

## 🖨 Invoice Layout

Each print run produces **two copies on one A4 sheet**:

| | |
|---|---|
| **Page 1** | ORIGINAL |
| **Page 2** | DUPLICATE |

Both pages include: company letterhead + logo, billing & consignee details, itemised service/goods table with HSN/SAC codes, GST summary, and jurisdiction line.

---

## 📊 Export Reference

| Option | Format | What's inside |
|---|---|---|
| 🖨 Print Summary | Browser print | Landscape A4 invoice list |
| 📊 Export as Summary | `.xlsx` | Summary + Line Items + GST sheets |
| 📋 Export as Report | `.xlsx` | All fields, one row per item |
| 📦 Export as JSON | `.json` | Full data backup, re-importable |

---

## ⚙️ Customisation

Edit the `CO` object near the top of the `<script>` block:

```js
const CO = {
  name:   'YOUR COMPANY NAME',
  l1:     'Address Line 1',
  l2:     'City, State, Country',
  gstin:  'YOUR_GSTIN',
  pan:    'YOUR_PAN',
  bank:   'Bank Name',
  acc:    'Account Number',
  branch: 'Branch Name',
  ifsc:   'IFSC Code',
  email:  'email@example.com',
  ph:     '+91 XXXXXXXXXX',
  web:    'www.yoursite.com',
};
```

Or skip the code entirely — use **⚙ Settings → Upload Logo** and the company info fields inside the app.

---

## 💾 Backup & Restore

| Action | How |
|---|---|
| Auto-backup | Downloads automatically on every **Save & Preview** |
| Manual backup | **⚙ Settings → Backup Now** |
| Restore | **⬇ Import** → pick any `Invoice_Backup_*.json` |
| Excel restore | **⬇ Import** → pick a Full Export `.xlsx` |

Backups **merge** — existing invoices are never overwritten. Duplicates are skipped automatically.

> All data lives on your device. Nothing is ever sent to a server.

---

## 🔑 Invoice Number Format

```
NNN / MM / YY-YY
 │     │    └── Fiscal year (e.g. 26-27)
 │     └─────── Month (01–12)
 └───────────── Serial number (resets each fiscal year)
```

Example: `003/04/26-27` = 3rd invoice, April 2026, FY 2026-27.  
Fiscal year runs **April → March**.

---

## 🛡 Browser Support

| Browser | Status |
|---|---|
| Chrome / Edge | ✅ Full support |
| Firefox | ✅ Full support |
| Safari | ✅ Works (Service Worker limited on iOS) |
| IE / Old browsers | ❌ Not supported |

---

## 📄 License

MIT — free to use, modify, and distribute.

---

*Built as a lightweight alternative to Excel-based invoicing for a port services client. No servers were harmed in the making of this app.*
