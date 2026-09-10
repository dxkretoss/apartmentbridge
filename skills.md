# 🏠 Apartment Bridge — Affordable Housing Platform · Project Skills & Flow Documentation

> **Project Name:** Apartment Bridge  
> **Type:** UI/UX Design Prototype (Static HTML/CSS/JS — Single-Page Application)  
> **Files:** `index.html` (main prototype), `index2.html` (clone), `admin.html` (admin panel)  
> **Total Lines:** ~5,493 in `index.html`  
> **Screens:** 22 navigable screens in one file  

---

## 📌 Project Concept

**Apartment Bridge** is a comprehensive **affordable housing search platform** designed to aggregate listings from government programs (HUD, Section 8, LIHTC, HOME, USDA Rural, Section 202) into a single, user-friendly search experience — free for renters.

### Core Problem It Solves
Millions of income-restricted homes are scattered across PDFs, county portals, and paper waitlists. Apartment Bridge puts them behind **one clean search** with:
- **Eligibility matching** — Users enter household size + income → see a match score (%) on every listing
- **Plain-language program explanations** — No jargon; programs explained simply
- **Waitlist tracking** — Real-time open/closed statuses with alerts
- **Map-based search** — Draw radius around work/school/family to find nearby homes

### Target Users
| User Type | Description |
|-----------|-------------|
| **Renters/Seekers** | Low-to-moderate income individuals/families seeking affordable housing |
| **Voucher Holders** | Section 8 Housing Choice Voucher holders looking for voucher-friendly properties |
| **Seniors (62+)** | Elderly seeking Section 202 senior housing |
| **Case Workers** | Social workers helping clients find housing |
| **Property Managers** | Affordable housing operators managing listings, leads, and waitlists |

---

## 🏗️ Architecture & Technical Structure

### Single-File Architecture
The entire prototype lives in **one HTML file** with:
1. **CSS Design System** (Lines 13–2090) — All styles, tokens, and component CSS
2. **SVG Icon Sprite** (Lines 2096–2317) — 40+ inline SVG symbols
3. **HTML Screens** (Lines 2320–5256) — 22 `<section class="screen">` elements
4. **JavaScript** (Lines 5289–5490) — Routing, data, interactions, and the eligibility calculator

### Screen Navigation System (Router)
```
Prototype Bar → <select> dropdown + prev/next buttons
     ↓
go(key) function → toggles `.screen.on` class
     ↓
Only the active screen is visible (display: block)
All others are hidden (display: none)
```

The `go(key)` function:
- Toggles visibility via CSS class `.on`
- Updates the URL hash (`#/home`, `#/search`, etc.)
- Scrolls to top
- Resizes open accordion panes

---

## 🎨 Design System (Screen 00)

### Color Tokens
| Token | Hex | Purpose |
|-------|-----|---------|
| `--blue-700` | `#155C93` | Primary — buttons, links, navigation |
| `--green-600` | `#218557` | Eligibility, success, matches |
| `--ink` | `#14293D` | Headings, footer, dark text |
| `--bg` | `#F6FAF8` | Page background |
| `--amber-700` | `#93600F` | Waitlists, warnings |
| `--red-700` | `#A63A32` | Errors only |
| `--violet-700` | `#5B4FA8` | Senior programs |

**Design Philosophy:** *Blue = trust & navigation · Green = eligibility & good news*

### Typography
| Role | Font | Weight | Size |
|------|------|--------|------|
| Display/Headings | Bricolage Grotesque | 700–800 | Responsive (clamp) |
| Body text | Public Sans | 400–700 | 16px base, 1.55 line-height |

### Component Library
- **Buttons:** `.btn-primary`, `.btn-green`, `.btn-outline`, `.btn-ghost`, `.btn-lg`, `.btn-sm`, `.btn-icon`
- **Badges:** `.b-blue`, `.b-green`, `.b-amber`, `.b-violet`, `.b-red`, `.b-ink`, `.b-line`
- **Chips:** `.chip` (toggleable with `.on` state)
- **Cards:** `.card` with `.pad`, `.hov` (hover lift effect)
- **Property Cards:** `.prop` with `.media`, `.body`, `.price`, `.specs`, `.match` ring
- **Forms:** `.input`, `.select`, `.field`, `.check`, `.toggle`, `.stepper`, range inputs
- **Tables:** `.tbl` with styled headers and row hovers
- **Tabs:** `.tabs` > `.tab` (with `.on` active state)
- **Accordions:** `.acc` (collapsible with animation)
- **Alerts:** `.alert.info`, `.alert.ok`, `.alert.warn`, `.alert.bad`
- **Map Elements:** `.map`, `.pin`, `.cluster`, `.park`, `.mapctl`
- **Skeleton Loaders:** `.skl` (shimmer animation)
- **Empty States:** `.empty` with art and CTA
- **Notifications:** `.notif` with `.unread` and `.dot`
- **Stats:** `.stat` with `.n` (number), `.d` (description), `.tr` (trend)
- **Charts:** `.bars` (bar chart), `.donut` (conic-gradient pie)

