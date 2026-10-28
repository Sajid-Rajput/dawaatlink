---
doc_id: pk-digital-invitations-kb
title: "Digital Wedding Invitations Startup (Pakistan-first): Research, Competitors, Decisions and Launch Plan"
version: 1.1.0
as_of: 2026-10-28
timezone: "Asia/Karachi (PKT, UTC+5)"
primary_currency: PKR
language: en
status: pre-launch
brand_name: DawaatLink
team:
  - role: founder
    skills: [lead software engineer]
  - role: partner
    skills: [software engineer, content creation]
    status: inactive            # as of 2026-10-28 the founder builds alone with Claude Code (Q-26)
intended_readers: [ai_agents, founders]
labels: [FACT, DECISION, ACCEPTED_REC, REC, ASSUMPTION, OPEN, RISK]
---

# Digital Wedding Invitations Startup (Pakistan-first)

Knowledge base compiled from web research and founder Q&A. It is the single source of truth for building, marketing and operating the product. Every section starts with a one-line summary so it can be retrieved on its own.

## 0. Instructions for AI agents

> Summary: How to read labels, resolve conflicts, cite IDs and handle stale data in this file.

### 0.1 Label legend

| Label | Meaning | How to treat it |
|---|---|---|
| `FACT` | Observed in an external source on or before `as_of` | Cite its `SRC-*` ID. Prices, features and follower counts go stale; re-verify anything older than 90 days before using it in pricing decisions or public copy. |
| `DECISION` | Confirmed by the founders | Keep it. If you believe it is wrong, raise the concern with reasoning instead of silently changing it. |
| `ACCEPTED_REC` | Founders delegated the choice ("go with your recommendation"), so the recommendation became the plan | Treat as the current plan. It has not been validated with customers yet. |
| `REC` | Recommendation not yet explicitly accepted | Use as the default only when no `DECISION` or `ACCEPTED_REC` covers the topic. |
| `ASSUMPTION` | Reasoned belief without direct evidence | Validate before relying on it (see section 16). |
| `OPEN` | Unresolved value | Ask the founders. Do not invent a value. |
| `RISK` | Known threat to the plan | Account for it in plans and code. |

### 0.2 Conflict resolution order

`DECISION` > `ACCEPTED_REC` > `REC` > `ASSUMPTION`. Facts are evidence, not plan items: if a newer fact contradicts a plan item, flag the conflict and propose a change rather than overriding the plan.

### 0.3 Working rules

1. Never invent competitor prices, features, user counts or follower counts. Write `unknown` and add an item to section 16, because pricing and positioning depend on accurate comparisons.
2. Keep money in its source currency. Use integers for PKR. Do not convert currencies silently.
3. Use ISO 8601 dates. Islamic calendar dates (Ramadan, Muharram, Eid) are estimates until the official moon sighting.
4. Reference stable IDs (`GAP-02`, `Q-12`, `TIER-02`) instead of re-copying text, so updates stay consistent.
5. Company-reported numbers (users, families served) are marked `self_reported: true`. Treat them as claims.
6. When you update this file, bump `version`, update `as_of`, and add a line to section 18.

### 0.4 ID scheme

| Prefix | Entity | Section |
|---|---|---|
| `MKT-*` | Pakistan market facts | 4 |
| `GLB-*` | Global benchmark facts | 4 |
| `BM-*` | Business model options | 5 |
| `COMP-*` | Competitors | 6 |
| `INS-*` | Research insights | 7 |
| `GAP-*` | Market gaps to target | 8 |
| `NG-*` | Non-goals for v1 | 8 |
| `Q-*` | Founder decision log | 9 |
| `TIER-*` | Pricing tiers | 10 |
| `ENT-*` | Data entities | 10 |
| `PAY-*`, `WA-*`, `LEG-*` | Payment, WhatsApp and legal facts | 11 |
| `SOP-*` | Operating procedures | 11 |
| `CNT-*`, `PART-*` | Content formats and partnerships | 12 |
| `MS-*` | Milestones | 13 |
| `KPI-*` | Success metrics | 14 |
| `RISK-*` | Risks | 15 |
| `VAL-*` | Validation backlog | 16 |
| `SRC-*` | Sources | 17 |

### 0.5 Research method and limitations

- Research date: 2026-09-17, using web search and direct page fetches.
- TikTok blocked automated access and Instagram requires a login, so social media data comes from publicly indexed profile and search snippets. Follower counts may be out of date.
- Most Instagram and TikTok sellers do not publish prices ("DM to order"), so their prices are `unknown`.
- Only the metadata of Qubool.pk (COMP-03) could be retrieved, not its full pricing page.
- National wedding market size figures conflict between sources (see MKT-05). Do not use them in pitches without a better source.

### 0.6 Table of contents

