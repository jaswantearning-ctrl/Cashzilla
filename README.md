# CashZilla - Referral Dashboard (v1)
This is a frontend project for CashZilla with built-in support for Firebase (Auth + Firestore).
If you want production-ready backend security, create a Firebase project, enable Authentication (Email/Password)
and Firestore, then paste your firebaseConfig into `firebase-config.js`.

Files:
- index.html           -> Main app (login/signup, nav, Home, Refer, Watch, Withdraw, Deposit)
- admin.html           -> Simple admin panel (view pending withdrawals)
- firebase-config.js   -> Placeholder where you must paste your firebaseConfig
- app.js               -> Main JavaScript logic (Auth, tasks, watch timer, withdraw flow)
- style.css            -> Basic styling
- manifest.json        -> PWA metadata (optional)
- assets/*             -> icons

### Important notes / steps to deploy:
1. Create Firebase project (https://console.firebase.google.com/)
2. Enable Authentication -> Email/Password
3. Enable Firestore Database (in native mode)
4. Copy firebase config and put into firebase-config.js (see template)
5. Deploy static site to Firebase Hosting / Netlify / Vercel / Surge.

### Demo fallback:
If you don't add firebase-config, the app runs in **localStorage demo mode**. It's only for testing. Not secure.

Watch & Earn behavior:
- Click "Watch & Earn" -> opens a random video (your two YouTube links) in a new tab via an intent-like link.
- Start timestamp saved (Firebase or localStorage).
- After returning, click "Claim Watch" -> server-side (Firestore) or local check computes watch duration.
- Minimum 150 sec (2.5 min) required. Reward ₹1 per 10 sec.

Withdraw behavior:
- Withdraw requires bank details and amount.
- Submission creates a `pending` withdrawal request (Firestore) or stored locally.
- Requests are NOT auto-approved: admin must approve from admin.html.

Deposit:
- Visible only if user.level === 4.

This package is a starting point. For full security, connect with a real backend or configure Firebase rules carefully.