---

## 📱 Complete Screen Flow (22 Screens)

### Flow Diagram
```
┌──────────────────────────────────────────────────────────────┐
│                    PUBLIC SCREENS                             │
├──────────────────────────────────────────────────────────────┤
│                                                              │
│  [00] Design System ──── Foundation & Component Reference    │
│                                                              │
│  [01] Home ─────┬───→ [02] Search Results ──→ [03] Property  │
│        │        │         (List/Map/Split)       Details      │
│        │        │                                    │        │
│        │        ├───→ [04] Browse Directory           │        │
│        │        │         (State/City/ZIP/Program)    │        │
│        │        │                                    │        │
│        │        └───→ [05] Compare Properties ◄──────┘        │
│        │                                                     │
│        ├───→ [06] Housing Programs (Section 8, LIHTC, etc.)  │
│        │                                                     │
│        ├───→ [07] Income Eligibility Calculator               │
│        │                                                     │
│        ├───→ [08] Resources (Guides, Videos, Downloads)      │
│        │                                                     │
│        ├───→ [09] About & Mission                            │
│        │                                                     │
│        ├───→ [10] Contact                                    │
│        │                                                     │
│        ├───→ [11] Help Center                                │
│        │                                                     │
│        └───→ [12] FAQ                                        │
│                                                              │
├──────────────────────────────────────────────────────────────┤
│                    AUTH SCREENS                               │
├──────────────────────────────────────────────────────────────┤
│                                                              │
│  [13] Login ──→ [14] Register (3-step)                       │
│        │                                                     │
│        └───→ [15] Forgot Password                            │
│                                                              │
├──────────────────────────────────────────────────────────────┤
│                 USER DASHBOARD (Authenticated)               │
├──────────────────────────────────────────────────────────────┤
│                                                              │
│  [16] Dashboard ──┬──→ [17] My Favorites                     │
│     (Overview)    │                                          │
│                   ├──→ [18] Saved Searches & Alerts           │
│                   │                                          │
│                   ├──→ [19] Notifications                     │
│                   │                                          │
│                   └──→ [20] Profile & Household               │
│                                                              │
├──────────────────────────────────────────────────────────────┤
│             PROPERTY MANAGER PORTAL (B2B)                    │
├──────────────────────────────────────────────────────────────┤
│                                                              │
│  [21] PM Dashboard ──┬──→ Listings (table, drafts, photos)   │
│                      ├──→ Lead Inbox (email-like thread)      │
│                      ├──→ Documents (shared PDFs)             │
│                      ├──→ Analytics (funnel, donut, bars)     │
│                      ├──→ Plans & Billing (3-tier pricing)    │
│                      └──→ Profile Settings                   │
│                                                              │
└──────────────────────────────────────────────────────────────┘
```

---

## 🔍 Screen-by-Screen Detailed Analysis

### Screen 00 — Design System & Components
- **ID:** `#s-system`
- **Purpose:** Internal reference for the design team
- **Contains:** Color swatches, typography samples, button variants, badge/chip gallery, form controls demo, property card examples, loading/empty/alert states

---

### Screen 01 — Home Page
- **ID:** `#s-home`
- **Sections:**
  1. **Hero with Search Box** — City/ZIP input, household size selector, income range, search button
  2. **Stats Bar** — 312,000+ units, 3,100 cities, Free for renters
  3. **Browse by Need** — Family, Senior 62+, Accessible units, Voucher-friendly (4 category cards)
  4. **Featured Properties** — 3 hand-picked property cards with match scores
  5. **Housing Programs** — 4 program cards (Section 8, LIHTC, Section 202, HOME)
  6. **How It Works** — 3-step process: Search → See eligibility → Apply
  7. **Map Preview** — Interactive-looking map with price pins and clusters
  8. **Recently Added** — 3 new listing cards
  9. **Success Stories** — 3 testimonial cards with star ratings
  10. **FAQ Preview + Newsletter** — 3 accordion items + email signup form

---

### Screen 02 — Search Results
- **ID:** `#s-search`
- **Key Features:**
  - **Sticky filter bar** (below header) with: location input, rent/beds/voucher/program chips, "All filters" expandable panel
  - **View toggle:** Split / List / Map (segmented control)
  - **Split layout:** Left = scrollable card grid (6 cards), Right = sticky map with pins
  - **Advanced filter panel** (hidden by default): rent range slider, household size, income input, program chips (Section 8, LIHTC, Public housing, HOME, USDA), demographic filters (Family, Senior, Accessible, Pets), amenity filters
  - **Sort dropdown:** Best match, Rent low→high, Rent high→low, Newest first, Waitlist status
  - **Match banner:** "7 strong matches for a 4-person household earning $42,000"
  - **Pagination:** Numbered page buttons

---

