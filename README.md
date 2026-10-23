# SmartBiz Booking & Ordering Engine

[![Deploy with Vercel](https://vercel.com/button)](https://vercel.com/new/clone?repository-url=https%3A%2F%2Fgithub.com%2FOlumidenana%2Fbiz-booking-engine)

A production-ready booking and online ordering engine designed specifically for **Beauty Salons / Lash Techs** and **Food & Snack Vendors**.


Connected with:
- 💳 **Paystack**: Automatic deposit and full-amount card/transfer checkout (stops fake bank alert fraud).
- 📊 **Google Sheets**: Automatic live logging for non-tech-savvy business owners.
- 💬 **Instant Telegram & WhatsApp Notifications**: Pings the owner immediately when money is paid.
- 📱 **Mobile-First UX**: Ultra-fast, luxury UI built to be linked directly in Instagram / TikTok bios.

---

## 🚀 Quick Start (Running Locally)

```bash
# Navigate to the project
cd biz-booking-engine

# Start the server
node src/server.js
```

Open your browser to:
* **Demo Showcase Hub:** `http://localhost:5000`
* **Lash & Nail Studio Template:** `http://localhost:5000/beauty`
* **Shawarma & Doughnuts Template:** `http://localhost:5000/food`
* **Vendor Admin Live Orders:** `http://localhost:5000/admin`

---

## 📁 System Architecture

```text
biz-booking-engine/
├── .env                  # Paystack keys, Telegram bot token, Google Sheet URL
├── google-apps-script.js # 1-click script for client's Google Sheet
├── src/
│   ├── server.js         # Express API & Paystack webhook handler
│   └── services/
│       ├── paystack.js   # Paystack transaction init & verify (with demo simulator)
│       ├── googleSheets.js# Google Sheets sync & local fallback store
│       └── notifications.js# Telegram bot alerts & WhatsApp deep-links
└── public/
    ├── index.html        # Sales showcase & pitch page
    ├── beauty/           # Lash, Nail & Hair appointment booking template
    ├── food/             # Shawarma, Doughnuts & Grills ordering template
    └── admin/            # Real-time vendor order & booking dashboard
```

---

## ⚡ Connecting to a Real Client (Takes < 5 Minutes)

### 1. Paystack Setup
1. Ask the business owner for their **Paystack Public & Secret Key** (or use your own subaccount if charging commission).
2. Set in `.env`:
   ```env
   PAYSTACK_SECRET_KEY=sk_live_xxxx...
   PAYSTACK_PUBLIC_KEY=pk_live_xxxx...
   ```
3. Set their Paystack Dashboard webhook URL to:
   `https://your-domain.com/api/paystack/webhook`

### 2. Google Sheets Setup (The Easy Way)
1. Open a new Google Sheet for the client.
2. Click **Extensions > Apps Script**.
3. Copy and paste the code from [google-apps-script.js](file:///C:/Users/giant/.gemini/antigravity/scratch/biz-booking-engine/google-apps-script.js).
4. Click **Deploy > New Deployment > Web App** (Set *Who has access* to **Anyone**).
5. Copy the generated Web App URL into `.env`:
   ```env
   GOOGLE_SHEET_WEBHOOK_URL=https://script.google.com/macros/s/.../exec
   ```
*Every time an appointment is booked or food is ordered, a new row is automatically appended to their Google Sheet!*

### 3. Telegram Alerts (100% Free & Instant)
1. Message `@BotFather` on Telegram to create a bot (copy token).
2. Create a private group or chat with the owner, add `@userinfobot` to get Chat ID.
3. Put both in `.env`:
   ```env
   TELEGRAM_BOT_TOKEN=123456:ABC-DEF...
   TELEGRAM_CHAT_ID=-100xxxxxxx
   ```

---

## 🎯 The Google Maps Outreach Script (How to Get Clients)

1. Open Google Maps in your target city (e.g. Lagos, Abuja, Port Harcourt, Accra, London, etc.).
2. Search:
   - *"Lash tech in Lekki"*
   - *"Nail studio in Ikeja"*
   - *"Shawarma near me"*
   - *"Doughnut bakery in [City]"*
3. Record a 45-second screen recording showing the booking/ordering flow on your phone.
4. Send them a WhatsApp or Instagram DM:

> *"Hi [Business Name]! Loved your work on Google Maps/Instagram. I noticed right now you take orders and bookings manually in DMs, which means you have to deal with missed messages, "is this slot free?" chats, and chasing bank transfers.*
> 
> *I built a sleek 1-minute booking system specifically for [lashes / shawarma vendors] that collects Paystack deposits upfront and drops confirmed orders straight onto your WhatsApp and Google Sheet.*
> 
> *Here’s a quick 30-second video of how it looks for a customer: [Link to screen record]*
> 
> *I can set this up with your exact menu/prices and Paystack account today for a one-time launch fee of ₦35,000. Would you like me to send you the test link?"*
