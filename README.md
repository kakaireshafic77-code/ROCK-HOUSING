# ROCK HOUSINGS
### Integrated Rental & Property Management System

---

## 📖 Overview

**ROCK HOUSINGS** is a modern, offline-first, multi-landlord rental and property management platform that gives landlords full control over their properties, tenants, rent collection, and maintenance — while giving every tenant their own private, permanent, self-service portal.

Built as a single-page progressive web app, it works **completely offline**, stores data locally in the browser, and requires **zero backend, zero server setup, and zero hosting costs** to run.

---

## 🎯 The Pitch

### For Landlords

> **"Stop chasing rent. Start running a business."**

Managing rental properties with notebooks, spreadsheets, or WhatsApp reminders is chaos. Tenants forget. Caretakers lose receipts. Arrears pile up invisibly. Month-end becomes a guessing game.

ROCK HOUSINGS replaces all of that with a clean, single dashboard that shows you — in real time — who has paid, who owes, what's broken, and where your money is going. No paperwork. No chasing. No math.

### For Tenants

> **"Your rent. Your portal. Your records — permanently."**

Every tenant gets a private, permanent link to their own portal. They can see exactly how much they owe, pay in one tap, track which months are settled, and report issues — without ever needing to call the landlord. Their portal stays alive as long as they rent the unit.

### The Big Idea

Most rental software is **either** made for professional property management companies (expensive, complex) **or** is a glorified spreadsheet. ROCK HOUSINGS sits in the sweet spot:

- **Simple enough** for a landlord with 3 rooms
- **Powerful enough** for a landlord with 300 units across multiple properties
- **Free to run** because it's a self-contained web app
- **Private by design** — each landlord's data is completely isolated

---

## ✨ Key Features

### 🏢 Landlord Workspace
- **Dashboard** — live KPIs: properties, units, occupancy, collections, arrears, open maintenance, monthly expenses
- **Properties** — register buildings, land, shops, hostels, offices with owner and location details
- **Units** — rentable spaces inside each property, with rent and occupancy tracking
- **Tenants** — full lifecycle: name, phone, unit, lease dates, monthly rent, balance
- **Payments** — record rent against a **specific month** so accounts reconcile cleanly
- **Arrears** — auto-calculated outstanding balances per tenant, sorted by amount owed
- **Maintenance** — unified requests from both the office and the tenant portal, with 3-state workflow (Pending → In Progress → Done)
- **Expenses** — categorised operational costs (utilities, repairs, salaries, security, etc.)
- **Staff** — caretakers, managers, agents, security — with property assignment and salary
- **Reports** — monthly income, expenses, net position, occupancy rate, and per-property performance
- **CSV Export** — download every table for accounting or backup

### 📱 Tenant Portal (permanent private link)
- **Balance due** — always up to date
- **Months Paid grid** — visual, coloured view of every month
- **Pay rent** — via MTN MoMo / Airtel Money buttons + PRN code
- **Payment history** — receipts, dates, methods, month allocations
- **Report issues** — lands directly in the landlord's Maintenance tab
- **Confirm resolution** — tenants click "Mark Resolved ✓" once they're satisfied
- **Lease details** — always visible on the sidebar

### 🛡️ Super Admin Console
- Platform-wide overview of all landlord accounts
- Total landlords, users, properties, units, tenants, collections
- Drill into any landlord's account
- Export all data across all landlords

### ⚙️ Technical Features
- **Offline-first** — works without internet, syncs via browser localStorage
- **Installable (PWA)** — add to home screen on Android / iOS
- **Cross-tab live sync** — admin and tenant portal update instantly when open side by side
- **Multi-landlord isolation** — each account sees only its own data
- **Zero backend** — no server, no database, no monthly cost
- **Mobile-first responsive** — works cleanly on phones, tablets, and desktops
- **Cross-domain ready** — deploys to Vercel, Netlify, GitHub Pages, or any static host

---

## 🎨 Design Language