### Screen 03 — Property Details
- **ID:** `#s-property`
- **Layout:** Main content + sticky sidebar
- **Sections:**
  1. **Breadcrumb** — Home > Sacramento > Cedar Grove Commons
  2. **Photo Gallery** — 4-image grid with "+14 photos" overlay
  3. **Tags** — LIHTC badge, Section 8 welcome, Waitlist open, Accessible units
  4. **Title + Actions** — Name, address, heart/share/compare buttons
  5. **Stats Bar** — Rent range, Beds, Baths, Match score (91% with ring gauge)
  6. **About** — Long-form description of the community
  7. **Income Limits Table** — Household size vs max income vs rent, with "Your status" column highlighting the user's row
  8. **Voucher Info Alert** — Explains Housing Choice Vouchers
  9. **Amenities** — 9 chips (laundry, A/C, pets, wheelchair, elevator, parking, playground, garden, management)
  10. **What's Nearby** — Schools, Transit, Healthcare (3 info cards + map)
  11. **Documents** — Application PDF, income checklist, accommodation form (download buttons)
  12. **Sidebar** — Leasing office info, Apply/Join waitlist button, Message/Call buttons, waitlist closing warning, re-check eligibility link
  13. **Similar Homes** — 3 property cards

---

### Screen 04 — Browse Directory
- **ID:** `#s-directory`
- **Tabbed Navigation:** By State | By City | By County | By ZIP | By Program
- **State/City tabs:** Card grid with name + listing count
- **ZIP tab:** Input field + popular ZIP chips
- **Program tab:** Badge cards linking to program-filtered search

---

### Screen 05 — Compare Properties
- **ID:** `#s-compare`
- **Comparison Table:** 3 properties side-by-side
- **Rows:** Rent, Program, Eligibility (%), Income limit, Vouchers, Waitlist status, Wheelchair access, Pets, Distance, Transit score
- **Actions:** View home, Remove from comparison

---

### Screen 06 — Housing Programs
- **ID:** `#s-programs`
- **Hero:** "Government housing help, without the jargon"
- **Program Cards (5):**
  1. Section 8 / Housing Choice Voucher — "Most flexible"
  2. LIHTC · Tax-Credit Apartments — "Most homes"
  3. HOME Program
  4. Section 202 · Senior Housing — "62+"
  5. FHA Loans — "For buying" (ownership path)
- **Income Limits Explainer:** AMI bands (≤30%, ≤50%, ≤60%, ≤80%)
- **Program FAQs:** 4 accordion items

---

### Screen 07 — Income Eligibility Calculator
- **ID:** `#s-calculator`
- **Interactive Calculator (fully functional JS):**
  - **Inputs:** County selector (with AMI data), household size stepper, income slider ($0–$140K), voucher checkbox, senior checkbox
  - **Output:** AMI gauge (SVG ring), percentage, income band label, list of qualifying programs
  - **Logic:** `income / (baseAMI × householdFactor) × 100 = AMI%`
  - **Household factors:** 1-person = 0.70, 2 = 0.80, 3 = 0.90, 4 = 1.00, 5+ = increments of 0.08
- **Matched Listings:** 3 property cards filtered by calculator results

---

### Screen 08 — Resources
- **ID:** `#s-resources`
- **Content Types:** Guides, Articles, Videos, Downloads, FAQs (chip filters)
- **6 Resource Cards:** Section 8 walkthrough, income certification video, waitlist strategy article, document checklist PDF, disability rights guide, rental scam video

---

### Screen 09 — About
- **ID:** `#s-about`
- **Mission Statement:** "Affordable housing exists. Finding it shouldn't be the hard part."
- **Impact Stats:** 312K+ units, 58,000 households housed, 100% free
- **Vision:** Plain language, accessible by default, verified data, never sell data
- **Team:** 4 team member profiles
- **Partners:** HUD, National Housing Trust, Enterprise, 640+ housing authorities, United Way 211

---

### Screen 10 — Contact
- **ID:** `#s-contact`
- **Contact Cards:** Renter support (email), Phone & TTY line (8 languages), Property managers (portal link)
- **Contact Form:** Name, email, topic dropdown, message textarea, copy checkbox
- **Map:** HQ location pin

---

### Screen 11 — Help Center
- **ID:** `#s-help`
- **Hero Search:** Search help articles with suggestions
- **6 Topic Cards:** Searching & filters, Eligibility & income, Vouchers & programs, Account & profile, Safety & scams, For property managers
- **CTA:** "Still stuck?" → Contact support

---

### Screen 12 — FAQ
- **ID:** `#s-faq`
- **Filter Chips:** All, Getting started, Eligibility, Vouchers, Waitlists, Account
- **6 Accordion Items:** Qualification, documents needed, voucher refusal legality, waitlist timelines, credit impact, searching for others
- **Bottom CTA:** Help Center + Contact us

---

