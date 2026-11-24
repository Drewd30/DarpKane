# DarpKane V8

A mobile-first personal finance PWA with a purple Nunito interface. Application logic and styles are embedded in `index.html`. No backend or build step is required.

## What's new
- Account toolbar uses matching 44px icon buttons and a fixed flex alignment in normal and rearrangement modes.
- Insights use vertical column charts for six-month cash flow, income and spending categories, and spending by account.
- Settings → Device transfer: download TXT, copy text, paste text, or import TXT. The transfer includes accounts (including card colors, logos, order, hidden/excluded flags and billing settings), transactions, categories, profile name/photo and appearance. Legacy FinTrack JSON backups can still be imported. TXT contains structured JSON internally, not encryption. Keep it private. Review and confirm before replacing local records; restore is not a merge. Cancel leaves stored records unchanged.
- Settings → Monthly transactions → Request Monthly Transactions: select month and Excel (.xlsx), CSV or PDF, then Request. Reports contain every transaction in that month including transfers and adjustments, with amount in PHP, date, type, description, category, source, destination and notes. Excel is a real workbook with numeric amounts; CSV includes UTF-8 BOM and formula-injection protection. PDF is paginated and raster-rendered (not searchable text). No internet connection is needed to generate reports. Reports are not backups. QR transfer is not included.

## Existing features
Two-column account cards, drag-to-reorder, optional cash, debit/credit/cash filters, custom bank logos, asset exclusion, credit limits, estimated statements and due dates, transaction editing, transfers and card payments, monthly summaries, categories, profile photo, light/dark theme, local IndexedDB storage. Net worth is not displayed. Billing estimates depend on recorded transactions; no bank connection.

## Installation and updates
1. Back up your existing data before replacing files (V6 JSON or V8 TXT).
2. Extract the ZIP and upload all files into the same GitHub Pages directory. Keep the same site origin and path to retain browser storage. The database identifier/schema is unchanged, but migration on your own device should be verified.
3. Reload online to activate the new service worker. Install from the browser menu if supported. The app works offline after caching. Nunito loads from Google Fonts when available; offline fallback is system font.
4. Directly opening index.html may work in browsers permitting IndexedDB on file URLs; HTTPS/localhost is recommended for PWA and clipboard features. If clipboard access is denied, select and copy the transfer text manually.

## Files
- index.html — complete application
- sw.js — offline caching (V8)
- manifest.webmanifest — PWA metadata
- icon-192.png, icon-192.png, icon-512.png — app icons
- README.md — this guide

## Verification
JavaScript syntax checked. Sample Excel output reopened with openpyxl; PDF container inspected using pdfinfo with a mock canvas image. Live browser navigation was blocked by administrator policy on both file and localhost URLs, so UI interactions, actual browser PDF rendering and device migration remain unverified.

## V8 branding update
The purple koala artwork is embedded in the header and used for the browser favicon and PWA icons. Financial features and database identifiers are unchanged.
