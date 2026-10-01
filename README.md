<div align="center">
  <img width="120" height="120" alt="OpenQR Studio" src="https://github.com/user-attachments/assets/2a27c648-8b50-4366-a103-eb8335dc0137" />
  <h1>OpenQR Studio</h1>
  <p><strong>Free, open-source QR code generator. No account, no watermark, no server.</strong></p>
  <p>Live at <a href="https://openqrstudio.com">openqrstudio.com</a></p>
</div>

---

## 🔍 Overview

OpenQR Studio lets anyone create a styled QR code in seconds and download it as a sharp PNG or editable SVG. Everything runs in the browser. Nothing is uploaded, nothing expires, no paywalls and there is no sign-up required.

## ✨ Features

- **9 content types**: Website, plain text, WhatsApp, email, phone, SMS, Wi-Fi, vCard and location
- **Custom shapes**: 7 body patterns (square, rounded, circle, gapped, vertical bars, diamond, heart) and 5 eye styles for both corner frames and corner dots
- **Colour options**: Solid colour or a linear gradient with a direction dial, plus a background colour picker and transparent background option
- **Logo**: Upload your own (PNG, JPG, SVG, up to 5 MB) or pick one of 16 presets (10 brand icons, 6 generic icons). Scale it between 10%, 20%, 25% and 30%
- **Margin**: Quiet-zone slider from 0 to 10 modules
- **Export**: PNG at 128, 256, 512 or 1024 px (default), and SVG with full gradient and logo support
- **Local library**: Save up to 5,000 codes to IndexedDB. Search, sort, edit and delete from the My QR codes page
- **Backup and restore**: Export the full library as a single JSON file and re-import it on any device
- **Live preview**: The code redraws as you type, debounced so fast typing stays fluid
- **Contrast warning**: Flags low-contrast colour combinations before you download
- **Privacy**: The engine runs entirely in the browser via [qrcode-generator](https://github.com/kazuhikoarase/qrcode-generator). No analytics, no ads, no external requests at runtime
- **Optional sign-in**: Sign in with Google or email to sync up to 5 codes across devices for free. Local codes stay private to your browser and are never uploaded unless you sign in.

## 🛠 Tech stack

| Layer | What |
|---|---|
| QR matrix | [qrcode-generator](https://github.com/kazuhikoarase/qrcode-generator) v2.0.4 (MIT) |
| SVG renderer | Custom (`js/engine.js`). Compound paths, gradient support, logo embedding |
| Icons | [Lucide](https://lucide.dev) inline SVG (ISC) |
| Preset logos | [simple-icons](https://simpleicons.org) (CC0). Brand marks belong to their owners, see `js/logos.js` |
| Storage | IndexedDB via `js/library.js` |
| Export | Canvas-based PNG rasterisation via `js/export.js` |
| Hosting | Static. No backend, no build step |

## 📁 Project structure

```
/                          Landing page (index.html)
/create/                   QR creation app (index.html)
/library/                  Saved codes (index.html)
/login/                    Sign-in page (index.html)
/css/
  style.css                Shared tokens, landing page, FAQ
  app.css                  App shell, sidebar, steps, designer, library cards
  login.css                Sign-in page layout and card styles
/js/
  vendor/qrcode.js         qrcode-generator UMD bundle
  engine.js                QR matrix → styled SVG (shapes, eyes, gradients, logos)
  payloads.js              Content type builders + form validation
  icons.js                 Lucide icons inline (no CDN)
  logos.js                 Preset logo data URLs (simple-icons + Lucide)
  export.js                PNG rasterisation, SVG download, logo file upload
  library.js               IndexedDB CRUD (codes + folders), validation
  backup.js                JSON export/import with full validation
  supabase.js              Supabase client initialisation
  auth.js                  Session management, cloud save/delete, quota, sidebar
  dialog.js                Themed confirmation dialog (replaces browser confirm())
  config.js                Site settings (donate URL)
  donate.js                Optional donate button
  home.js                  Landing page: hero QR, icon hydration
  app.js                   Create page: 3-step flow, designer, save (local or cloud)
  lib-page.js              Library page: card grid, search, sort, edit, backup
/favicon.svg               White rounded-square icon matching the app logo style
```
## 🔐 Optional sign-in & sync

Signing in is entirely optional. Without an account, everything works locally because codes are saved in your browser and never leave your device.

If you want your codes available across multiple devices or browsers, you can sign in with Google or a magic email link. Signed-in codes are stored in a private Supabase database, separate from your local codes. Local codes stay untouched when you sign in or out.

| Plan | Codes stored | Price |
|---|---|---|
| No account | Up to 5,000 (local only) | Free |
| Free account | Up to 10 (cloud sync) | Free |
| One-time purchase *(coming soon)* | Up to 200 (cloud sync) | 10€ |

## 🌐 Browser support

Any modern browser (Chrome, Firefox, Safari, Edge). The library uses IndexedDB, which Safari clears after 7 days of no interaction, so use the Backup function to keep your codes safe.

## ☕ Support the project

OpenQR Studio is free and has no ads. A donation helps cover the domain maintenance cost. It is entirely optional.

[<img width="240" height="62" alt="buymeacoffee" src="https://github.com/user-attachments/assets/c855b44d-9856-407d-a03d-b4fb75ab459a" />](https://buymeacoffee.com/openqrstudio)  [<img width="240" height="62" alt="paypalme" src="https://github.com/user-attachments/assets/92bff645-3dd5-42f5-9a7a-bc53c75d966f" />](https://paypal.me/LiinkPK)

> Any amount is appreciated and goes directly toward hosting costs.

## 📄 Licence

[![Licence: MIT](https://img.shields.io/badge/Licence-MIT-blue.svg)](/LICENCE)

This project is licensed under the MIT Licence. You are free to use, modify, and distribute this software under the conditions stated in the [LICENCE](/LICENCE) file.

Brand icons in `js/logos.js` come from [simple-icons](https://simpleicons.org) (CC0) but the marks themselves belong to their respective owners.

---

*Made by [LiinkPK](https://github.com/LiinkPK)*