### Screens 13–15 — Authentication
| Screen | ID | Features |
|--------|----|----------|
| **Login** | `#s-login` | Email/password, remember me, forgot password, Google login, SMS code login, split layout with testimonial art |
| **Register** | `#s-register` | 3-step wizard (step 1 shown), name/email/password/role, progress bar, newsletter opt-in |
| **Forgot Password** | `#s-forgot` | Email input → sends reset link (30min validity), fallback phone verification |

---

### Screens 16–20 — User Dashboard (Authenticated)
All use the **app shell layout:** sidebar navigation + main content area.

**Sidebar links:** Overview, Saved homes (6), Saved searches (3), Notifications (2), Profile, Account settings.

| Screen | ID | Key Features |
|--------|----|--------------|
| **Dashboard** | `#s-dashboard` | Welcome message, waitlist warning alert, 4 stat cards (saved homes, alerts, applications, AMI level), recommended listings, activity feed, profile completeness gauge (75%) |
| **Favorites** | `#s-favorites` | 6 saved property cards, compare button, sort option, note-taking textarea per listing |
| **Saved Searches** | `#s-saved-searches` | 3 saved search cards with criteria chips, alert toggles (email/text/digest), pause/resume/delete controls |
| **Notifications** | `#s-notifications` | Tab filters (All/Matches/Messages/Applications), 5 notification items (match alerts, waitlist deadlines, messages, document requests, housing updates), delivery preference toggles |
| **Profile** | `#s-profile` | Personal info form, household details (size/children/income/source), voucher information with toggle, accessibility needs checkboxes, account danger zone (delete account) |

---

### Screen 21 — Property Manager Portal
- **ID:** `#s-pm`
- **Separate tab-based navigation** within the screen (not shared sidebar)
- **6 Sub-panes:**

| Pane | Features |
|------|----------|
| **Dashboard** | 4 stats (views, inquiries, applications, reply time), weekly views bar chart, today's queue alerts |
| **Listings** | Table with property rows (name, program, status, views, leads, edit), draft listings with "Finish setup", photo upload drop zone |
| **Leads** | Email-like inbox with sidebar list + thread view, pre-screening info, canned reply templates ("Insert: doc checklist", "Insert: tour times") |
| **Documents** | List of shared PDFs (application, income checklist, accommodation form) with replace buttons, multi-language support |
| **Analytics** | Donut chart (lead sources), funnel chart (views → checks → inquiries → applications), conversion tips |
| **Billing** | 3-tier pricing (Basic $0, Premium $89/listing, Portfolio custom), invoice history table with PDF download |

---

## ⚙️ JavaScript Logic Breakdown

### 1. Property Data Store (`PROPS` array)
```javascript
// 8 sample properties with:
{ id, name, loc, rent, beds, bath, sq, g (gradient class), 
  prog (program badges), vou (voucher accepted), 
  match (eligibility %), mid (borderline flag), newd (new listing flag) }
```

### 2. Card Renderer (`cardHTML` function)
- Builds property card HTML from data object
- Generates SVG match ring with dynamic `stroke-dasharray`
- Conditionally renders "Featured", "New", voucher badges

### 3. Data Population (`fill` function)
Populates 8 different card grids across screens:
```
ds-cards      → Design system examples
home-featured → Home page featured section
home-recent   → Home page recently added
search-cards  → Search results
prop-similar  → Property detail "similar homes"
dash-recs     → Dashboard recommendations
fav-cards     → Favorites page
calc-recs     → Calculator matched listings
```

### 4. Shared Chrome Injection
- **Headers** (`[data-header]`) — Dynamically renders with authenticated/unauthenticated variants
- **Footers** (`[data-footer]`) — Same footer injected across all public pages
- **Sidebars** (`[data-appside]`) — Dashboard sidebar with active state

### 5. Screen Router (`go` function)
```
URL hash (#/home) → go("home") → toggle .screen.on → scroll top → resize accordions
```
- Supports browser hash navigation
- Previous/Next buttons cycle through screens
- Dropdown selector for quick jump

### 6. Interactive Components (Event Delegation)
All interactions use a single `document.addEventListener("click")`:
- **Accordions** — Toggle `.open` class, animate `max-height`
- **Favorites** — Toggle heart `.on` with bounce animation
- **Chips** — Toggle `.on` selection state
- **View Segments** — Switch between Split/List/Map layouts
- **Directory Tabs** — Show/hide `[data-dpane]` panes
- **PM Tabs** — Show/hide `.pm-pane` elements
- **Filter Panel** — Toggle `#filterPanel` visibility
- **Password Eye** — Toggle input type password/text
- **Steppers** — Increment/decrement counter

### 7. Eligibility Calculator (Fully Functional)
```
Input:  county AMI, household size, income
        ↓
Factor: HH_FACTOR = {1: 0.70, 2: 0.80, ..., 8: 1.32}
        ↓
Calc:   adjustedLimit = baseAMI × HH_FACTOR[size]
        AMI% = (income / adjustedLimit) × 100
        ↓
Output: SVG arc gauge, band label, program eligibility list
```

