[README.md](https://github.com/user-attachments/files/27055585/README.md)
# 🧾 Company Invoice App

A lightweight, **single-file** GST-compliant invoice management app built with React — no server, no installation, no heavy ERP required. Runs entirely in the browser.

---

## 🎯 Why This Exists

The client was managing invoices in old-school Excel spreadsheets. Their system couldn't handle heavy invoice software or cloud-based ERPs, and they needed something:

- Fast and lightweight
- Works offline after first load
- Printable as proper GST Tax Invoices (A4, Original + Duplicate)
- Exportable to Excel for accountants
- Runs on any device — desktop, tablet, or mobile

This single `.html` file solves all of that.

---

## ✨ Features

- **GST-Compliant Tax Invoices** — SGST/CGST and IGST support, auto-calculations
- **Auto Invoice Numbering** — format: `NNN/MM/YY-YY` (serial/month/fiscal year), resets each FY
- **Print Ready** — A4 portrait, Original + Duplicate on one print job
- **Excel Export** — Summary report, Line Items, GST summary sheets; or Full Report (one row per item)
- **JSON Backup & Restore** — auto-backup on every save, manual backup anytime, merge-import
- **Offline Support** — Service Worker caches CDN scripts after first load
- **Dark Mode** — persisted across sessions
- **Party & Vessel Autocomplete** — learns from your own invoices
- **Port of Service Dropdown** — all major Indian ports pre-loaded + custom option
- **3-Layer Storage** — IndexedDB (primary) + localStorage (mirror) + optional linked JSON file
- **Undo** — up to 4 steps back
- **Logo Upload** — appears on invoice header and Excel exports
- **Configurable date format** — DD/MM/YYYY or YYYY-MM-DD

---

## 🚀 Getting Started

1. Download `invoice_app.html`
2. Open it in any modern browser (Chrome, Edge, Firefox)
3. First open requires internet to load React/Babel from CDN — after that it works offline
4. Go to ⚙ **Settings** → fill in your company name, address, GSTIN, bank details
5. Upload your logo
6. Hit **+ New Invoice** and you're set

No npm. No build step. No server. Just one file.

<img width="1920" height="916" alt="image" src="https://github.com/user-attachments/assets/1aad7cf1-3bc7-40e7-a57a-9ded84ab3d80" />
<img width="1894" height="919" alt="image" src="https://github.com/user-attachments/assets/56f17628-6c41-4d7f-9227-4c658492f1e4" />
<img width="564" height="845" alt="image" src="https://github.com/user-attachments/assets/d7a5869a-4b59-43b5-ab84-e21818610876" />



---

## 🏗 Tech Stack

| Layer | Tech |
|---|---|
| UI Framework | React 18 (CDN, no build) |
| Transpiler | Babel Standalone |
| PDF Export | html2pdf.js |
| Excel Export | SheetJS (XLSX) — custom OOXML builder for styled output |
| Storage | IndexedDB + localStorage |
| Offline | Service Worker (inline blob SW) |
| Styling | Pure CSS with CSS variables (dark mode support) |

---

## 📁 File Structure

```
invoice_app.html     ← The entire app. Everything in one file.
README.md
```

---

## 🖨 Invoice Format

Each print produces **two copies** on one A4 sheet:
- **Page 1** — ORIGINAL
- **Page 2** — DUPLICATE

Both include: company header, billing & consignee details, itemized table with HSN/SAC, GST breakup, and jurisdiction line.

---

## 📊 Export Options

| Export | Format | Contents |
|---|---|---|
| Print Summary | Print dialog | Landscape A4 summary table |
| Export as Summary | `.xlsx` | 3 sheets: Summary, Line Items, GST |
| Export as Report | `.xlsx` | 1 sheet, all fields, one row per item |
| Export as JSON | `.json` | Full backup, re-importable |

---

## 💾 Backup Strategy

- Auto-backup JSON downloads on every **Save & Preview**
- Manual backup via **⚙ Settings → Backup Now**
- Import/merge from any previous backup via **⬇ Import**
- Optionally link a local JSON file for persistent auto-save

---

## ⚙ Customization

Edit the `CO` constant near the top of the `<script>` block to set your company details:

```js
const CO = {
  name: 'YOUR COMPANY NAME',
  l1: 'Address Line 1',
  l2: 'City, State, Country',
  gstin: 'YOUR_GSTIN',
  pan: 'YOUR_PAN',
  bank: 'Bank Name',
  acc: 'Account Number',
  branch: 'Branch Name',
  ifsc: 'IFSC Code',
  email: 'email@example.com',
  ph: '+91 XXXXXXXXXX',
  web: 'www.yoursite.com'
};
```

Or upload your logo via **⚙ Settings** — no code change needed.

---

## 🔒 Privacy

All data stays on your device. Nothing is sent to any server. Ever.

---

## 📄 License

MIT — use freely, modify as needed.

---

*Built for a client in the port & shipping services industry who needed a fast, reliable alternative to Excel-based invoicing without any heavy infrastructure.*
