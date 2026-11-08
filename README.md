# NEXA SHOP MANAGER 2.0

Offline-first static PWA by JS NEXA HUB. No build command, Node/npm, backend, login server, or paid service required.

## Deploy on Netlify

1. Extract `NEXA_SHOP_MANAGER_V2.zip`.
2. Upload the **extracted folder that directly contains `index.html`** to https://app.netlify.com/drop.
3. Prefer upgrading the **same Netlify site and same URL/origin** as Version 1 to give the new version access to existing browser storage.
4. Open the HTTPS link in Safari or Chrome. On iPhone: Safari → Share → Add to Home Screen.
5. Perform a JSON backup on the original Version 1 app **before** replacing it, and keep the downloaded file in a safe location.

## Data safety and migration

- Version 1 uses localStorage key `nexa-shop-manager-v1`.
- Version 2 stores a snapshot in IndexedDB database `nexa-shop-manager-v2`, object store `document`.
- If no Version 2 data exists, Version 1 records are copied into Version 2; **the Version 1 LocalStorage key is not deleted or edited**.
- If a storage write fails, the app displays an error. Do not delete browser data as troubleshooting.
- Data is **per device and per website origin**; a new Netlify site/address will not automatically contain the old device data. Use backup/restore on the destination origin.
- A JSON backup is not automatic cloud sync. Perform backups regularly. Manual reminder appears after 24h since the last backup when app opens.
- IMPORTANT: Previous Version 1 clients cannot read new Version 2 records. Keep a V2 JSON backup before rolling back.

## Features

Quick amount-only cash sales, customer credit ledger and payments, cash/bank separation, expense tracking, cash in/out, denomination counting, 5-step closing, staff labels, audit corrections, seven-day charts, local insights, classic/modern/detailed PNG statements, iOS/Android Web Share file support (with PNG download fallback), App PIN lock, JSON backup/restore, CSV export, PWA service worker, responsive dark/light UI.

## Financial calculation

`Expected cash = opening + cash sales + cash credit collections + other cash in - cash expenses - other cash out`

Credit sales, bank collections and bank expenses are excluded from cash. Finalized days are locked. Edits are represented as voided original records with replacement transactions and audit logs.

## Known limitations / verification still needed

- Local-only: no remote owner dashboard, automatic sync, true security boundary between staff profiles, or automatic WhatsApp sending.
- Web Share API file attachment support depends on browser, operating system, and WhatsApp installation. On unsupported devices, download the PNG and attach it manually.
- PIN is a local convenience lock, not server-backed authentication or a tamper-proof security system.
- Existing data model amounts use decimal JavaScript numbers; upgrade does not change the legacy value model. Validate money-specific rounding with real business records before commercial rollout.
- Migration compares per-table record counts and retains original records but is not yet a comprehensive forensic reconciliation of every possible corrupted legacy record.
- App uses a versioned static shell cache; verify service worker updates after uploading a new version.
- Browser automation and real-device iPhone/WhatsApp tests were not available in the build environment. Must be verified on actual devices before business use.
- Some CSV and PNG exports include personal/customer transaction data. Share and store securely.