---

## 📐 Responsive Design

### Breakpoints
| Breakpoint | Behavior |
|------------|----------|
| `≤ 980px` | 4-col → 2-col grids, 3-col → 2-col grids |
| `≤ 960px` | Navigation hidden, burger shown, ghost buttons hidden |
| `≤ 900px` | Split layouts → single column, app sidebar → horizontal scroll, search map → stacked above results |
| `≤ 860px` | Footer grid → 2 columns |
| `≤ 760px` | Gallery → 2-col layout |
| `≤ 700px` | Search box → vertical stack |
| `≤ 640px` | All grids → single column |
| `≤ 560px` | Footer → single column |

### Accessibility Features
- Skip-to-content link
- `prefers-reduced-motion` media query (disables animations)
- Screen-reader-only class (`.sr`)
- ARIA attributes: `aria-label`, `aria-expanded`, `aria-pressed`, `aria-selected`, `aria-current`, `aria-live`
- Focus-visible styling with blue ring
- Keyboard-navigable focus management
- Semantic HTML: `<main>`, `<nav>`, `<header>`, `<footer>`, `<article>`, `<figure>`, `<caption>`

---

## 💰 Business Model (Reflected in UI)

| Revenue Source | Details |
|----------------|---------|
| **Free for renters** | Search, save, alerts, calculator — always free |
| **PM Basic Plan** | $0/mo — unlimited listings, lead inbox, waitlist sync |
| **PM Premium Plan** | $89/listing/mo — featured placement, analytics, auto-replies, priority support |
| **PM Portfolio Plan** | Custom pricing — 50+ listings, API sync, compliance reporting, account manager |

---

## 🗃️ File Structure Summary

```
d:\Apartment_bridge\
├── index.html       (242 KB) — Main prototype with 22 screens
├── index2.html      (242 KB) — Clone of index.html
├── admin.html       (215 KB) — Admin panel
└── .git/            — Git repository
```

---

## 🔗 Key Navigation Functions

| Action | Code |
|--------|------|
| Navigate to screen | `go('screenId')` |
| Toggle accordion | Click `.acc > button` |
| Toggle favorite | Click `.fav` / `.fav-any` |
| Toggle chip | Click `button.chip` |
| Switch search view | Click `.seg button[data-view]` |
| Toggle filter panel | Click `#moreFilters` |
| Run calculator | Modify any calculator input → `calc()` auto-runs |

---

## 📊 Data Sources Referenced (Prototype Data)

| Data Type | Source |
|-----------|--------|
| Property listings | 8 hardcoded sample properties in `PROPS[]` |
| AMI figures | 5 counties with base AMI values (Sacramento $129K, Houston $99.9K, Columbus $110.3K, Phoenix $103.7K, Denver $142.8K) |
| Income limits | Computed from AMI × household factor × program tier (30/50/60/80%) |
| Directory | 8 states, 8 cities (hardcoded arrays) |
| Programs | 6 government programs with plain-language descriptions |

---

## ✅ Summary Checklist

- [x] Fully self-contained single-file prototype (HTML + CSS + JS)
- [x] 22 navigable screens with hash-based routing
- [x] Complete design system with tokens and reusable components
- [x] Functional eligibility calculator with real AMI math
- [x] Responsive design with 7+ breakpoints
- [x] WCAG 2.2 AA accessibility considerations
- [x] Two-sided marketplace: Renters (search) + Property Managers (portal)
- [x] Interactive elements: accordions, toggles, chips, tabs, favorites, map pins
- [x] Property card system with dynamic match score rings
- [x] Auth flow: login, register (3-step), forgot password
- [x] Dashboard with stats, recommendations, activity feed
- [x] PM portal with listings, leads, analytics, billing
- [x] Newsletter signup, contact form, help center
- [x] Success stories and social proof
- [x] Print-friendly document downloads (PDFs)
- [x] Multi-language support indicators (8 languages)

---

## 🏛️ Enterprise Admin Console (`admin.html`) · 19 Screens / Modules

`admin.html` (5,002 lines, 215 KB) is a standalone Enterprise Super Admin console featuring **IBM Plex Sans/Mono** typography, dark/light theme switcher, and 19 operational panes:

| Module | Pane ID | Purpose & Key Features |
|--------|---------|------------------------|
| **1. Dashboard** | `#p-dashboard` | Real-time platform KPIs (128k listings, 2.4k users/wk, revenue), ingestion sparklines, and quick actions. |
| **2. Properties** | `#p-properties` | Full inventory table (128,412 properties) with bulk actions, program tags, and verification status. |
| **3. Edit Property** | `#p-property-edit` | Deep property editor (unit mix, income tiers, HUD ID matching, amenities, and photo manager). |
| **4. Import Center** | `#p-import` | Automated ETL sync pipelines (LIHTC DB, HUD Multifamily, USDA Rural), status logs, error queues, and manual sync triggers. |
| **5. Users** | `#p-users` | Renter and PM directory, 2FA status, account flags, and impersonation tools. |
| **6. Claim Requests** | `#p-claims` | Queue of PMs requesting ownership of HUD-ingested listings with proof verification. |
| **7. Property Managers** | `#p-pms` | Management company directory, assigned properties, subscription tiers, and contact details. |
| **8. Programs** | `#p-programs` | Configuration for LIHTC, Section 8, Section 202, HOME, and state-level subsidy parameters. |
| **9. Search Management** | `#p-searchmgmt` | Search ranking rules, synonym tables, boost weights, and sponsored placement rules. |
| **10. CMS** | `#p-cms` | Editorial content manager for educational guides, FAQ entries, and homepage announcements. |
| **11. Resources** | `#p-resources` | Document checklist and downloadable PDF application vault editor. |
| **12. Reports** | `#p-reports` | Detailed reporting on user engagement, lead generation, housing authority conversion, and CSV exports. |
| **13. Monetization** | `#p-monetize` | Revenue roadmap and tier controls ($0 Basic, $49 Enhanced, $89 Premium, Enterprise Portfolio). |
| **14. Notifications** | `#p-notifs` | Broadcast system announcements, scheduled maintenance banners, and push alert triggers. |
| **15. Email Templates** | `#p-emails` | Transactional email template editor (welcome, match alerts, reset links, invoice receipts). |
| **16. Audit Logs** | `#p-audit` | Complete security audit trail (logins, role changes, listing approvals, data exports). |
| **17. Roles & Permissions** | `#p-roles` | Granular RBAC (Super Admin, Data Manager, Moderator, Support Staff, Content Admin). |
| **18. Settings** | `#p-settings` | Platform configurations, API keys, webhook endpoints, and data retention policies. |
| **19. Design System** | `#p-design` | Ops UI design system (Plex Mono numbers, data-dense tables, status pills, chart themes). |

---

---

# 📋 PART 2: CLIENT REQUIREMENTS & PRODUCTION EXECUTION PLAN

> **Status:** Pre-development planning  
> **Client Vision:** "Not another listing website — a significantly better user experience than what currently exists in the affordable housing space"  
> **Current Assets:**  
> - `index.html`: 24 Consumer, Renter, PM, & Legal Screens  
> - `admin.html`: 19 Enterprise Super Admin Screens  
> - **Total Existing Screens:** 43 Prototype Screens Complete  
> - **Production Readiness:** 2 UI screens missing (Reset Password, Dedicated Settings) + backend/database/ETL services to build

## 🎯 Client's Project Goals

1. Build a **centralized platform** for affordable housing listings
2. Enhance **accessibility and connection** between renters and property operators
3. Aggregate **HUD/LIHTC government data** into consumer-friendly format
4. Implement **location-based search** with advanced filters
5. Create a **clean, modern, mobile-first** UI (comparable to apartments.com, rentcafe.com, forrent.com)
6. Build **monetization** through property listing visibility controls
7. Ensure **scalable infrastructure** for future growth

---

## 📝 Client's Scope of Work

| Requirement | Details |
|-------------|---------|
| **Consumer Platform** | Aggregate affordable housing listings from HUD/LIHTC/Section 8 into one search |
| **Location Search** | City, ZIP, county, state with map integration |
| **Advanced Filters** | Household size, income range, voucher acceptance, program type, amenities |
| **Mobile-First Design** | Responsive, mobile-friendly, comparable to top rental platforms |
| **PM Listing System** | Property managers can create/manage listings for marketing |
| **Visibility Control** | Admin controls listing visibility for monetization (sales structure) |
| **Data Ingestion** | HUD/LIHTC dataset normalization, mapping, search optimization |
| **Admin Panel** | Moderation, user management, data sync controls |

---

## 🏛️ HUD/LIHTC Data Sources

### Government Data Links (Client Provided)

| Source | URL | Description |
|--------|-----|-------------|
| **LIHTC Database** | https://www.huduser.gov/lihtc | 54,000+ properties / 3.7M units — built for analysts, NOT consumers |
| **HUD Resource Locator** | https://resources.hud.gov | Find affordable rentals + services — consumer-facing but unpolished |
| **HUD Multifamily Search** | https://www.hud.gov/hud-partners/multifamily-property-search | Search subsidized properties (Section 8, FHA, etc.) |

### Data Field Availability Matrix

| Field | HUD/LIHTC Available | Notes |
|-------|---------------------|-------|
| Property name | ✅ Yes | From LIHTC + HUD datasets |
| Address / Geocoordinates | ✅ Yes | Requires geocoding for coords |
| Unit count | ✅ Yes | LIHTC dataset |
| Bedroom mix | ✅ Yes | LIHTC dataset |
| Program type | ✅ Yes | LIHTC/Section 8/Section 202/HOME |
| Income tier / AMI % | ✅ Yes | LIHTC compliance data |
| Year built | ✅ Yes | LIHTC placed-in-service date |
| Owner / Management | ✅ Yes | LIHTC/HUD records |
| Rent amounts | ⚠️ Partial | Some HUD records, not universal |
| Waitlist status | ❌ No | Must be PM-entered |
| Voucher acceptance | ⚠️ Partial | HUD has flag, needs PM confirmation |
| Photos | ❌ No | PM-uploaded only |
| Amenities | ❌ No | PM-entered only |
| Occupancy rate | ❌ No | PM-entered only |