- [0. Instructions for AI agents](#0-instructions-for-ai-agents)
- [1. Project snapshot](#1-project-snapshot)
- [2. Founder input and original concept](#2-founder-input-and-original-concept)
- [3. Glossary](#3-glossary)
- [4. Market context](#4-market-context)
- [5. Business model](#5-business-model)
- [6. Competitors](#6-competitors)
- [7. Key insights](#7-key-insights)
- [8. Positioning, gaps and non-goals](#8-positioning-gaps-and-non-goals)
- [9. Decision log (Q-01 to Q-30)](#9-decision-log-q-01-to-q-30)
- [10. MVP product specification](#10-mvp-product-specification)
- [11. Payments, WhatsApp and legal](#11-payments-whatsapp-and-legal)
- [12. Marketing and partnerships](#12-marketing-and-partnerships)
- [13. Launch timeline](#13-launch-timeline)
- [14. KPIs](#14-kpis)
- [15. Risks](#15-risks)
- [16. Open questions and validation backlog](#16-open-questions-and-validation-backlog)
- [17. Source registry](#17-source-registry)
- [18. Changelog](#18-changelog)

## 1. Project snapshot

> Summary: A done-for-you web invitation service for Pakistani wedding functions, launching before the 2026-27 wedding season.

```yaml
project:
  product: Web-based invitation pages for Pakistani wedding functions
  production_model: done_for_you        # customer sends details, team builds the page (Q-07, DECISION)
  business_type: per_event_consumer_product   # not classic subscription SaaS (section 5)
  positioning: "Done-for-you family dawatnama"  # section 8
  launch_market: Pakistan
  expansion_path:
    - Pakistani and South Asian Muslim diaspora (UK, UAE, US, Canada)
    - Broader international markets
  functions_at_launch: [nikkah, mehndi, baraat, walima, engagement]
  optional_functions: [dholki, mayun]
  marketing_channels: [instagram, tiktok]
  customer_channel: whatsapp
  payment_v1: "Raast ID on a personal bank account; customer sends screenshot on WhatsApp; staff verifies"
  brand: DawaatLink                     # Q-27, DECISION 2026-10-28
  team: solo founder building with Claude Code   # Q-26, DECISION 2026-10-28
  stack: [Next.js, Vercel, Supabase]    # Q-31
  status: pre_launch
  key_dates:
    launch: rolling from 2026-10-28     # original dates (MVP 2026-10-01, public launch 2026-10-10) were missed; see section 13
    peak_season: [2026-11-01, 2026-12-31]
    ramadan_estimated_start: 2027-02-08
    kpi_review: 2027-02-28
```

## 2. Founder input and original concept

> Summary: What the founders decided before and during the research (label: DECISION).

- **Offering:** Web-based invitations only at the start, with multiple packages, a template catalog, and a custom template option.
- **Marketing:** Instagram and TikTok first. Organic content first, paid ads later.
- **Market:** Pakistan first, then global expansion.
- **Payment flow (v1):** The website shows the account details. The customer pays, then sends a payment screenshot on WhatsApp. All further communication happens on WhatsApp.
- **Production:** The client shares details and the team builds the invitation. All design work is done in-house.
- **Team:** The founder is a lead software engineer. The partner is a software engineer who also creates content. **Update 2026-10-28:** the partner is inactive; the founder works alone with Claude Code (Q-26).
- **Legal:** Register the business, but later.
- **Delegated decisions:** For most open questions the founders chose "go with your recommendation". Those items are labeled `ACCEPTED_REC` in section 9.

## 3. Glossary

> Summary: Urdu and Pakistani wedding terms used across this file. Label: ASSUMPTION (general cultural knowledge; customs vary by family and region, so confirm details with customers).

| Term | Meaning | Product relevance |
|---|---|---|
| Nikkah (Nikah) | Islamic marriage contract ceremony | Core function |
| Mehndi (Rasm-e-Hina) | Henna celebration before the wedding; the bride's and groom's families may host separate Mehndis | Core function |
| Baraat (Barat) | The groom's family arrives at the event hosted by the bride's family; often includes Rukhsati (the bride's departure) | Core function |
| Walima (Valima) | Reception hosted by the groom's family after the marriage | Core function |
| Engagement (Mangni) | Formal engagement ceremony | Core function |
| Dholki | Pre-wedding musical gathering, often at home | Optional function; may have a restricted audience |
| Mayun (Mayoun) | Pre-wedding ritual held before Mehndi | Optional function |
| Dawatnama | Urdu word for an invitation letter or card | Also the name of competitor COMP-02; do not use it as the brand name |
| Shagun / Salami | Cash gifts given at wedding functions | Possible later feature (competitor COMP-01 offers digital shagun) |
| Side (larki walay / larke walay) | The bride's family / the groom's family; each side hosts different functions and sends its own invitations | Pricing unit (Q-13) |
| Dadke / Nanke | Paternal / maternal relatives | Guest grouping |
| Household invite | An invitation addressed to a family unit, e.g. "Ahmed Sahab & family" | Guest list modeled by household (ENT-06) |
| Raast / Raast ID | State Bank of Pakistan instant payment system; a Raast ID is a mobile-number alias for a bank account | Payment v1 |
| Raast P2M QR | Merchant QR code payments on Raast | Payment upgrade path |
| NTN | National Tax Number issued by FBR | Needed for business bank account and gateways |
| IRIS | FBR's online tax portal | NTN registration |
| SECP | Securities and Exchange Commission of Pakistan (company registration) | Not needed for a sole proprietorship |
| wa.me link | WhatsApp click-to-chat URL with prefilled text | Free way to send personal invites |
| BSP | WhatsApp Business Solution Provider (API reseller) | Only needed for API automation |
| Diaspora | Overseas Pakistanis (UK, UAE, US, Canada, etc.) | Expansion market and cross-border payers |

## 4. Market context

> Summary: Pakistan's wedding spending is large, guest lists are big, connectivity is limited, and the season peaks in November-December. Label: FACT.

### 4.1 Pakistan market facts

| ID | Fact | Value | Data date | Sources | Confidence |
|---|---|---|---|---|---|
| MKT-01 | Karachi wedding economy | About PKR 33 billion of direct economic activity in the 2025 winter season (industry association estimate) | 2026-01 | SRC-10, SRC-11 | medium |
| MKT-02 | Average guests per wedding | 249 attendees (Shadiyana data) | 2026-01 | SRC-10 | medium |
| MKT-03 | Demand trend | Wedding enquiries rose about 25% between October and December 2025 (Shadiyana) | 2026-01 | SRC-10 | medium |
| MKT-04 | Average wedding ticket size | About PKR 600,000 on Shadiyana, before the 2026 inflation wave | 2026-05 | SRC-12 | medium |
| MKT-05 | National wedding economy size | Conflicting: about PKR 900 billion per industry estimates cited by The Friday Times, while Dawn printed PKR 900 million | 2026 | SRC-12, SRC-13 | low |
| MKT-06 | Cost pressure | Halls raising rates or avoiding long-term price commitments; stricter enforcement of wedding regulations under austerity measures | 2026-05 | SRC-12 | medium |
| MKT-07 | Internet users | 117 million; 45.6% penetration at end of 2025 | 2025-10 | SRC-14 | high |
| MKT-08 | Social media user identities | 79.9 million (31.2% of population) | 2025-10 | SRC-14 | high |
| MKT-09 | Mobile connection penetration | 82.6% (Pakistan Economic Survey) | 2026-06 | SRC-15 | medium |
| MKT-10 | Printed wedding card price | PKR 30 to PKR 3,500+ per card, depending on material and style | 2026-06 | SRC-16 | medium |
| MKT-11 | Functions per wedding | Engagement, Mayun, Mehndi, Dholki, Barat and receptions are common | 2026-07 | SRC-13 | medium |
| MKT-12 | Who sends which card | The bride's family traditionally sets the Nikkah cards; different families send cards for different functions | 2026-05 | SRC-17 | low |
| MKT-13 | Season volume by month | October medium-high (season starts); November very high; December very high; January high; February medium. Diaspora families fly back mostly in November-December. | 2026-07 | SRC-18 | medium |
| MKT-14 | Avoided months | Many families avoid weddings during Muharram, Safar and Ramadan | 2026-06 | SRC-19 | medium |
| MKT-15 | Ramadan 2027 (estimate) | Expected 2027-02-08 to about 2027-03-09; Eid al-Fitr about 2027-03-10, subject to moon sighting | 2026-04 | SRC-20 | medium |
| MKT-16 | Invitation etiquette | Send WhatsApp invites individually, not in group chats; many families pair digital invites with printed or hand-delivered cards for elders | 2026-07 | SRC-21 | low |

### 4.2 Global benchmark facts

| ID | Market | Fact | Data date | Sources | Confidence |
|---|---|---|---|---|---|
| GLB-01 | US | Joy, Zola, The Knot and Minted offer core wedding websites free with no time limit; custom domains cost about USD 17.99/year (Zola) and about USD 20/year (Joy) | 2026-07 | SRC-22 | medium |
| GLB-02 | US | The free website is an acquisition tool: Zola and Joy earn registry commissions, Minted sells stationery, The Knot charges vendors for access to couples | 2026-05 | SRC-23 | medium |
| GLB-03 | US | 90% of roughly 10,000 surveyed couples made a wedding website (The Knot 2026 Real Weddings Study) | 2026-03 | SRC-24 | medium |
| GLB-04 | US | Paid builders exist but are hard to justify against free ones: Wedsites USD 99 one-time; Riley & Grey USD 39/month or USD 299/year; Bliss & Bone USD 15-21/month | 2026-05 | SRC-25 | medium |
| GLB-05 | Indonesia | Digital invitation prices range from about Rp 50,000 (basic) to Rp 3,000,000+ (fully custom) | 2026-06 | SRC-26 | medium |
| GLB-06 | Indonesia | Inveet reports 444,960 users and 12,593,714 guests reached (self_reported: true) | 2026 | SRC-27 | medium |
| GLB-07 | Indonesia | LoveLink runs a done-for-you model from Rp 99,000: customer picks a package, sends details on WhatsApp, receives the design within 24 hours, and pays after approving it; reports 1,200+ invitations (self_reported: true) | 2026 | SRC-28 | medium |
| GLB-08 | Indonesia | LinkUndangan is a free web invitation maker usable by resellers, covering weddings, walimah, engagements, khitanan, aqiqah and birthdays | 2026 | SRC-29 | medium |
| GLB-09 | India | eInvit offers free-to-start RSVP pages, personalized WhatsApp invites through free wa.me links (no paid API), a UPI gift-money QR, and Nikah templates | 2026-07 | SRC-30 | medium |
| GLB-10 | India | Weddingkart sends personalized WhatsApp messages to every guest through the WhatsApp Business API, with per-guest delivery tracking and RSVP buttons | 2026-04 | SRC-31 | medium |
| GLB-11 | UK diaspora | TikTok sellers advertise custom digital Nikkah invites from GBP 15 | 2026-08 | SRC-32 | low |

## 5. Business model

> Summary: This is a per-event consumer product with SaaS-like parts, not classic subscription SaaS. Recurring revenue comes later from B2B customers. Label: REC, except where noted.

Reasoning: a family buys invitations once per wedding, so subscriptions do not fit the core customer. Competitors price per event and one-time (COMP-01, COMP-02).

| ID | Model | Description | Revenue type | Scalability | Role in this plan |
|---|---|---|---|---|---|
| BM-1 | Design service | Each invitation made by hand; orders via Instagram and WhatsApp | Per order | Low (limited by labor hours) | How most Pakistani social media sellers operate (COMP-04) |
| BM-2 | Template platform | Customer picks a template, adds details, pays once, receives a link | Per event | Medium to high | Where Pakistani platforms sit (COMP-01 to COMP-03) |
| BM-3 | B2B SaaS | Planners, printers and banquet halls subscribe and create invitations for many clients, possibly white-labeled | Recurring | High | Phase 2 recurring revenue (PART-01, PART-03) |
| BM-4 | Wedding ecosystem | The invitation is the entry point; revenue from payments, gifts or vendor referrals | Commissions | High | Long-term option (see Shadiyana, COMP-08) |

```yaml
chosen_model:
  customer_experience: BM-1     # done-for-you (Q-07, DECISION)
  production_engine: BM-2       # config-driven templates so each order takes minutes (Q-07, REC)
  phase_2: BM-3                 # white-label and partner accounts (REC)
  long_term: BM-4               # optional (REC)
```

## 6. Competitors

> Summary: Three young Pakistani self-serve platforms (price cluster PKR 2,999-5,999), many small Instagram/TikTok designers, printers adding e-cards, DIY template shops, and international Muslim-wedding platforms. Label: FACT for observed fields; fields prefixed `analysis_` or `rec_` are ASSUMPTION or REC.

### 6.1 Overview

| ID | Name | Category | Entry price | Delivery model | Threat level (analysis) |
|---|---|---|---|---|---|
| COMP-01 | Smart Invites (formerly ShaadiLink) | Self-serve platform | PKR 3,499 | DIY | High |
| COMP-02 | DawatNama | Self-serve platform | PKR 0 (paid tiers on free promo) | DIY | Medium |
| COMP-03 | Qubool.pk | Self-serve platform | PKR 0 starter; paid from PKR 2,999 | DIY | Medium |
| COMP-04 | Instagram/TikTok designers | Manual design service | unknown (DM to order) | Manual, done for customer | Medium |
| COMP-05 | Card printers with e-card add-ons | Print plus digital files | PKR 30 to 3,500+ per printed card | Manual | Low as competitor; high as partner |
| COMP-06 | Template marketplaces and apps | DIY templates | Varies; Zazzle printed invites about USD 1.90-2.27 each on sale; Etsy template prices not captured | DIY | Low in Pakistan |
| COMP-07 | International Muslim/South Asian platforms | Self-serve platforms | Free to start or pay once | DIY | Low now; high in diaspora phase |
| COMP-08 | Pakistani wedding marketplaces | Adjacent marketplace | n/a | Vendor marketplace | Partner candidate |

### 6.2 Competitor profiles

```yaml
- id: COMP-01
  name: Smart Invites
  former_name: ShaadiLink          # shaadilink.com.pk redirects to smartinvites.com.pk
  url: https://www.smartinvites.com.pk
  location: Jhelum, Pakistan
  category: self_serve_platform
  delivery_model: diy
  event_types: [weddings, birthdays, school_events, meetings]
  pricing_pkr:
    classic: {price: 3499, struck_through_price: 5500, unit: per_invitation}
    royal: {price: 5799, struck_through_price: 7299, unit: per_invitation}
    addon_personalized_guest_links: {price: 1000, unit: per_50_guests}
  payment_terms: "one-time payment, no subscription, unlimited guests"
  refund_policy: "all purchases final, no refunds on digital goods"
  classic_features:
    - 20 classic templates
    - RSVP collection
    - wishes and guestbook
    - background music
    - live countdown
    - Google Maps integration
    - unlimited edits
    - 3 months cloud hosting
  royal_adds:
    - 10 extra cinematic templates (30 total)
    - personal voice greeting and audio memo
    - custom MP3 upload
    - 3D door and gate reveals
    - scratch-card date reveal
    - personalized guest links with WhatsApp dispatch
    - digital shagun via EasyPaisa and JazzCash
    - VIP passes with QR gate scanner
    - AI invitation copywriter (Urdu and English)
    - dress code swatches and timeline
    - travel and accommodation info
  programs:
    affiliate: "10% discount for couples, 10% commission for creators"
    agency_page: "Agency & Planners"
  languages: [English, Urdu]
  tech_stack_from_public_repo: [Next.js 16, TypeScript, Tailwind CSS, shadcn/ui, Supabase, Safepay, Upstash Redis, Resend, Vitest]
  signals:
    - "Full codebase is public on GitHub, suggesting a small team"
    - "Hero copy promises pay once and keep forever, while the Classic plan lists 3 months of hosting"
  analysis_weaknesses:
    - Customer must build the invitation themselves
    - No refunds
    - Personalization is a paid add-on on the entry plan
    - Heavy cinematic features may load slowly on weak connections (not measured)
  rec_counter_strategy:
    - Done-for-you delivery (GAP-01)
    - Postponement-friendly refund policy (Q-18)
    - Household links included in the Family tier (TIER-02)
    - Lightweight pages (GAP-03)
  sources: [SRC-01, SRC-02]
  confidence: high

- id: COMP-02
  name: DawatNama
  url: https://www.dawatnama.app
  operator: Tayyab Technologies
  category: self_serve_platform
  delivery_model: diy
  pricing_pkr:
    free:
      price: 0
      limits: {events: 1, guests: 50, templates: 3, active_days: 30}
    premium:
      price: 2999
      unit: one_time
      promo: "free for a limited time"
      active_period: 6_months
      features: [unlimited events, unlimited guests, 20+ templates, RSVP with meal preferences, our story and gallery sections, CSV or Excel guest import, branding removed]
    royal:
      price: 5999
      unit: one_time
      promo: "free for a limited time"
      active_period: 1_year
      features: [exclusive royal templates, video header, seating arrangement, priority WhatsApp support, 15-minute onboarding call, analytics export]
  design_themes: [Mughal art, Islamic patterns, truck art fusion, modern minimal]
  languages: [English, Urdu]
  other_features: [one-tap WhatsApp sharing, per-event RSVP tracking, guestbook and wishes, view and share analytics]
  social:
    instagram: https://instagram.com/dawatnama.app
  signals:
    - "Site metadata shows it was generated with the v0.app AI builder"
    - "Paid plans given away free, indicating an early-stage product"
  analysis_weaknesses:
    - Very early stage
    - DIY only
    - A free promotion may train customers to expect free invitations
  rec_counter_strategy:
    - Do not match free; sell done-for-you service and speed
    - Avoid "Dawatnama" as a brand word
  sources: [SRC-03]
  confidence: high

- id: COMP-03
  name: Qubool.pk
  url: https://qubool.pk
  location: Lahore, Pakistan
  category: self_serve_platform
  delivery_model: diy
  pricing_pkr:
    free_starter_theme: 0
    premium_from: 2999
  claims:
    families_served: "1,700+"
    cities: [Lahore, Karachi, Islamabad]
    self_reported: true
  functions: [nikkah, baraat, walima, mehndi]
  channels:
    - WhatsApp sending
    - "Heavy SEO targeting in English and Urdu (keywords include wedding website and RSVP management)"
  social:
    x_twitter: "@quboolpk"
  signals:
    - "Name overlaps with Qubool, an existing matrimonial app"
  unknowns: [full tier list, feature list, hosting duration, refund policy]
  rec_counter_strategy:
    - Distinctive brand name (Q-27)
    - Live demo invitations as proof of quality
    - Start Urdu content and SEO early
  sources: [SRC-04, SRC-05]
  confidence: medium        # only site metadata was retrievable

- id: COMP-04
  name: Instagram and TikTok invitation designers (category)
  category: manual_design_service
  delivery_model: manual_done_for_you
  typical_order_flow: "DM on Instagram or TikTok, move to WhatsApp, advance payment, design delivered"
  pricing: unknown          # not published; buyers are told to DM
  examples:
    - handle: "@ecards.pk"
      url: https://www.instagram.com/ecards.pk/
      followers: 4230
      posts: 135
      notes: "Digital and printed cards; worldwide orders; fixed prices but DM to order; advance payment only"
    - handle: "@sketchbookstudio.pk"
      url: https://www.instagram.com/sketchbookstudio.pk/
      followers: 4883
      posts: 193
      notes: "Wedding invites, digital illustrations, Nikkah certificates; claims 500+ customers (self_reported)"
    - handle: "@weddingcardskarachi (Royal Wedding Cards Pakistan)"
      url: https://www.instagram.com/weddingcardskarachi/
      followers: 5807
      posts: 336
      notes: "Printed card focus"
    - handle: "TikTok sellers under Pakistani wedding hashtags"
      url: https://www.tiktok.com/discover/pakistani-wedding-invitation?lang=en
      notes: "Posts ask buyers to DM and share WhatsApp numbers; some sell Canva-editable website invites with envelope animation, countdown, Google Maps and RSVP form; content targets siblings (for example a brother's wedding) and specific wedding months"
  data_caveat: "Follower counts come from indexed snippets and may be outdated"
  analysis_weaknesses:
    - Prices hidden behind DMs
    - Capacity limited by designer hours
    - Output is mostly static images or videos without RSVP or live updates
  rec_counter_strategy:
    - Public price list (Q-21)
    - 24-hour delivery (Q-08)
    - Live link with RSVP plus a downloadable image (TIER-01, TIER-02)
  sources: [SRC-06, SRC-07, SRC-08, SRC-09]
  confidence: medium

- id: COMP-05
  name: Card printers offering e-cards (category)
  category: print_plus_digital_addon
  printed_card_price_pkr: {min: 30, max: "3500+", unit: per_card}
  examples:
    - name: weds.pk
      url: https://weds.pk/
      notes: "Outlets in Lahore and Islamabad; laser-engraved, acrylic, box and digital invitations; worldwide delivery"
    - name: invitationcards.pk
      url: https://invitationcards.pk/product-category/digital-cards/
      notes: "E-cards delivered as GIF, video, PNG or JPEG files; customized through back-and-forth coordination"
    - name: Zem Printers (weddingsadda.com)
      url: https://weddingsadda.com/
      notes: "50% advance and the rest before delivery; ships to UK, USA, Australia and Denmark"
    - name: Wedding Card Experts
      url: https://weddingcardexperts.com/
      notes: "Prints in Lahore; delivers to UK, USA and Canada"
    - name: CardFusion (UK)
      url: https://www.cardfusion.co.uk/pakistani-wedding-cards/
      notes: "Every printed order includes a free matching PDF e-vite; minimum order 70 cards"
  analysis: "Printers own the prestige printed card and the family relationship; their digital output is static files, not live pages"
  rec_counter_strategy:
    - Partner instead of competing (PART-01)
  sources: [SRC-16, SRC-17, SRC-33, SRC-34, SRC-35, SRC-36]
  confidence: medium

- id: COMP-06
  name: Template marketplaces and card-maker apps (category)
  category: diy_templates
  examples:
    - "Etsy: Canva-editable Pakistani and Muslim invitation templates, including animated video templates"
    - "Zazzle: printed Pakistani and Muslim wedding invitations at about USD 1.90-2.27 each on sale"
    - "Canva templates and Google Play card-maker apps"
  analysis_weaknesses:
    - Customer does all the work
    - Static files with no RSVP or household management
    - Not built around Pakistani payment methods
  relevance: "Mostly diaspora buyers; low direct threat in Pakistan"
  sources: [SRC-37, SRC-38]
  confidence: medium

- id: COMP-07
  name: International Muslim and South Asian wedding platforms (category)
  category: self_serve_platform_international
  examples:
    - name: Invyt
      url: https://www.invyt.app/nikah-planner
      notes: "Separate RSVP pages for Nikah, Walima, Mehndi and Baraat; halal dietary requirements collected; WhatsApp sharing; QR codes for printed invitations and mosque notice boards; free to start"
    - name: Nikahly (UK)
      url: https://www.nikahly.co.uk/
      notes: "Separate RSVPs for Nikah, Walima and Mehndi; guest sides and plus-one limits; dual-language cards; guest photos stream to the couple's Google Drive; registry and vendor marketplace"
    - name: WooowInvites
      url: https://www.wooowinvites.com/
      notes: "Pay once, no subscription; per-guest personalization; multilingual; RSVP, seating and budget tools; white-label options for planners; 29 Trustpilot reviews, one describing the platform as initially overwhelming to navigate"
    - name: eInvit (India)
      url: https://einvit.in/
      notes: "See GLB-09"
    - name: Weddingkart (India)
      url: https://www.weddingkart.co/tools/guest-communication-whatsapp
      notes: "See GLB-10"
  analysis: "Strong multi-event RSVP features; aimed at diaspora and international couples rather than families in Pakistan (PKR payment and Urdu support not verified)"
  rec_counter_strategy:
    - Win Pakistani families first
    - Enter the diaspora with the Pakistani-family product in phase 2
  sources: [SRC-30, SRC-31, SRC-39, SRC-40, SRC-41, SRC-42]
  confidence: medium

- id: COMP-08
  name: Pakistani wedding marketplaces (adjacent)
  category: vendor_marketplace
  examples:
    - name: Shadiyana
      notes: "Wedding-tech marketplace; about 80% of revenue from commissions (photographers about 10%, venues 2-10%) plus vendor subscriptions and marketing add-ons; its app lists 50+ invitation card designs and connects couples with printed and digital card vendors; iOS rating 4.6 from 12 ratings"
      sources: [SRC-12, SRC-43]
    - name: Wedding Wala
      url: https://www.weddingwala.pk/
      notes: "Wedding planning guides and vendor browsing"
      sources: [SRC-19]
  relationship: "Listing and partnership channel (PART-04), not a direct competitor today"
  confidence: medium
```

## 7. Key insights

> Summary: No one has won the Pakistani market, technology is easy to copy, the market is split between DIY tools and slow designers, and print still matters for elders. Label: analysis based on the cited facts.

| ID | Insight | Evidence | Implication |
|---|---|---|---|
| INS-01 | No dominant Pakistani brand yet. At least two of the three platforms look like early, small projects, and prices cluster at PKR 2,999-5,999. | COMP-01, COMP-02, COMP-03 | There is room for a new brand if it launches fast and builds trust. |
| INS-02 | Technology is not a moat. Open-source Pakistani wedding invitation websites built with Next.js are public on GitHub, and a competitor's full stack is public too. | SRC-44, SRC-45, SRC-02 | Compete on service, trust, cultural depth and distribution, not features. |
| INS-03 | The market is split between DIY platforms and DM-only designers. No reviewed Pakistani competitor combines done-for-you service, public prices and a live link. | COMP-01 to COMP-04 | Done-for-you with public prices is open (GAP-01). This is limited to the competitors reviewed (ASSUMPTION beyond that set). |
| INS-04 | Printed cards still matter for elders, and digital-plus-print hybrids are common. | MKT-16, COMP-05 | Bridge print and digital instead of fighting print (GAP-03). |
| INS-05 | Competitors lead with heavy cinematic features, while many guests have limited connectivity. | COMP-01, MKT-07 | Fast, lightweight pages are a differentiator. Competitor page performance was not measured (ASSUMPTION). |
| INS-06 | Indonesia shows the done-for-you, WhatsApp-based, pay-after-approval model working at scale. | GLB-06, GLB-07 | Adopt the same order flow (Q-14, Q-16). |

## 8. Positioning, gaps and non-goals

> Summary: Position as a done-for-you family dawatnama. Target three gaps: done-for-you with public prices, family-first guest management, and a bridge between print and digital. Label: ACCEPTED_REC (this is the answer to Q-30).

### 8.1 Positioning statement

A family sends its details on WhatsApp and, within 24 hours, gets a live invitation that works for every guest, from grandparents to relatives abroad.

### 8.2 Gaps to target

```yaml
- id: GAP-01
  name: Done-for-you with public prices and 24-hour delivery
  priority: primary
  problem: "Pakistani platforms make families build invitations themselves; social media designers hide prices behind DMs and deliver slowly"
  evidence: [COMP-01, COMP-02, COMP-03, COMP-04, GLB-07]
  product_implications: [Q-07, Q-08, Q-14, Q-21]

- id: GAP-02
  name: Family-first guest management
  priority: primary
  problem: "Invitations go to households, not individuals; each side hosts different functions; halls and caterers need headcounts per function"
  evidence: [MKT-02, MKT-11, MKT-12]
  product_implications:
    - Household invites such as "Ahmed Sahab & family" (ENT-06)
    - Headcount per function in RSVP (ENT-07)
    - Pricing per family side (Q-13)

- id: GAP-03
  name: Bridge between print, elders and digital
  priority: primary
  problem: "Many guests are offline or on weak connections, and elders often still receive printed cards"
  evidence: [MKT-07, MKT-16, COMP-05]
  product_implications:
    - Downloadable image of every invitation for forwarding
    - QR code linking printed cards to the live page
    - Lightweight page that loads quickly on low-end phones
    - Printer partnerships (PART-01)

- id: GAP-04
  name: Trust
  priority: secondary
  problem: "Competitors are new with thin social proof, and the strongest one refunds nothing"
  evidence: [COMP-01, COMP-02]
  product_implications: [watermarked preview before payment (Q-14), postponement-friendly policy (Q-18), public reviews (KPI-05)]

- id: GAP-05
  name: Diaspora families paying from abroad
  priority: phase_2
  problem: "Relatives abroad organize or fund weddings in Pakistan, but local tools only take PKR and international tools are not built for Pakistani families"
  evidence: [MKT-13, COMP-07]
  product_implications: [international payments (Q-19), UK and UAE ad targeting (Q-23)]
```

### 8.3 Non-goals for v1

| ID | Non-goal | Reason |
|---|---|---|
| NG-01 | 3D door or gate reveals and scratch-card reveals | COMP-01 already has them; they add build time and page weight on weak connections (INS-05). |
| NG-02 | AI copywriter, QR gate scanner, seating charts | Competitor parity features; not the chosen differentiator. |
| NG-03 | WhatsApp Business API automation | Per-message costs for Pakistan rise from 2026-10-01 (WA-01); automate the website side first (SOP-WA-02). |
| NG-04 | A self-serve editor for customers | Conflicts with the done-for-you model (Q-07); build an internal tool instead. |
| NG-05 | Native mobile app | The founders chose web-based invitations only at the start. |

## 9. Decision log (Q-01 to Q-30)

> Summary: Every planning question, the founders' answer, its status, and the resulting plan. Where the founders said "go with your recommendation", the status is ACCEPTED_REC.

```yaml
- id: Q-01
  topic: Functions supported
  status: DECISION
  founder_answer: "Mehndi, Baraat, Walima, Nikkah, engagement"
  plan:
    - Support the five founder-chosen functions at launch
    - "REC: add Dholki and Mayun as optional functions"
    - "REC: add aqiqah and birthdays after the wedding season"
  evidence: [MKT-11]

- id: Q-02
  topic: Invitation structure for multi-function weddings
  status: ACCEPTED_REC
  plan:
    - One order equals one family side's website, with one section per function that side hosts
    - Per-household links control which functions each household sees (for example, a ladies-only Dholki hidden from other guests)
  evidence: [MKT-12]
  validate: [VAL-02]

- id: Q-03
  topic: Features included in every tier
  status: ACCEPTED_REC
  plan:
    - "All tiers: all functions of that side, Google Maps buttons, countdown, English and Urdu text, WhatsApp share button, downloadable image"
    - "Higher tiers add: RSVP, household links, music, optional photos, custom design"
    - "Photos are optional; pages are unlisted and not indexed by search engines by default"
  rationale: "Some families will not want the bride's photos online (ASSUMPTION)"
  validate: [VAL-03]

- id: Q-04
  topic: RSVP at launch
  status: ACCEPTED_REC
  plan:
    - "RSVP collects household name, functions attending, and headcount per function"
    - "Host gets a private summary link with counts per function plus a CSV export"
    - "No full dashboard in v1"
  evidence: [MKT-02]

- id: Q-05
  topic: Personalized guest links
  status: ACCEPTED_REC
  plan:
    - Included from the Family tier (TIER-02)
    - Generate one link per household from the host's guest list
    - The host sends each link from their own WhatsApp using wa.me click-to-chat links, so there is no API cost
  evidence: [GLB-09, MKT-16, COMP-01]
  rationale: "COMP-01 charges PKR 1,000 per 50 guests for this; individual sending also matches etiquette"

- id: Q-06
  topic: Languages
  status: ACCEPTED_REC
  plan:
    - English and Urdu (right-to-left layout) at launch
    - Arabic only for calligraphy elements such as Bismillah and duas
  evidence: [COMP-01, COMP-02]
  rationale: "Urdu support is already table stakes"

- id: Q-07
  topic: Production model
  status: DECISION
  founder_answer: "It's a website. The client shares details and the team builds the invitation."
  plan:
    - "REC: structured order form produces a JSON config; templates render from the config automatically"
    - "REC: team role is quality-checking each order, targeting about 10 minutes per template order (ASSUMPTION)"
  evidence: [GLB-07]

- id: Q-08
  topic: Delivery time
  status: ACCEPTED_REC
  plan:
    - Template tiers delivered within 24 hours
    - Custom designs delivered in 3-5 working days
    - Paid express option during peak season
    - "DECISION 2026-10-28: 24-hour promise capped at about 5 template orders per day; overflow is quoted 48 hours or waitlisted"
    - "DECISION 2026-10-28: express fee PKR 1,000 for guaranteed 24 hours, offered only when the daily cap is hit (VAL-05 resolved)"

- id: Q-09
  topic: Revisions and edits
  status: ACCEPTED_REC
  plan:
    - Unlimited detail edits until the event, including date and venue changes
    - Custom work includes two design revision rounds; extra rounds are paid
  evidence: [COMP-01]
  rationale: "COMP-01 already offers unlimited edits, so offering fewer is not viable"

- id: Q-10
  topic: Custom templates
  status: DECISION
  founder_answer: "Go with the recommendation, but everything done in-house"
  plan:
    - "Signature (TIER-03): semi-custom, with colours and motifs matched to outfits or the printed card"
    - "Bespoke (TIER-04): fully new design with limited weekly slots"
    - "DECISION 2026-10-28: all four tiers launch; capacity capped at 2 Signature and 1 Bespoke order per week, shown as 'limited slots'"
  risks: [RISK-01]

- id: Q-11
  topic: How long invitations stay live
  status: ACCEPTED_REC
  plan:
    - Classic tier stays live 6 months
    - Higher tiers stay live 1 year
  evidence: [COMP-01, COMP-02]
  rationale: "Beats COMP-01 Classic (3 months) and matches COMP-02 (6 months and 1 year); live pages keep marketing the brand"

- id: Q-12
  topic: Pricing
  status: ACCEPTED_REC
  plan:
    - "Tiers TIER-01 to TIER-04 in section 10.1"
    - "Launch offer: first 30 families get a steep discount in exchange for a public review and showcase permission"
    - "DECISION 2026-10-28: launch discount is 50% (Classic PKR 1,500; Family PKR 2,750) (VAL-04 resolved)"
  evidence: [COMP-01, COMP-02, COMP-03, MKT-04, MKT-10]
  open: [VAL-01, VAL-04]

- id: Q-13
  topic: Pricing unit
  status: ACCEPTED_REC
  plan:
    - Price per family side, covering every function that side hosts
    - When one side orders, offer the other side 25% off
  rationale: "Creates a referral loop into a second family"

- id: Q-14
  topic: Preview before payment
  status: ACCEPTED_REC
  plan:
    - Send a watermarked preview with the family's real names before payment

- id: Q-15
  topic: Payment account
  status: DECISION
  founder_answer: "Raast ID on a personal account"
  plan:
    - Acceptable for launch
    - "REC: move to a business account with a Raast merchant QR as volume grows, after Q-28"
  evidence: [PAY-02, PAY-03]
  risks: [RISK-04]

- id: Q-16
  topic: When payment is taken
  status: ACCEPTED_REC
  plan:
    - "Template tiers: pay after approving the preview, before the watermark is removed"
    - "Custom tiers: 50% upfront, 50% before final delivery"
  evidence: [GLB-07, COMP-05]

- id: Q-17
  topic: Payment verification
  status: DECISION
  founder_answer: "Someone checks"
  plan:
    - "REC: follow SOP-PAY-01; always confirm the transaction ID and amount in the bank app, never from the screenshot alone"
  evidence: [PAY-01]
  risks: [RISK-03]

- id: Q-18
  topic: Refund policy
  status: ACCEPTED_REC
  plan:
    - Full refund before work starts
    - No refund after delivery
    - Postponed wedding gets a free date change
    - Cancelled wedding gets store credit
  rationale: "COMP-01 refunds nothing, so a fair policy builds trust (GAP-04)"

- id: Q-19
  topic: International customers
  status: ACCEPTED_REC
  plan:
    - "Phase 1: relatives in Pakistan pay, or overseas payers use remittance apps that deposit to the bank account"
    - "Phase 2, after NTN registration: add a card payment gateway (COMP-01 uses Safepay)"
  evidence: [PAY-06, PAY-07, PAY-08]

- id: Q-20
  topic: WhatsApp operations
  status: DECISION
  founder_answer: "Manual first, then automation"
  plan:
    - "REC: use the free WhatsApp Business app with labels and quick replies (SOP-WA-01)"
    - "REC: automate the website side before the WhatsApp API (SOP-WA-02)"
  evidence: [WA-01, WA-02, WA-04, WA-06]

- id: Q-21
  topic: Role of the website
  status: ACCEPTED_REC
  plan:
    - Live demo invitations, not screenshots
    - Public price list
    - Structured order form
    - '"Continue on WhatsApp" button that opens a chat with the order number prefilled'

- id: Q-22
  topic: Content creation
  status: DECISION
  founder_answer: "A team member creates content"
  plan:
    - "REC: post daily from October using formats CNT-01 to CNT-05"
    - "DECISION 2026-10-28 (supersedes daily cadence): the founder posts 3 times a week, mainly CNT-01 screen recordings of real orders and CNT-05 showcases (VAL-12 resolved)"
  evidence: [COMP-04]
  validate: [VAL-12]

- id: Q-23
  topic: Paid marketing
  status: DECISION
  founder_answer: "Organic first, paid afterwards"
  plan:
    - "REC: in November and December, boost the 2-3 best-performing organic videos"
    - "REC: add UK and UAE targeting once international payments work"

- id: Q-24
  topic: Partnerships
  status: ACCEPTED_REC
  plan:
    - "PART-01 to PART-04 in section 12.3"

- id: Q-25
  topic: Brand credit on invitations
  status: DECISION
  founder_answer: "Yes"
  plan:
    - "REC: show a subtle 'Made by' credit on every tier except Bespoke, styled like a designer's signature"
    - "REC: show a 'Create yours' button after a guest submits an RSVP"
  evidence: [MKT-02]
  rationale: "Each invitation reaches roughly 249 guests on average"

- id: Q-26
  topic: Team
  status: DECISION
  founder_answer: "Founder is a lead software engineer; partner is a software engineer who also creates content"
  plan:
    - "REC: add a designer for custom work"
    - "REC: add temporary WhatsApp operations help from November to January"
    - "DECISION 2026-10-28: the partner is inactive; the founder is the only person building, designing, delivering and posting, using Claude Code"
  risks: [RISK-01, RISK-02]

- id: Q-27
  topic: Brand name and domain
  status: DECISION
  founder_answer: "DawaatLink is the brand (2026-10-28), overriding the naming rule below"
  plan:
    - "DECISION: brand is DawaatLink; dawaatlink.com is primary, dawaatlink.pk redirects to it; secure @dawaatlink on Instagram and TikTok before posting"
    - "Superseded rule (kept for context):"
    - "Avoid names built on 'Shaadi', 'Qubool' or 'Dawatnama' (collisions with the Shaadi Link matrimonial service, the Qubool matrimonial app, and competitor COMP-02)"
    - Choose a short name that works in both Urdu and English
    - Secure the .com and .pk domains plus Instagram and TikTok handles on the same day
  evidence: [SRC-47, SRC-05, SRC-03]
  risks: [RISK-09]
  resolved: [VAL-06]

- id: Q-28
  topic: Legal setup
  status: DECISION
  founder_answer: "Register the business, but later"
  plan:
    - "REC: register as a sole proprietorship (NTN via IRIS) before 2026-12-01"
    - "REC: then open a business bank account and apply for a payment gateway"
  evidence: [LEG-01, LEG-02, LEG-03]

- id: Q-29
  topic: Success metrics
  status: ACCEPTED_REC
  plan:
    - "KPI-01 to KPI-05 in section 14"
    - "DECISION 2026-10-28: KPI-01 lowered to 150 paid orders and KPI-05 to 30 reviews for a solo founder with a late start"

- id: Q-30
  topic: Which market gap to target
  status: ACCEPTED_REC
  plan:
    - "Positioning and GAP-01 to GAP-03 in section 8"

# Decisions from the 2026-10-28 grilling session

- id: Q-31
  topic: Tech stack
  status: DECISION
  founder_answer: "Next.js + Vercel + Supabase"
  plan:
    - Next.js app renders every invitation from an order config
    - Supabase stores orders and RSVPs
  note: "Same stack family as COMP-01 (SRC-02); pages must still meet the budget in Q-37 and section 10.5"

- id: Q-32
  topic: Where order configs live
  status: DECISION
  founder_answer: "Supabase table"
  plan:
    - "Supabase `orders` table with the invitation config as jsonb, validated by a Zod schema shared with the renderer"
    - Edits go live without a redeploy; watermark and archiving follow the order state (ENT-08)
    - Supabase table editor is the admin tool until the order form exists (Q-36)

- id: Q-33
  topic: Hosting plan
  status: DECISION
  founder_answer: "Vercel Hobby until the business earns, then upgrade to Pro"
  plan:
    - Deploy on Vercel Hobby
    - Upgrade to Vercel Pro (USD 20/month) once revenue starts
  risks: [RISK-12]

- id: Q-34
  topic: Invitation URLs
  status: DECISION
  founder_answer: "Readable slug plus random suffix, household token links"
  plan:
    - "General link: /i/{couple-slug}-{4 random chars}, e.g. /i/ali-sara-7kq2"
    - "Household link: /i/{slug}/h/{about 10-char random token} (ENT-06 invite_token)"
    - "Preview uses the same URL, watermarked until PAYMENT_VERIFIED; no second link"
    - Pages stay noindex (ENT-08)

- id: Q-35
  topic: Order intake during launch weeks
  status: DECISION
  founder_answer: "WhatsApp template first, web form in week 2"
  plan:
    - "Week 1: WhatsApp quick reply with a fill-in text template (names in English and Urdu; per function date, time, venue, Maps link); the founder copies it into the Supabase order row"
    - "Week 2: web order form writing the same Zod-validated config (Q-21)"

- id: Q-36
  topic: Launch strategy and build order
  status: DECISION
  founder_answer: "Hand-build now; build in this order"
  plan:
    - "Start selling immediately (2026-10-28) with hand-built invitations from 1-2 templates; the platform is built alongside real orders"
    - "Build order: (1) config schema + template 1 rendered at /i/[slug] + state-driven watermark; (2) one-page marketing site with price list, 2 live demos and Continue-on-WhatsApp button; (3) RSVP + host summary link + CSV export; (4) household links + wa.me generator; (5) template 2; (6) web order form"
    - "Downloadable image and QR code are made by hand until step 6"
    - "First templates: (1) Urdu-first with Mughal and Islamic motifs for families and elders; (2) modern minimal, English-first; both bilingual and lightweight"

- id: Q-37
  topic: Urdu typography and page weight
  status: DECISION
  founder_answer: "Naskh body + SVG names; 250 KB budget"
  plan:
    - Urdu body text uses a subset of Noto Naskh Arabic
    - The couple's names in Nastaliq are pre-rendered to SVG per order, so guests never download a full Nastaliq font
    - "Guest page first load at most 250 KB compressed (HTML, CSS, JS, font subset, name SVG); music and photos load only on tap"
    - "Lighthouse mobile performance at least 90 on slow 4G (VAL-13 resolved)"

- id: Q-38
  topic: Guest data handling
  status: DECISION
  founder_answer: "Purge on archive + RLS"
  plan:
    - "When an order reaches ARCHIVED, delete household phone numbers and RSVP notes; keep counts"
    - State this on the policy page
    - Row-level security on every Supabase table from the first migration
    - Guests insert RSVPs only through a server route; everything else is read server-side with the service key
    - The service key is never committed (the repository is public)
```

## 10. MVP product specification

> Summary: Tiers, supported functions, order lifecycle, data entities and page requirements derived from the decision log. Label: REC (proposed design, not user-tested; adjust freely where no DECISION applies).

### 10.1 Tiers, pricing and policies

```yaml
tiers:
  - id: TIER-01
    name: Classic
    price_pkr: 2999
    unit: per_family_side
    delivery: 24_hours
    hosting: 6_months
    brand_credit: true
    includes:
      - Template design built by the team
      - All functions hosted by that family side
      - Google Maps button per function
      - Countdown
      - English and Urdu text
      - WhatsApp share button
      - Downloadable image version
      - Unlimited detail edits until the event

  - id: TIER-02
    name: Family
    price_pkr: 5499
    unit: per_family_side
    delivery: 24_hours
    hosting: 1_year
    brand_credit: true
    includes:
      - Everything in Classic
      - RSVP with headcount per function
      - Per-household invitation links with wa.me send links
      - Host summary link with CSV export
      - Background music
      - Optional photo section
      - Printable image with QR code

  - id: TIER-03
    name: Signature
    price_pkr_from: 12999
    unit: per_family_side
    delivery: 3_to_5_working_days
    hosting: 1_year
    brand_credit: true
    includes:
      - Everything in Family
      - Semi-custom design with colours and motifs matched to outfits or the printed card
      - Two design revision rounds

  - id: TIER-04
    name: Bespoke
    price: quote
    delivery: quoted_per_order
    hosting: 1_year
    brand_credit: false
    includes:
      - Fully new design
      - Limited weekly slots

pricing_rules:
  second_side_discount_pct: 25
  launch_offer:
    eligible: first_30_families
    discount_pct: 50              # VAL-04 resolved 2026-10-28; Classic PKR 1,500, Family PKR 2,750
    conditions: [public review, permission to showcase the invitation]
  express_delivery_fee_pkr: 1000  # VAL-05 resolved 2026-10-28; only offered when the daily cap is hit
  capacity:                       # Q-08, Q-10 DECISION 2026-10-28
    template_orders_per_day: 5
    signature_orders_per_week: 2
    bespoke_orders_per_week: 1

payment_rules:
  template_tiers: pay_after_preview_approval
  custom_tiers: {upfront_pct: 50, before_delivery_pct: 50}
  verification: SOP-PAY-01

refund_rules:
  before_work_starts: full_refund
  after_delivery: no_refund
  wedding_postponed: free_date_change
  wedding_cancelled: store_credit

competitor_price_reference_pkr:
  COMP-01: {entry: 3499, premium: 5799}
  COMP-02: {entry: 2999, premium: 5999, note: "currently free on promotion"}
  COMP-03: {entry: 2999}
```

### 10.2 Supported functions

```yaml
functions:
  launch: [nikkah, mehndi, baraat, walima, engagement]   # Q-01 DECISION
  optional_at_launch: [dholki, mayun]                    # Q-01 REC
  after_peak_season: [aqiqah, birthday]                  # Q-01 REC
```

### 10.3 Order lifecycle

```yaml
order_states:
  - state: NEW
    whatsapp_label: New
    meaning: "Customer made first contact"
  - state: DETAILS_RECEIVED
    whatsapp_label: Details received
    meaning: "Order form submitted; WhatsApp chat opened with the order number"
  - state: DEPOSIT_CLAIMED
    applies_to: [TIER-03, TIER-04]
    meaning: "Customer reports paying the 50% deposit and sends the transaction ID"
  - state: DEPOSIT_VERIFIED
    applies_to: [TIER-03, TIER-04]
    meaning: "Deposit confirmed in the bank app; design work may start"
  - state: PREVIEW_SENT
    whatsapp_label: Preview sent
    meaning: "Watermarked preview link sent"
    sla: {template_tiers: 24_hours, custom_tiers: 3_to_5_working_days}
  - state: PAYMENT_CLAIMED
    meaning: "Customer approved the preview, paid, and sent screenshot plus transaction ID"
  - state: PAYMENT_VERIFIED
    whatsapp_label: Paid
    meaning: "Transaction ID and amount confirmed in the bank app"
  - state: PUBLISHED
    whatsapp_label: Delivered
    meaning: "Watermark removed; final link, image and QR code delivered; edits allowed until the event"
  - state: ARCHIVED
    meaning: "Hosting period ended"
  - state: CANCELLED
    meaning: "Cancelled; apply refund_rules"

transitions:
  - {from: NEW, to: DETAILS_RECEIVED}
  - {from: DETAILS_RECEIVED, to: PREVIEW_SENT, condition: "template tiers"}
  - {from: DETAILS_RECEIVED, to: DEPOSIT_CLAIMED, condition: "custom tiers"}
  - {from: DEPOSIT_CLAIMED, to: DEPOSIT_VERIFIED, condition: "SOP-PAY-01 passed"}
  - {from: DEPOSIT_VERIFIED, to: PREVIEW_SENT}
  - {from: PREVIEW_SENT, to: PREVIEW_SENT, condition: "revision round (custom tiers: 2 included)"}
  - {from: PREVIEW_SENT, to: PAYMENT_CLAIMED}
  - {from: PAYMENT_CLAIMED, to: PAYMENT_VERIFIED, condition: "SOP-PAY-01 passed"}
  - {from: PAYMENT_VERIFIED, to: PUBLISHED}
  - {from: PUBLISHED, to: PUBLISHED, condition: "detail edit before the event"}
  - {from: PUBLISHED, to: ARCHIVED, condition: "hosting period ended"}
  - {from: [NEW, DETAILS_RECEIVED, DEPOSIT_CLAIMED, DEPOSIT_VERIFIED, PREVIEW_SENT, PAYMENT_CLAIMED], to: CANCELLED}
```

### 10.4 Data entities

```yaml
entities:
  - id: ENT-01
    name: Order
    fields:
      order_number: string            # short, human-friendly; used in WhatsApp prefilled messages and payment references
      tier_id: "TIER-01 | TIER-02 | TIER-03 | TIER-04"
      state: order_state              # section 10.3
      side: "bride_side | groom_side"
      linked_order_number: "string | null"   # the other side's order, for the 25% discount
      customer_whatsapp: string       # E.164 format, e.g. +923001234567
      language_mode: "en | ur | en_ur"
      template_id: string
      price_pkr: integer
      discount_pct: integer
      created_at: datetime

  - id: ENT-02
    name: Host
    fields:
      display_name_en: string         # e.g. "Mr. & Mrs. Tariq Mahmood"
      display_name_ur: string
      rsvp_contacts: "list of {name, phone}"

  - id: ENT-03
    name: Couple
    fields:
      bride_name_en: string
      bride_name_ur: string
      bride_parents: string
      groom_name_en: string
      groom_name_ur: string
      groom_parents: string

  - id: ENT-04
    name: Function
    fields:
      type: "nikkah | mehndi | baraat | walima | engagement | dholki | mayun"
      date: date
      start_time: "time (PKT)"
      venue_name: string
      venue_address: string
      maps_url: url
      dress_code: "string | null"
      audience: "all_households | selected_households"

  - id: ENT-05
    name: Payment
    fields:
      type: "full | deposit | balance"
      amount_pkr: integer
      method: "raast | bank_transfer | gateway"
      transaction_id: string
      screenshot_url: "url | null"
      status: "claimed | verified | rejected"
      verified_by: "string | null"
      verified_at: "datetime | null"

  - id: ENT-06
    name: Household
    fields:
      display_name: string            # e.g. "Ahmed Sahab & family"
      group: "dadke | nanke | friends | colleagues | other"
      phone: "string | null"
      invited_function_ids: "list of Function ids"
      invite_token: string            # unguessable token used in the personal link

  - id: ENT-07
    name: RSVP
    fields:
      household_id: string
      function_id: string
      attending: boolean
      headcount: integer
      note: "string | null"
      submitted_at: datetime

  - id: ENT-08
    name: PageSettings
    fields:
      noindex: "boolean (default true)"
      watermark: "boolean (true until PAYMENT_VERIFIED)"
      brand_credit: "boolean (false only for TIER-04)"
      photos_enabled: "boolean (default false; privacy-first, see VAL-03)"
      music_track: "string | null"
      hosting_expires_at: datetime

relationships:
  - "Order 1..1 Host; Order 1..1 Couple"
  - "Order 1..n Function; Order 1..n Payment"
  - "Order 0..n Household (TIER-02 and above)"
  - "Household n..n Function (via invited_function_ids)"
  - "RSVP belongs to one Household and one Function"
```

### 10.5 Page requirements

```yaml
guest_page:
  - Opens from a link with no app install or login
  - Loads quickly on low-end Android phones and slow mobile data (budget in Q-37: at most 250 KB compressed first load; Lighthouse mobile at least 90)
  - Shows only the functions the household is invited to when opened through a personal link
  - English and Urdu content with right-to-left support for Urdu
  - Google Maps button and countdown per function
  - RSVP form prefilled with the household name from the link token (TIER-02 and above)
  - "'Create yours' call-to-action after RSVP submission (Q-25)"
  - Not indexed by search engines; unguessable URLs (scheme in Q-34)

host_tools:
  - Private summary link with RSVP counts per function and per household
  - CSV export of RSVPs
  - Generator of one wa.me link per household with a prefilled personal message

deliverables_per_order:
  - Live invitation link
  - Downloadable image for WhatsApp forwarding
  - QR code for printed cards (TIER-02 and above)

public_website:
  - Home page with positioning (section 8.1)
  - Live demo invitations per template
  - Public price list (section 10.1)
  - Structured order form feeding the JSON config (Q-07)
  - '"Continue on WhatsApp" button with prefilled order number (Q-21)'
  - Refund and edit policy page (section 10.1 refund_rules)

internal_tools:
  - Config-driven template renderer (order config in Supabase, Q-32, to invitation page)
  - Automatic watermarked preview generation
  - Order list with states (section 10.3) and payment verification record (ENT-05)
```

## 11. Payments, WhatsApp and legal

> Summary: Screenshot fraud is common, Raast merchant QR is the upgrade path, WhatsApp API costs for Pakistan rise from 2026-10-01, and a sole proprietorship needs only an NTN. Labels: FACT tables, then REC procedures.

### 11.1 Payment facts

| ID | Fact | Data date | Sources | Confidence |
|---|---|---|---|---|
| PAY-01 | Fake payment screenshots are a common scam against Pakistani online sellers; forged receipts include realistic timestamps and transaction IDs | 2026-07 | SRC-46 | medium |
| PAY-02 | Raast P2M merchant QR payments settle directly into the merchant's IBAN, with T+1 settlement and a lower merchant discount rate (Bank Alfalah) | 2026 | SRC-51 | high |
| PAY-03 | JazzCash Business Raast QR credits payments in real time and supports Till ID payments; SBP transaction limits apply | 2026 | SRC-52 | high |
| PAY-04 | SBP subsidy scheme for Raast P2M QR: merchants reimbursed 0.5% of each transaction or PKR 100, whichever is lower; scheme started September 2025 (verify current status) | 2025-10 | SRC-53 | medium |
| PAY-05 | Over 85% of Pakistan's transactions are conducted in cash (study cited in October 2025) | 2025-10 | SRC-53 | medium |
| PAY-06 | Safepay requires onboarding documents including NTN and business age before live payments; preparing documents typically takes 1-2 weeks | 2023-03 | SRC-49 | medium |
| PAY-07 | A 2026 gateway roundup says some providers, such as Safepay, onboard freelancers and unregistered sole proprietors with stricter limits; this conflicts with PAY-06, so confirm directly | 2026-04 | SRC-50 | low |
| PAY-08 | COMP-01 uses Safepay with webhook signature verification for automated checkout | 2026 | SRC-02 | high |

### 11.2 WhatsApp facts

| ID | Fact | Data date | Sources | Confidence |
|---|---|---|---|---|
| WA-01 | From 2026-10-01, Meta charges Pakistani businesses about USD 0.015 per utility, authentication or service message on the API, including replies inside the 24-hour customer window; about 11 times India's USD 0.0014 | 2026-09 | SRC-54 | medium |
| WA-02 | Meta is introducing a free monthly tier of 1,000 service messages per business phone number, while service messages become billable at utility and authentication rates (announced 2026-05-27 with 4 months' notice) | 2026 | SRC-55 | high |
| WA-03 | Pakistan's utility and authentication rates increased on 2026-04-01 | 2026 | SRC-55 | high |
| WA-04 | API access requires a BSP subscription on top of Meta fees; example: WeTarseel from about USD 50 (about PKR 14,000) per month | 2026 | SRC-56 | medium |
| WA-05 | Indicative per-message figures conflict across BSP websites; check Meta's official rate card before any API decision | 2026 | SRC-56, SRC-57 | low |
| WA-06 | The WhatsApp Business app (non-API) is free | 2026 | SRC-56 | medium |
| WA-07 | wa.me click-to-chat links let hosts send personalized invites from their own WhatsApp with no API cost (eInvit uses this) | 2026-07 | SRC-30 | medium |

### 11.3 Legal facts

| ID | Fact | Data date | Sources | Confidence |
|---|---|---|---|---|
| LEG-01 | A sole proprietorship needs only an NTN from FBR; SECP registration is not required | 2026-07 | SRC-48 | medium |
| LEG-02 | NTN registration is done online through the IRIS portal and typically takes 3-4 working days when documents are ready | 2025-11 | SRC-58 | medium |
| LEG-03 | Major banks (HBL, MCB, UBL, Meezan, Bank Alfalah) open sole-proprietor current accounts with an NTN, a proprietorship declaration on letterhead, a business stamp and proof of address; approval commonly takes 1-3 working days | 2026-07 | SRC-59 | medium |

### 11.4 Operating procedures

```yaml
- id: SOP-PAY-01
  name: Payment verification
  label: REC
  steps:
    - Ask the customer to include the order number as the payment reference and to send the transaction ID with the screenshot
    - Open the bank app or statement and find the incoming payment by transaction ID
    - Confirm the amount and date match the order
    - Record the check in ENT-05 (verified_by, verified_at)
    - Only then remove the watermark and send the final link
  never:
    - Deliver based on a screenshot alone (PAY-01)

- id: SOP-WA-01
  name: WhatsApp Business app setup
  label: REC
  labels_in_order: [New, Details received, Preview sent, Paid, Delivered]
  quick_replies:
    - Greeting with price list link and live demos
    - Order form link
    - Preview sent, with approval instructions
    - Payment instructions with Raast ID and order number as reference
    - Payment verified, with final link, image and QR code
    - Edit request received

- id: SOP-WA-02
  name: Automation order
  label: REC
  steps_in_order:
    - Website order form producing structured data
    - Automatic watermarked preview generation
    - Payment matching support
    - WhatsApp Business API, only when manual chat handling cannot keep up and costs are justified (WA-01, WA-02, WA-04)

- id: SOP-LEG-01
  name: Business registration
  label: REC
  deadline: 2026-12-01
  steps_in_order:
    - Register NTN as a sole proprietor through IRIS (LEG-01, LEG-02)
    - Open a business current account (LEG-03)
    - Set up a Raast merchant QR on the business account (PAY-02, PAY-03)
    - Apply for a card payment gateway for international customers (PAY-06)
```

## 12. Marketing and partnerships

> Summary: Short-form content three times a week (updated 2026-10-28), boosts in peak season, and four partnership channels led by card printers. Label: REC unless noted.

### 12.1 Content formats (Q-22)

| ID | Format | Purpose |
|---|---|---|
| CNT-01 | Screen recording of an invitation being opened on a phone | Show the live experience |
| CNT-02 | Printed card cost versus digital invitation cost (use MKT-10) | Justify price |
| CNT-03 | Urdu invitation wording tips for each function | Search, saves and shares |
| CNT-04 | Posts aimed at siblings and parents (for example, "your brother's wedding"), not only couples | Reach the real buyers (COMP-04 shows this format in use) |
| CNT-05 | Real customer showcases from the launch offer | Social proof (GAP-04) |

```yaml
content_plan:
  owner: founder                # Q-22 DECISION; VAL-12 resolved 2026-10-28
  cadence: 3_per_week           # was daily; changed 2026-10-28
  start: 2026-10-28
  platforms: [instagram, tiktok]
paid_plan:                      # Q-23: DECISION organic first; details REC
  start: 2026-11-01
  method: "Boost the 2-3 best-performing organic videos"
  later: "Add UK and UAE targeting once international payments work (GAP-05)"
```

### 12.2 Brand credit (Q-25)

Show a subtle "Made by [brand]" credit on every tier except Bespoke, styled like a designer's signature, plus a "Create yours" button after RSVP submission. Reason: each invitation reaches about 249 guests on average (MKT-02).

### 12.3 Partnerships (Q-24)

| ID | Partner type | Offer | Evidence | Priority |
|---|---|---|---|---|
| PART-01 | Card printers | Bundle a live link and QR code with printed cards; pay the printer a commission | COMP-05 (CardFusion bundles a free e-vite with every order); GAP-03 | 1 |
| PART-02 | Bridal makeup artists and photographers | Referral codes with a customer discount and partner commission | COMP-01 pays creators 10% and gives couples 10% off | 2 |
| PART-03 | Wedding planners and banquet halls | White-label accounts; path to recurring revenue (BM-3) | COMP-07 (WooowInvites offers white-label for planners) | 3 |
| PART-04 | Wedding marketplaces | Get listed on Shadiyana and Wedding Wala | COMP-08 | 4 |

### 12.4 Naming rules (Q-27)

**Update 2026-10-28:** the founder chose **DawaatLink** as the brand, overriding the rules below (RISK-09). Content must make the done-for-you, 24-hour difference obvious so customers do not confuse DawaatLink with DawatNama (COMP-02) or ShaadiLink/Smart Invites (COMP-01).

- Avoid names built on "Shaadi", "Qubool" or "Dawatnama" (SRC-47, SRC-05, SRC-03).
- Pick a short name that is easy to say and spell in both Urdu and English.
- Check and secure the .com domain, .pk domain, Instagram handle and TikTok handle on the same day.

## 13. Launch timeline

> Summary: Updated 2026-10-28: the original MVP and launch dates were missed; selling starts immediately with hand-built invitations while the platform is built (Q-36). Peak in November-December. Label: REC. Dates are based on MKT-13 and MKT-15.

Reason for urgency: invitations for November weddings go out in October, November and December are the busiest months, and many families avoid Ramadan (expected from 2027-02-08).

```yaml
milestones:
  # 2026-10-28: MS-01 to MS-03 were not delivered on their original dates. They now run in parallel from
  # 2026-10-28: selling with hand-built invitations starts at once and the build follows Q-36.
  - id: MS-01
    name: MVP ready
    start: 2026-09-17
    end: 2026-10-01
    status: missed; replaced by the Q-36 build order from 2026-10-28
    deliverables:
      - 4-5 templates, including one Urdu-first and one lightweight template
      - Structured order form feeding the JSON config
      - Automatic watermarked previews
      - RSVP with host summary link and CSV export
      - WhatsApp Business app setup (SOP-WA-01)
      - Brand name, domains and social handles secured (Q-27)
      - Teaser content posted
    stretch:
      - Per-household link and wa.me send-link generator (TIER-02)

  - id: MS-02
    name: Soft launch
    start: 2026-10-01
    end: 2026-10-10
    status: rescheduled; starts 2026-10-28 with hand-built orders
    deliverables:
      - 10-15 weddings from the founders' own network at the launch discount
      - Reviews and showcase videos collected (CNT-05)

  - id: MS-03
    name: Public launch
    start: 2026-10-10
    end: 2026-10-31
    status: rescheduled; begins once the one-page marketing site is live (Q-36 step 2)
    deliverables:
      - Daily posting (section 12.1)
      - Outreach to card printers and makeup artists in the home city (PART-01, PART-02)

  - id: MS-04
    name: Peak season
    start: 2026-11-01
    end: 2026-12-31
    deliverables:
      - Boost best organic videos (section 12.1 paid_plan)
      - Temporary WhatsApp operations help (Q-26)
      - Business registration completed before 2026-12-01 (SOP-LEG-01)

  - id: MS-05
    name: Final pre-Ramadan push
    start: 2027-01-01
    end: 2027-02-07

  - id: MS-06
    name: Ramadan build season
    start: 2027-02-08      # estimate, subject to moon sighting (MKT-15)
    end: 2027-03-09
    deliverables:
      - New event types such as aqiqah and birthdays (Q-01)
      - International payments (Q-19, GAP-05)
```

## 14. KPIs

> Summary: Starting targets to reach by 2027-02-28; recalibrate after the soft launch. Label: ACCEPTED_REC (Q-29).

```yaml
kpis:
  deadline: 2027-02-28
  recalibrate_after: first 15 paid orders   # was MS-02
  items:
    - id: KPI-01
      metric: paid_orders
      target_min: 150               # was 250-300; lowered 2026-10-28 (solo founder, late start)
    - id: KPI-02
      metric: average_order_value_pkr
      target: 4500
    - id: KPI-03
      metric: preview_to_paid_conversion_rate
      target_min: 0.50
    - id: KPI-04
      metric: share_of_orders_from_referrals
      definition: "Orders attributed to brand credits, second-side discounts or partner referral codes"
      target_min: 0.30
    - id: KPI-05
      metric: public_reviews
      target_min: 30                # was 50; lowered 2026-10-28 to match the launch offer
```

## 15. Risks

> Summary: The biggest risks are the missing designer, peak-season overload, payment fraud and the tight timeline. Label: RISK.

| ID | Risk | Likelihood (analysis) | Mitigation | Related |
|---|---|---|---|---|
| RISK-01 | No designer on the team, so custom work (TIER-03, TIER-04) cannot scale; since 2026-10-28 the solo founder is also the designer | High | Hire a part-time or freelance designer; cap bespoke slots per week; build reusable design components | Q-10, Q-26 |
| RISK-02 | WhatsApp chat volume overwhelms the team in November-January | High | Labels and quick replies (SOP-WA-01); order form instead of chat collection; temporary operations help | Q-20, Q-26 |
| RISK-03 | Fake payment screenshots | Medium | SOP-PAY-01 | PAY-01, Q-17 |
| RISK-04 | Business payments into a personal account may draw bank questions as volume grows (ASSUMPTION) | Medium | Keep records per order; register and move to a business account before December | Q-15, SOP-LEG-01 |
| RISK-05 | WhatsApp API costs for Pakistan rise from 2026-10-01 | High if the API is adopted | Stay on the Business app; use wa.me links for guest sending | WA-01, NG-03 |
| RISK-06 | MVP not ready before invitations for November weddings go out | Medium | Keep MS-01 scope tight; defer stretch items | MS-01 |
| RISK-07 | Guests offline or on weak connections, especially elders | High | Downloadable image, QR on printed cards, lightweight pages | MKT-07, GAP-03 |
| RISK-08 | Competitors copy features quickly | High | Compete on service, trust and partnerships rather than features | INS-02 |
| RISK-09 | Brand name collisions with matrimonial services or competitors; accepted 2026-10-28 by choosing DawaatLink | Medium | Content stresses done-for-you and 24-hour delivery (section 12.4) | Q-27 |
| RISK-10 | Families uncomfortable with photos online | Medium | Photos off by default; unlisted pages | Q-03, VAL-03 |
| RISK-11 | Free competitor promotions push price expectations down | Medium | Sell done-for-you service and speed, not features | COMP-02 |
| RISK-12 | Vercel Hobby is limited to personal, non-commercial use, and its terms let Vercel train AI models on hosted content (guest names and phone numbers); the founder accepted this on 2026-10-28 | High once paid orders start | Upgrade to Vercel Pro as soon as revenue starts; keep guest data in Supabase; purge on archive (Q-38) | Q-33 |
| RISK-13 | This knowledge base, including pricing strategy, competitor weaknesses and KPIs, is in a public repository that competitors can read; accepted 2026-10-28 | Medium | Compete on service and trust, not secrecy (INS-02) | Q-36 |
| RISK-14 | One person handles building, design, delivery, WhatsApp and content during peak season | High | Daily and weekly order caps (section 10.1 capacity); 3 posts per week; automate in the Q-36 order | Q-26 |

## 16. Open questions and validation backlog

> Summary: Values that must not be invented and assumptions to test with real customers. Label: OPEN.

| ID | Question | How to resolve | Related |
|---|---|---|---|
| VAL-01 | Are the tier prices (PKR 2,999 / 5,499 / 12,999+) right? | Track preview-to-paid conversion and objections during MS-02 | Q-12, KPI-03 |
| VAL-02 | Do families want per-function audience restrictions, such as a ladies-only Dholki? | Ask the first 15 families | Q-02 |
| VAL-03 | How many families want photos on the invitation? | Ask during onboarding; measure opt-in rate | Q-03, RISK-10 |
| VAL-04 | Launch discount percentage for the first 30 families | **Resolved 2026-10-28:** 50% | Q-12 |
| VAL-05 | Express delivery fee | **Resolved 2026-10-28:** PKR 1,000, only when the daily cap is hit | Q-08 |
| VAL-06 | Brand name | **Resolved 2026-10-28:** DawaatLink | Q-27 |
| VAL-07 | Designer: hire freelance, part-time, or train a team member? | Open; for now the founder designs, with Signature and Bespoke capped (section 10.1) | RISK-01 |
| VAL-08 | Qubool.pk's full tier list, features and policies | Visit the site manually | COMP-03 |
| VAL-09 | Instagram and TikTok designer prices | Message 5-10 sellers as a prospective customer | COMP-04 |
| VAL-10 | Pakistan WhatsApp API per-message rates | Check Meta's official rate card before any API decision | WA-01, WA-05 |
| VAL-11 | Reliable national wedding market size | Find a primary source (survey or official statistics) | MKT-05 |
| VAL-12 | Who owns content creation? Q-22 says a team member; Q-26 says the partner creates content | **Resolved 2026-10-28:** the founder, 3 posts per week | Q-22, Q-26 |
| VAL-13 | Page-weight budget for guest pages | **Resolved 2026-10-28:** at most 250 KB compressed first load, Lighthouse mobile at least 90 (Q-37); still test on a low-end Android phone | section 10.5 |

## 17. Source registry

> Summary: Every external source used, with URL and publication date where known. All sources were accessed on 2026-09-17. Label: FACT.

| ID | Publisher / title | URL | Published or updated | Used for |
|---|---|---|---|---|
| SRC-01 | Smart Invites homepage (shaadilink.com.pk redirects here) | https://www.smartinvites.com.pk | unknown | COMP-01 |
| SRC-02 | GitHub: Raufkhalid78/shaadilink | https://github.com/Raufkhalid78/shaadilink | unknown | COMP-01, PAY-08, INS-02 |
| SRC-03 | DawatNama homepage | https://www.dawatnama.app/ | unknown | COMP-02, Q-27 |
| SRC-04 | Qubool.pk homepage metadata | https://qubool.pk/ | unknown | COMP-03 |
| SRC-05 | Qubool matrimonial app (Apple App Store) | https://apps.apple.com/us/app/qubool/id1546200587 | unknown | COMP-03, Q-27 |
| SRC-06 | Instagram @ecards.pk | https://www.instagram.com/ecards.pk/ | unknown | COMP-04 |
| SRC-07 | Instagram @sketchbookstudio.pk | https://www.instagram.com/sketchbookstudio.pk/ | unknown | COMP-04 |
| SRC-08 | Instagram @weddingcardskarachi | https://www.instagram.com/weddingcardskarachi/ | unknown | COMP-04 |
| SRC-09 | TikTok discover: Pakistani wedding invitation | https://www.tiktok.com/discover/pakistani-wedding-invitation?lang=en | about 2026-09-10 | COMP-04 |
| SRC-10 | Profit (Pakistan Today): Karachi wedding sector adds Rs33 billion | https://profit.pakistantoday.com.pk/2026/01/15/karachi-wedding-sector-adds-rs33-billion-to-local-economy-in-2025/ | 2026-01-15 | MKT-01, MKT-02, MKT-03 |
| SRC-11 | Business Recorder: weddings generated Rs33bn for Karachi's economy | https://www.brecorder.com/news/40402372/beyond-the-baraat-weddings-generated-rs33bn-for-karachis-economy-in-2025 | 2026-01-16 | MKT-01 |
| SRC-12 | Dawn: Mideast war taking a toll on Pakistan's wedding economy | https://www.dawn.com/news/1998854 | 2026-05-09 | MKT-04, MKT-05, MKT-06, COMP-08 |
| SRC-13 | The Friday Times: Pakistan's wedding competitions | https://www.thefridaytimes.com/22-Jul-2026/pakistan-s-wedding-competitions | 2026-07-22 | MKT-05, MKT-11 |
| SRC-14 | DataReportal: Digital 2026 Pakistan | https://datareportal.com/reports/digital-2026-pakistan | 2025-11-08 | MKT-07, MKT-08 |
| SRC-15 | PhoneWorld: Economic Survey digital adoption | https://www.phoneworld.com.pk/pakistan-smartphone-usage-71-percent-economic-survey-2026/ | 2026-06-12 | MKT-09 |
| SRC-16 | The Framers: wedding card price in Pakistan 2026 | https://theframers.pk/blog/wedding-card-price-in-pakistan/ | 2026-06-20 | MKT-10, COMP-05 |
| SRC-17 | CardFusion UK: Pakistani wedding cards | https://www.cardfusion.co.uk/pakistani-wedding-cards/ | 2026-05-05 | MKT-12, COMP-05 |
| SRC-18 | One Time Bridals: Pakistani wedding season 2026 guide | https://rent.onetimebridals.shop/pakistani-wedding-season-2026-guide/ | 2026-07-03 | MKT-13 |
| SRC-19 | Wedding Wala: Pakistani wedding checklist and timeline | https://www.weddingwala.pk/pakistani-wedding-checklist-and-timeline | 2026-06-14 | MKT-14, COMP-08 |
| SRC-20 | Wego Travel Blog: Ramadan in Pakistan | https://blog.wego.com/ramadan-in-pakistan/ | 2026-04-22 | MKT-15 |
| SRC-21 | InviteNova: how to send wedding invitations on WhatsApp | https://invitenova.com/blog/how-to-send-wedding-invitations-on-whats-app | 2026-07-07 | MKT-16 |
| SRC-22 | Paperlust: wedding website builders compared | https://paperlust.co/blog/wedding-website-builders-compared/ | 2026-08-11 | GLB-01 |
| SRC-23 | Bliss & Bone: best free wedding websites 2026 | https://blissandbone.com/resources/free-wedding-websites | 2026-05-27 | GLB-02 |
| SRC-24 | The Knot: best wedding websites | https://www.theknot.com/content/best-wedding-websites | 2026-03-05 | GLB-03 |
| SRC-25 | Woman Getting Married: wedding websites reviewed | https://www.womangettingmarried.com/the-best-wedding-websites-reviewed/ | 2026-05-01 | GLB-04 |
| SRC-26 | Sannubari: digital wedding invitation pricelist 2026 | https://sannubari.com/pricelist-undangan-digital-pernikahan/ | 2026-06-25 | GLB-05 |
| SRC-27 | Inveet homepage | https://inveet.id/ | unknown | GLB-06 |
| SRC-28 | LoveLink homepage | https://lovelink.id/ | unknown | GLB-07 |
| SRC-29 | LinkUndangan homepage | https://www.linkundangan.com/ | unknown | GLB-08 |
| SRC-30 | eInvit homepage | https://einvit.in/ | 2026-07-15 | GLB-09, WA-07, COMP-07 |
| SRC-31 | Weddingkart: wedding guest WhatsApp | https://www.weddingkart.co/tools/guest-communication-whatsapp | 2026-04-24 | GLB-10, COMP-07 |
| SRC-32 | TikTok discover: digital invitation Islamic wedding | https://www.tiktok.com/discover/digital-invitation-islamic-wedding | about 2026-08-27 | GLB-11 |
| SRC-33 | weds.pk homepage | https://weds.pk/ | unknown | COMP-05 |
| SRC-34 | invitationcards.pk: digital cards | https://invitationcards.pk/product-category/digital-cards/ | unknown | COMP-05 |
| SRC-35 | Zem Printers (weddingsadda.com) | https://weddingsadda.com/ | unknown | COMP-05, Q-16 |
| SRC-36 | Wedding Card Experts homepage | https://weddingcardexperts.com/ | unknown | COMP-05 |
| SRC-37 | Etsy: Pakistani wedding cards digital | https://www.etsy.com/market/pakistani_wedding_cards_digital | unknown | COMP-06 |
| SRC-38 | Zazzle: Pakistani wedding invitations | https://www.zazzle.com/pakistani+wedding+invitations | unknown | COMP-06 |
| SRC-39 | Invyt: Nikah planner | https://www.invyt.app/nikah-planner | unknown | COMP-07 |
| SRC-40 | Nikahly homepage | https://www.nikahly.co.uk/ | unknown | COMP-07 |
| SRC-41 | WooowInvites homepage | https://www.wooowinvites.com/ | unknown | COMP-07, PART-03 |
| SRC-42 | Trustpilot: WooowInvites reviews | https://www.trustpilot.com/review/www.wooowinvites.com | 2026-08-13 | COMP-07 |
| SRC-43 | Shadiyana app (Apple App Store, Pakistan) | https://apps.apple.com/pk/app/shadiyana-plan-your-shadi/id6741158634 | unknown | COMP-08 |
| SRC-44 | GitHub: bakartechnology/wedding-invitation | https://github.com/bakartechnology/wedding-invitation | unknown | INS-02 |
| SRC-45 | GitHub: shaheersohail254-droid/weddinginvite | https://github.com/shaheersohail254-droid/weddinginvite | unknown | INS-02 |
| SRC-46 | WikiTechLibrary: common online frauds and scams in Pakistan 2026 | https://wikitechlibrary.com/common-online-frauds-and-scams-pakistan/ | 2026-07-08 | PAY-01 |
| SRC-47 | Shaadi Link matrimonial service (Facebook) | https://www.facebook.com/shaadilink.org | unknown | Q-27 |
| SRC-48 | HR Business Solutions: register a sole proprietorship in Pakistan | https://hrbs.com.pk/how-to-register-sole-proprietorship-in-pakistan/ | 2026-07-22 | LEG-01 |
| SRC-49 | Safepay Knowledge Base: merchant onboarding form | https://safepay.helpscoutdocs.com/article/118-merchant-onboarding-form | 2023-03-01 | PAY-06 |
| SRC-50 | Hostedium: best payment gateways in Pakistan | https://www.hostedium.com/5-best-payment-gateways-in-pakistan-for-ecommerce/ | 2026-04-30 | PAY-07 |
| SRC-51 | Bank Alfalah: Raast P2M QR | https://www.bankalfalah.com/business-banking/retail-payment-solution/raast-p2m-qr/ | unknown | PAY-02 |
| SRC-52 | JazzCash: Raast QR payments | https://www.jazzcash.com.pk/business/accept-payments/qr-raast-payments | unknown | PAY-03 |
| SRC-53 | The Express Tribune: SBP to use Raast for government payments | https://tribune.com.pk/story/2570322/sbp-to-use-raast-for-govt-payments | 2025-10-03 | PAY-04, PAY-05 |
| SRC-54 | TechX.pk: WhatsApp Business API pricing in Pakistan versus India | https://techx.pk/whatsapp-business-api-pakistan-pricing-india-comparison/ | 2026-09-16 | WA-01 |
| SRC-55 | Meta for Developers: WhatsApp Business Platform pricing | https://developers.facebook.com/documentation/business-messaging/whatsapp/pricing | unknown | WA-02, WA-03 |
| SRC-56 | WeTarseel: WhatsApp API pricing for Pakistan 2026 | https://wetarseel.ai/whatsapp-api-pricing-for-pakistan-2026/ | 2026 (updated February 2026) | WA-04, WA-05, WA-06 |
| SRC-57 | Ominiflow: WhatsApp API pricing Pakistan | https://ominiflow.com/whatsapp-api-pricing/pakistan | 2026-06-19 | WA-05 |
| SRC-58 | Vohra Law Associates: individual NTN registration | https://vohralaw.pk/individual-ntn-registration/ | 2025-11-22 | LEG-02 |
| SRC-59 | LegalPK: sole proprietorship registration in Pakistan | https://legalpk.com/blog-post/sole-proprietorship-registration-pakistan | 2026-07-10 | LEG-03 |

## 18. Changelog

| Version | Date | Change |
|---|---|---|
| 1.0.0 | 2026-09-17 | Initial knowledge base compiled from market research, competitor research and founder Q&A (Q-01 to Q-30). |
| 1.1.0 | 2026-10-28 | Grilling session: solo founder, rolling launch, DawaatLink brand, stack/hosting/URL/data decisions (Q-31 to Q-38), capacity caps, KPI recalibration, VAL-04/05/06/12/13 resolved, RISK-12 to RISK-14 added. |
