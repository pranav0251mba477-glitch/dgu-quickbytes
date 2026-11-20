# DGU QuickBytes & Prints (Assignment 2 prototype)

One-file React + Tailwind app (`index.html`), no build step. Roles: Customer, Courier, Admin.

## 1. Try it now (demo mode)
Open `index.html` (or run `npx serve .`). With `FIREBASE_CONFIG = null` it runs on browser storage and seeds 12 menu items, 3 hostels and 10 demo orders. Log in as any `@dgu.ac.in` email. Admin = emails in `ADMIN_EMAILS` (top of the script).
Tip: tick **Test mode** in Admin to place orders outside 9 PM-3 AM.

## 2. Real login + database (Google AI Studio / Firebase)
1. Build/preview in Google AI Studio (paste this code or the prompt), or use https://console.firebase.google.com directly.
2. Firebase: create project, add a Web app, copy the config into `FIREBASE_CONFIG`.
3. Authentication: enable **Google**. Firestore: create database; for the pilot use rules that need login:
   `allow read, write: if request.auth != null;`
4. Open Admin → Metrics → **Load demo data** (optional).
5. Add your Vercel domain under Authentication → Settings → Authorized domains.

## 3. GitHub → Vercel → static URL
1. Create a GitHub repo, upload `index.html` + `README.md`.
2. vercel.com → log in with GitHub → Add New Project → pick the repo → Deploy (framework: Other, no build command).
3. Submit the Vercel URL + your GitHub profile link (before 11:59 PM).

## Demo script (one order, ~3 min)
1. Log in as **Customer** `aarav.test@dgu.ac.in`. If it's daytime, first tick Test mode as Admin (another tab/login).
2. Menu → add 2 Lay's Chips + 1 Cold Drink. Open **Print Order**, upload a small PDF, set B/W, 2 copies, Add print.
3. Cart → name, Rajpur Road Hostel A, room 204, note "Call at gate". Scan the UPI QR, enter reference `UPI123456`, Place order.
4. Orders tab shows status **Placed**.
5. Log out, log in as **Courier**, go Online, Accept → Start preparing → Picked up → Delivered.
6. Back as Customer: watch status update, rate 5 stars + comment, try **Reorder**.
7. Log in as **Admin**: see the order, delivery minutes, metrics, unit economics, Export CSV and match the UPI ref.

## What to test in the 30-day pilot (all from Admin → Metrics)
| Check | Target | Where |
|---|---|---|
| Paying customers | ≥ 25 | Paying customers |
| Completed orders | ≥ 100 | Total orders / Pilot goals |
| Repeat usage | ≥ 20% | Repeat customers |
| Delivery speed | avg 15-20 min, ≥ 90% within 20 | Avg delivery time, Within 20 min |
| Price acceptance (~₹80/order) | AOV near ₹80 | Avg order value |
| Late-night demand | orders spread across 9 PM-3 AM | Orders by hour |
| Satisfaction | avg ≥ 4.0 ★ | Avg rating + comments |
| Unit economics | contribution > 0, orders heading to break-even (200) | Unit-economics panel |
| Payment honesty | every order has a matching UPI receipt | Export CSV vs bank statement |

Weekly: week 1 get 10 sign-ups, week 2 first 30 orders, week 3 check repeat %, week 4 fix the top 3 complaints from ratings.

## Not in V1
Native app, GPS tracking, dynamic pricing, large inventory, 24/7 delivery, wallet, expansion beyond DGU.

## Known prototype limits
UPI payment is manual (reference only). PDFs are stored in the order record, so max 600 KB. Page count is auto-detected from the PDF but you can edit it.
