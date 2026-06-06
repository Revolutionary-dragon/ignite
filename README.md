# 🔥 Ignite — Event Ticketing Platform

> A production-grade, self-service event ticketing platform built for live events in Nairobi, Kenya. No third-party platforms. No commissions. Built from scratch with vanilla JavaScript, Firebase Realtime Database, and deployed on GitHub Pages.

🔗 **Live Site:** [revolutionary-dragon.github.io/ignite](https://revolutionary-dragon.github.io/ignite)

---

## 📸 Overview

Ignite is a real-world ticketing system designed to handle the full event lifecycle — from buyer purchase to door check-in — with zero reliance on paid ticketing services. Built for African events where M-Pesa is the dominant payment method.

---

## ✨ Features

### Buyer Side
- Animated event landing page with fire/ember visual theme
- 3-step ticket purchase flow (details → M-Pesa payment → reference submission)
- Real-time submission to Firebase Realtime Database
- Instant ticket generation with unique code and QR
- Screenshot-ready ticket design with IGNITE VERIFIED stamp

### Organizer Dashboard
- Password-protected access
- Live attendee list synced from Firebase in real time across all devices
- Pending / Confirmed / Checked-In status management
- One-click ticket confirmation
- **Send via WhatsApp** — opens WhatsApp with buyer's number and ticket details pre-typed
- Live revenue tracker
- Door check-in verification panel

### Security & Anti-Forgery
- Every QR code encodes: platform ID, unique ticket code, attendee name, amount, event ID
- QR verification checks against Firebase — not just the code itself
- Once checked in, ticket is permanently marked as used — duplicate scans rejected
- Forged or screenshot-copied tickets fail at the door
- Organizer dashboard is password protected

### Door Check-In
- Type or scan ticket code at entrance
- Instant green ✓ or red ✗ response
- Works on any phone browser — no app needed
- Marks ticket as used in Firebase in real time

---

## 🛠️ Tech Stack

| Layer | Technology |
|---|---|
| Frontend | Vanilla HTML, CSS, JavaScript |
| Database | Firebase Realtime Database |
| QR Generation | QRCode.js (Error Correction Level H) |
| Fonts | Google Fonts (Syne, Space Mono, Instrument Sans) |
| Hosting | GitHub Pages |
| Payment | M-Pesa (manual verification flow) |

---

## 🏗️ Architecture

```
Buyer (any device/browser)
    │
    ▼
ignite.html (GitHub Pages — static)
    │
    ├── Form submit → Firebase Realtime Database
    │                     │
    │                     └── Ticket code generated + stored
    │
Organizer (any device)
    │
    ▼
ignite.html → Organizer Tab (password: LIVEVENT1ST)
    │
    ├── Real-time listener on Firebase
    ├── Confirms payment → ticket visible
    ├── Generates QR ticket
    ├── Sends via WhatsApp deeplink
    └── Door check-in → marks used in Firebase
```

---

## 💳 M-Pesa Payment Flow

1. Buyer enters details on the site
2. Site shows organizer's M-Pesa number and exact amount
3. Buyer sends payment and copies the M-Pesa reference from their SMS
4. Buyer submits reference — stored in Firebase instantly
5. Organizer verifies payment, confirms on dashboard
6. Ticket + QR generated, sent via WhatsApp
7. At the door: code/QR scanned, Firebase checked, entry granted or denied

---

## 🚀 How to Deploy Your Own

1. Clone the repo:
```bash
git clone https://github.com/Revolutionary-dragon/ignite.git
```

2. Create a Firebase project at [console.firebase.google.com](https://console.firebase.google.com)

3. Enable Realtime Database in test mode

4. Register a web app and copy your config keys

5. Replace the `firebaseConfig` object in `ignite.html` with your keys

6. Update the M-Pesa number and account name in the HTML

7. Push to GitHub and enable GitHub Pages

8. Share your link

---

## 🔐 Security Notes

- Organizer password is client-side (sufficient for single-organizer events)
- Firebase rules should be tightened for production multi-event use
- For full production security, implement Firebase Authentication

---

## 📁 Project Structure

```
ignite/
├── ignite.html     # Complete single-file application
└── README.md       # Documentation
```

---

## 🗺️ Roadmap

- [ ] Multi-event support (multiple events on one platform)
- [ ] M-Pesa Daraja API integration (automatic payment confirmation)
- [ ] Custom domain (ignite.co.ke)
- [ ] QR camera scanner for door check-in
- [ ] SMS ticket delivery via Africa's Talking
- [ ] Analytics dashboard
- [ ] White-label for other organizers

---

## 👨‍💻 Built By

**Marvelle** — BSc Data Science, KCA University Nairobi.
Building real products, not just coursework.

GitHub: [@Revolutionary-dragon](https://github.com/Revolutionary-dragon)

---

## 📄 License

MIT — free to use, adapt, and build on.
