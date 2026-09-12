# MB-Pay V5.1 — Final earning + payout model

## Model
- AdMob revenue is the owner's/app publisher's revenue.
- Rewarded Ad gives only non-cash, non-transferable Bonus Points.
- Bonus Points are never added to the UPI payout balance.
- Real-money payout balance is credited by Admin only after a separately verified eligible activity/reward.
- User requests withdrawal with UPI ID.
- Admin controls payout ON/OFF, maintenance, minimum withdrawal and payout fund.
- Admin approves/rejects requests and marks them Paid after manually sending UPI payment.

## AdMob IDs
Production IDs already included:
- App ID: `ca-app-pub-9118816469156613~9747468788`
- Banner: `ca-app-pub-9118816469156613/631155603`
- Interstitial: `ca-app-pub-9118816469156613/7950688887`
- Rewarded: `ca-app-pub-9118816469156613/7405105429`

**Important:** Debug builds use Google's official test ad IDs. Google says to use test ads during development; replace/disable test mode only for release builds. Do not click live ads during testing.

## Backend URL — जरूरी
Open `app/build.gradle` and replace:
`https://YOUR-BACKEND-DOMAIN.example/api`
with your real **HTTPS** backend URL ending in `/api`.

Example:
`https://your-domain.example/api`

The Android app injects this URL automatically into the WebView.

## Backend setup
```bash
npm install
JWT_SECRET="a-long-random-secret" ADMIN_EMAIL="your-admin-email@example.com" npm start
```
For production use HTTPS and a real database (Postgres/SQLite/Supabase etc.) instead of the demo JSON file.

## Admin earning credit
Admin panel includes a user selector and **Credit Real ₹ Balance**. Use it only after the corresponding eligible activity has been independently verified. This credit is separate from AdMob rewarded ads.

## Build Android APK
Open the `MB-Pay-V5` folder in Android Studio/AndroidIDE and build the debug APK first. Release APK should be built only after the backend URL, privacy/terms, production database, HTTPS and AdMob production configuration are ready.

## Not production-ready until
- HTTPS backend
- production database
- strong JWT secret stored as environment secret
- rate limiting / abuse protection
- audit logs and idempotency
- secure admin authentication
- privacy policy and terms
- final Google Play/AdMob review
