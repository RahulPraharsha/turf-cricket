# Cricket Turf Manager

Mobile-first web app to manage **cricket turf bookings** and **drink sales per day** for a business, with role-based access. Everyone can view full details; only the admin can edit/delete.

## Features

- Login with username/password (session persists across refresh)
- **3 user accounts** (Srinivasa Rao, Varahala Rao, Sathi Babu) + **1 hidden admin** (Rahul)
- Add/view cricket turf bookings (customer, slot, turf, amount, status, contact)
- Add/view daily drink sales (item from stock list, qty, price, total)
- **Drinks in stock**: any user can add drink names to the stock list; selecting one when recording a sale
- **Complete visibility**: every user sees full details of all bookings and drink sales
- **No edits by users**: once recorded, only the admin can edit or delete
- Hidden admin: regular users never see an "Admin"/"Manage" tab or any edit-delete controls
- Each account has its own unique password; users can change their own password via the 🔑 button, and passwords must be unique across accounts
- Dashboard with daily totals & all-time totals
- Filter bookings/sales by date
- Prevents overlapping time slots for the same date & turf (e.g. 19:00-21:00 blocks another booking during that window)
- Bookings automatically show "completed" once their time slot has ended
- Each booking requires customer name, 10-digit mobile number, time slot, turf, and total amount; mobile and amount are mandatory
- Bookings track total revenue and collected payments; 💳 Pay records advance/balance payments (online simulated / cash / UPI), amounts cannot exceed balance due
- Revenue edit/delete remains admin-only
- In-app payment gateway: UPI payment uses the signed-in user's mobile number (not customer), and a demo card/Netbanking checkout; payment cannot exceed balance due
- Admin-only **Manage** panel: account management, password reset, data export (JSON), clear data

## Demo credentials

| Role   | Username    | Password     | Display name    |
|--------|-------------|--------------|-----------------|
| User   | srinivasa   | Srinivasa@2003 | Srinivasa Rao   |
| User   | varahala    | Varahala@2003  | Varahala Rao    |
| User   | sathi       | Sathi@2003     | Sathi Babu      |
| Admin  | rahul       | Rahul@2003     | Rahul           |

> The admin account is intentionally not advertised inside the app UI. Users only see "Home / Bookings / Drinks". The "Manage" tab appears only after signing in as admin.

## Run (browser)

Open `index.html` in any modern browser (mobile or desktop). Data is stored in the browser's `localStorage` — no server required. Offline caching works after first load.

## Install on mobile (PWA)

This app is now a Progressive Web App. To install it like a mobile app:

1. Host the folder on any **HTTPS** static host (GitHub Pages, Netlify, Vercel) —or— run a local server on your PC:
   - Double-click `start-server.bat` (needs Node.js) then open `http://<your-pc-ip>:8080` on the phone over the same Wi-Fi.
2. Open that URL in Chrome (Android) or Safari (iOS).
3. Tap **Add to Home Screen / Install app**. It will open in standalone mode without browser bars.
4. After first load it works offline via service worker.

> Opening `index.html` directly as a `file://` does not allow PWA install; use a local/HTTPS server.

## Notes

- This is a client-only demo. For production, move authentication and data to a backend API and store passwords hashed server-side. The "hidden admin" is a UI-level restriction here and should be enforced by the backend in production.
- Sample bookings/drinks are seeded on first load. Use "Clear All Data" in Manage to reset records.