- **Theme:** Clean, light, professional SaaS
- **Fonts:** Poppins (display), Inter (body)
- **Icons:** Custom inline SVG set (no icon libraries)
- **Colors:** Monochrome primary with a rich semantic accent palette
  - **Green** — paid, positive, done
  - **Amber** — partial, in-progress, warning
  - **Black** — primary action, current month
  - **Red** — arrears, danger, delete
  - **Blue / Purple / Teal / Pink** — informative accents
- **Motion:** Subtle hover lifts, fade-ins, active-state scaling
- **Layout:** Card-first, pill navigation, generous whitespace

---

## 🧠 The Cascade Engine (behind the scenes)

Rent accounting in ROCK HOUSINGS is smarter than a spreadsheet.

When a tenant pays, the system **automatically settles the earliest unpaid month first**, then rolls any surplus into the following months — as many as needed.

### Example

Rent = 650,000. Tenant pays **1,500,000** in January.

| Month | Allocated | Status | Rollover |
|---|---|---|---|
| Jan | 650,000 | ✅ Paid | +850,000 |
| Feb | 650,000 | ✅ Paid | +200,000 |
| Mar | 200,000 | 🟡 Partial (450k left) | — |
| Apr | — | ⚪ Unpaid | — |

Result: **three months handled from one payment**, with no manual bookkeeping.

### Month Colour Codes (Tenant Portal)

| Colour | Meaning |
|---|---|
| 🟢 Green | Fully paid |
| 🟡 Amber | Partially paid (shows amount remaining) |
| ⚫ Black (ring) | Current month |
| ⚪ Dashed grey | Future / unpaid |

---

## 🔗 How Admin & Tenant Connect

The two pages — `index.html` (admin) and `tenant.html` (tenant) — share a single browser storage key (`rock_housings_db_v1`).

### Flow

1. **Landlord adds a tenant** → tenant record created with a unique ID
2. **Landlord clicks "Copy Link"** on the tenant card → gets a permanent URL like  
   `https://yoursite.com/tenant.html?tenant=id_abc123`
3. **Landlord shares that link** with the tenant (SMS, WhatsApp, email)
4. **Tenant opens the link** → sees only their own unit, balance, and history
5. **Tenant pays or reports an issue** → instantly appears in the admin's account
6. **Landlord updates maintenance status** → instantly visible in the tenant's portal
7. **Tenant confirms resolution** → admin sees a "Tenant Confirmed" badge

The link is **permanent** — it stays live as long as the tenant exists in the system. Delete the tenant → the link stops working.

---

## 🚀 Quick Start

### 1. Files needed

Place these **two files in the same folder**:
- `index.html` — landlord admin app
- `tenant.html` — tenant portal

### 2. Run locally

Just double-click `index.html` — no server required. Everything runs in the browser.

### 3. Deploy to Vercel (recommended)