### Data Sync Strategy

| Data Source | Sync Type | Frequency |
|-------------|-----------|-----------|
| LIHTC dataset | Bulk CSV import | Annual + quarterly refresh |
| HUD multifamily | API/scrape | Monthly |
| AMI/Income limits | HUD published tables | Annual (FY update) |
| PM-entered data | Real-time CRUD | As PMs update |

---

## 🔐 IP & Ownership Requirements (Client Confirmed)

> Client requires **written confirmation** of all ownership transfers upon final payment:

| Item | Ownership |
|------|-----------|
| Full source code | → Client (no retained rights) |
| Design assets (Figma, UI kit, branding) | → Client |
| Database + schema + export rights | → Client |
| Codebase transferability | → Fully portable to another dev team |
| No licensing restrictions | → Confirmed, clean transfer |

---

## 🏗️ Infrastructure Ownership (Client-Controlled)

> All infrastructure must be **established under client-owned accounts**:

| Service | Must Be Client-Owned |
|---------|---------------------|
| Domain registrar | ✅ |
| AWS / Vercel hosting | ✅ |
| GitHub repositories | ✅ |
| API credentials (Maps, SMS, Email) | ✅ |
| Analytics accounts (GA4) | ✅ |
| Email systems (SendGrid) | ✅ |
| Payment processor (Stripe) | ✅ |
| All third-party integrations | ✅ |

---

## 📄 Complete Page Inventory (32 Pages)

### Public Pages — 14 Pages

| # | Page | Route | Function |
|---|------|-------|----------|
| 1 | Home / Landing | `/` | Hero search, featured listings, programs, how-it-works, testimonials |
| 2 | Search Results | `/search` | Filterable grid + map (List/Map/Split) |
| 3 | Property Details | `/property/:id` | Full listing: photos, rent, eligibility, amenities, apply |
| 4 | Browse Directory | `/directory` | Browse by State/City/County/ZIP/Program |
| 5 | Housing Programs | `/programs` | Plain-language program explainers |
| 6 | Eligibility Calculator | `/calculator` | Interactive AMI calculator |
| 7 | Compare Properties | `/compare` | Side-by-side comparison (up to 3) |
| 8 | Resources / Guides | `/resources` | Guides, videos, document checklists |
| 9 | About Us | `/about` | Mission, team, impact stats |
| 10 | Contact | `/contact` | Form, support channels, map |
| 11 | Help Center | `/help` | Searchable FAQ categories |
| 12 | FAQ | `/faq` | Accordion-based Q&A |
| 13 | Privacy Policy | `/privacy` | Legal |
| 14 | Terms of Service | `/terms` | Legal |

### Auth Pages — 4 Pages

| # | Page | Route | Function |
|---|------|-------|----------|
| 15 | Login | `/login` | Email/password + Google + SMS |
| 16 | Register | `/register` | Multi-step wizard (3 steps) |
| 17 | Forgot Password | `/forgot-password` | Email reset link |
| 18 | Reset Password | `/reset-password/:token` | New password from link |

### Renter Dashboard — 6 Pages

| # | Page | Route | Function |
|---|------|-------|----------|
| 19 | Dashboard Overview | `/dashboard` | Stats, recommendations, activity |
| 20 | Saved Homes | `/dashboard/favorites` | Favorites with notes, compare |
| 21 | Saved Searches | `/dashboard/searches` | Alert configs with email/SMS toggles |
| 22 | Notifications | `/dashboard/notifications` | Matches, messages, waitlist updates |
| 23 | My Profile | `/dashboard/profile` | Household, income, voucher, accessibility |
| 24 | Account Settings | `/dashboard/settings` | Password, preferences, data export, delete |

### Property Manager Portal — 5 Pages

| # | Page | Route | Function |
|---|------|-------|----------|
| 25 | PM Dashboard | `/pm/dashboard` | KPI stats, charts, action queue |
| 26 | Listings Management | `/pm/listings` | CRUD, photos, income tiers, waitlist |
| 27 | Lead Inbox | `/pm/leads` | Inquiry threads, templates, archive |
| 28 | Analytics | `/pm/analytics` | Sources, funnel, CSV export |
| 29 | Plans & Billing | `/pm/billing` | Subscriptions, invoices |

### Admin Panel — 3 Pages

| # | Page | Route | Function |
|---|------|-------|----------|
| 30 | Admin Dashboard | `/admin` | Platform stats, sync status |
| 31 | Listing Moderation | `/admin/listings` | Approve/reject, visibility controls |
| 32 | User Management | `/admin/users` | Manage renters, PMs, subscriptions |

