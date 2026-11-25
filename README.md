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

## V9 — PHP and JPY
Select currency in each account. Existing accounts default to PHP. Amounts are stored in hundredths for compatibility; JPY input must be whole yen. Cross-currency transfers require the actual received amount, and the effective rate is calculated from the two amounts. Summary and Insights currency selectors keep totals separate. TXT backups and monthly reports include currency and received amounts. Do not restore V9 backups into older versions. Currency relabeling is blocked for accounts with transfers.

## V11 — Dues and scheduled payments
- Tap outside a popup to dismiss it without saving. Dues is a separate bottom navigation tab, with Installments and Utilities filters.
- Add an installment schedule with the first due date, monthly amount, and number of payments (1–120). Dates clamp to the last valid day of shorter months. A utility is a one-time reminder. Edit or delete each unpaid payment separately.
- From a new expense, choose Schedule as installment or utility instead. From an existing expense, schedule future payments without changing the original expense. Mark as paid records an expense on the selected account on the actual payment date; unpaid items never affect balances, history, reports or insights. Deleting the linked expense reopens the due. Editing the expense retains its link. Credit account entries are installment charges, not card repayments; avoid recording the full purchase as well if using this tracking method.
- Upcoming payments on Home lists card statements and up to six earliest unpaid scheduled payments; View dues shows all. Reminders are in-app, not push notifications.
- Dues are stored in the existing metadata store and included in TXT transfers. Restoring older backups replaces dues with an empty list. Accounts with dues cannot be deleted or have currency changed until their dues are resolved (paid due records are retained).
- JavaScript syntax checked; browser interactions not verified.


V11: Dues are grouped by plan, with colored full-width cards, hidden paid history, individual payment editing and additional payment periods. Legacy schedules are grouped only when their matching dates and identifiers are unambiguous.

## V12 — Dues layout refinement
Removed the card chevron and duplicate detail heading. Edit/check and close icons sit inside the detail card. Payment actions sit directly below the amount on the right. No data schema changes.