1. Create a folder with both files
2. Push to GitHub **or** drag-and-drop the folder into [vercel.com/new](https://vercel.com/new)
3. Framework preset → **Other**
4. Deploy
5. Your app is live at `https://your-app.vercel.app`
6. Tenant links become `https://your-app.vercel.app/tenant.html?tenant=...`

The same works for **Netlify**, **Cloudflare Pages**, **GitHub Pages**, or any static host.

---

## 🔐 Access & Credentials

### Landlord (Register / Login)

**Register** creates a private landlord account:
- Landlord / Business Name
- Owner Full Name
- Contact Phone
- Email (optional)
- Username + Password

Then log in with **Landlord Name + Username + Password**.

### Super Admin (hidden)

| Field | Value |
|---|---|
| Username | `superadmin` |
| Password | `ROCK#Root2025` |
| Landlord Name | *(any value)* |

⚠️ **Change this password** in `index.html` (search for `SUPER_ADMIN`) before sharing.

The Super Admin is **not advertised anywhere in the UI** — access is by entering the credentials on the normal login screen.

---

## 🗂️ Data Model

All data is stored in a single `localStorage` key: `rock_housings_db_v1`.

```
landlords       { id, name, ownerName, contact, email, status, createdAt }
users           { id, landlordId, username, password, name, role, phone, avatar }
properties      { id, landlordId, name, location, type, owner }
units           { id, landlordId, propertyId, name, type, rent, status }
tenants         { id, landlordId, name, contact, unitId, rent, leaseStart, leaseEnd, status }
payments        { id, landlordId, tenantId, amount, date, month, year, monthName, method, receipt, source }
tenantPayments  { id, landlordId, tenantId, amount, date, month, year, monthName, method, receipt, source: 'tenant-portal' }
maintenance     { id, landlordId, unitId, issue, reportedBy, priority, cost, status, date }
tenantTickets   { id, landlordId, tenantId, unitId, issue, status, tenantConfirmed, date }
expenses        { id, landlordId, category, description, propertyId, amount, date }
staff           { id, landlordId, name, role, phone, propertyId, salary }
activityLogs    { id, landlordId, userId, action, details, timestamp }
```

This structure **maps 1:1 to SQL tables** — perfect for migrating to a real backend later.

---

## 🔄 Upgrading to a Real Backend

Since the entire data model is already flat and landlord-scoped, migrating is a drop-in:

1. Replace `insert()`, `updateRecord()`, `delRecord()`, `findById()`, `byLandlord()` with API calls
2. Keep the exact same JSON shapes → backend tables map directly
3. Recommended stack options:
   - **Node + Express + SQLite** (single file DB, same offline ethos)
   - **Supabase** (Postgres + auth + realtime out of the box)
   - **Firebase** (fastest to ship)
   - **PocketBase** (single binary, self-hosted)
4. Keep the tenant URL pattern (`?tenant=<id>`) — works with any auth token

---

## 📱 Mobile Experience

- Full responsive layout
- Bottom-safe areas handled (`viewport-fit=cover`)
- Installable as a home-screen app (PWA)
- Tab bar collapses to icons on small screens
- Stat cards reflow to 2-up on phones
- Modals take full width with margins
- Long tables scroll horizontally inside their card
- Touch-friendly action buttons (44px+ targets)

---

## 🎯 Use Cases

| Scenario | How ROCK HOUSINGS Fits |
|---|---|
| A landlord with 3 rental rooms | Full-featured, zero cost, no learning curve |
| A landlord with 30 units across 2 buildings | Dashboard, reports, arrears tracking |
| A property management company with 300 units | Multi-landlord isolation, Super Admin console, staff management |
| A hostel warden managing student rooms | Per-tenant portals for easy payment |
| A shop owner renting out stalls | Unit types support Shops and Offices |
| A church managing land leases | "Land" property type supported |

---

## 🏁 Roadmap (future ideas)

- **SMS reminders** for overdue tenants (Africa's Talking / Twilio)
- **WhatsApp receipts** via Business API
- **PDF rent statements** per tenant per year
- **Online payments** via Flutterwave / Paystack / MTN MoMo API
- **Photo uploads** on maintenance tickets
- **Meter reading** module (water / electricity)
- **Lease agreements** generated as PDFs
- **Multi-currency** support
- **Audit trail** per record
- **Push notifications** for tenants (PWA)

---

## 📝 License & Credit

ROCK HOUSINGS is a self-contained, offline-first web application designed for landlords who want clarity without complexity.

Everything runs locally. Nothing is sent to a server unless you explicitly move it there.

**Made with care for landlords who'd rather be building than bookkeeping.**

---

## 🆘 Troubleshooting

| Issue | Fix |
|---|---|
| Tenant link doesn't open | Make sure both `index.html` and `tenant.html` are in the same folder on your host |
| Data disappeared | Clearing browser storage wipes everything — export CSV regularly |
| Tenant portal says "Not linked" | The tenant record was deleted, or the URL's `?tenant=` ID is wrong |
| Two landlords on same phone don't see each other | Each landlord logs in with their own name — data is isolated by `landlordId` |
| Payment month looks wrong | The cascade engine always settles earliest unpaid month first — this is by design |
| Can't install as PWA | Some browsers require HTTPS + user interaction with the app first |

---

**ROCK HOUSINGS** — *Rent, tenants, maintenance. One dashboard. Every month. Offline.*