---

## 👤 User Flows

### Renter Flow
```
Home → Search (location + filters)
  → View Results (list/map/split)
    → Property Details (eligibility match, apply, save)
      → Register → Dashboard (saved homes, alerts, notifications)
```

### Property Manager Flow
```
PM Register → PM Dashboard
  → Add/Edit Listings (photos, tiers, waitlist, docs)
    → Manage Leads (inbox, reply, archive)
      → View Analytics (sources, funnel)
        → Manage Billing (subscribe, invoices)
```

### Admin Flow
```
Admin Login → Admin Dashboard
  → Moderate Listings (approve/reject/flag, visibility control)
    → Manage Users (renters, PMs, subscriptions)
      → HUD Data Sync (status, trigger, logs)
```

---

## 💻 Production Tech Stack

| Layer | Technology |
|-------|-----------|
| Frontend | Next.js 14+ (React, App Router, SSR) |
| Styling | Tailwind CSS + Headless UI |
| Maps | Mapbox GL JS or Google Maps |
| Database | PostgreSQL + PostGIS (Supabase or AWS RDS) |
| ORM | Prisma |
| Auth | NextAuth.js or Clerk |
| File Storage | AWS S3 / Cloudflare R2 |
| Email | SendGrid or Resend |
| SMS | Twilio |
| Payments | Stripe |
| Hosting | Vercel (frontend) + AWS (backend/DB) |
| CI/CD | GitHub Actions |
| Monitoring | Sentry + Vercel Analytics |

---

## 📅 Development Timeline (22 Weeks / 6 Phases)

| Phase | Weeks | Deliverables |
|-------|-------|-------------|
| **1. Foundation** | W1–W4 | Infrastructure, design system, DB schema, auth, home page, basic search |
| **2. Core Search** | W5–W8 | Map integration, property details, calculator, directory, compare, filters |
| **3. User Accounts** | W9–W12 | Registration, login, dashboard, favorites, saved searches, notifications, profile |
| **4. PM Portal** | W13–W16 | PM dashboard, listing CRUD, photos, lead inbox, analytics, Stripe billing |
| **5. Admin & Monetization** | W17–W19 | Admin panel, moderation, visibility controls, listing tier monetization |
| **6. Polish & Launch** | W20–W22 | Mobile optimization, accessibility audit, SEO, testing, deployment, handoff |

---

## 💰 Monetization Tiers

| Tier | Price | Features |
|------|-------|----------|
| **Basic (Free)** | $0/mo | Standard listing, basic page, lead inbox |
| **Enhanced** | $49/listing/mo | Boosted search ranking, badge, map priority |
| **Premium** | $89/listing/mo | Featured on homepage, full analytics, auto-replies |
| **Portfolio** | Custom | 50+ listings, API sync, compliance, account manager |

### Future Revenue Streams
- Featured listing placements (pay-per-impression)
- Sponsored search results
- Premium lead generation
- Data analytics for housing authorities
- Partnership referral integrations

---

## 🎨 UX Differentiation Strategy

| Principle | How We Execute |
|-----------|---------------|
| Plain language | "You pay ~30% of income" not "Section 8 PBRA per 24 CFR 983" |
| Emotional clarity | Match scores (91%) instead of raw income tables |
| Mobile-first | Thumb-friendly, bottom sheets, sticky CTAs |
| Trust signals | "Verified against HUD" badges, sync dates, "Free to apply" |
| Visual warmth | Gradients, soft colors, illustrations — not clinical government UI |
| Inclusive | WCAG 2.2 AA, 8 languages, screen reader tested |
| Anxiety reduction | Progress bars, "No credit check", document checklists |
| Retention | Saved search alerts (email + SMS), waitlist reminders |

---

## 🔄 Future Scalability Roadmap

| Timeline | Features |
|----------|----------|
| **Q1 Post-Launch** | PM claimed listings, enhanced analytics, A/B testing |
| **Q2 Post-Launch** | Inquiry pipelines, partnership integrations, expanded data |
| **Q3 Post-Launch** | Mobile app (React Native), push notifications |
| **Q4 Post-Launch** | Advertising platform, sponsored listings |
| **Year 2** | Public API, partner widgets, housing authority integrations |

---

## ⚠️ Key Risks & Mitigations

| Risk | Mitigation |
|------|------------|
| HUD data gaps (no waitlist/photos) | PM-entered data + "Contact property" fallback |
| PM adoption (chicken & egg) | Seed with HUD data first, outreach in pilot cities |
| Photo unavailability | Gradient placeholders (as in prototype) |
| Legal (data scraping) | Use only public HUD datasets, no private scraping |
| Mobile performance | Mobile-first build, image optimization, lazy loading |

---

*Updated on: September 10, 2026*  
*Repository: [dxkretoss/apartmentbridge](https://github.com/dxkretoss/apartmentbridge)*
