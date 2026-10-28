# DawaatLink — Domain Context

DawaatLink builds web invitation pages for Pakistani wedding functions, done for you: a family sends its details on WhatsApp and the team delivers a live invitation link. Business decisions, research, pricing and the decision log live in [`docs/kb.md`](docs/kb.md); cite its IDs (`Q-*`, `TIER-*`, `ENT-*`) rather than copying text.

## Product language

| Term | Meaning | Avoid |
|---|---|---|
| **Order** | One family side's purchase: one invitation site covering every function that side hosts (ENT-01, Q-02). | "invitation" when you mean the purchase |
| **Side** | The bride's family (*larki walay*) or the groom's family (*larke walay*). The pricing unit; each side orders separately (Q-13). | "client", "couple" as the buyer |
| **Linked order** | The other side's order, which gets 25% off. | |
| **Function** | One event within a wedding: nikkah, mehndi, baraat, walima, engagement, plus optional dholki and mayun (ENT-04). | "event" for a single function |
| **Host** | The family member(s) named as inviting, e.g. "Mr. & Mrs. Tariq Mahmood" (ENT-02). | |
| **Household** | A family unit invited as one, e.g. "Ahmed Sahab & family". Guest lists are households, not individuals (ENT-06). | "guest" for the invited unit |
| **Household link** | A personal URL `/i/{slug}/h/{token}` showing only the functions that household is invited to (Q-34). | "guest link" |
| **RSVP** | A household's reply for one function: attending and headcount (ENT-07). | |
| **Host summary link** | Private link showing RSVP counts per function and household, with CSV export (Q-04). | "dashboard" |
| **Tier** | Classic, Family, Signature or Bespoke (TIER-01 to TIER-04). Classic and Family are *template tiers*; Signature and Bespoke are *custom tiers*. | "plan", "package" |
| **Order config** | The jsonb config in the Supabase `orders` table, validated by a shared Zod schema, from which a template renders the invitation (Q-32). | |
| **Template** | A design that renders any order config. | |
| **Preview** | The invitation at its final URL, watermarked, sent before payment (Q-14, Q-34). | "draft", "mockup" |
| **Watermark** | Shown until the order reaches `PAYMENT_VERIFIED` (ENT-08). | |
| **Order state** | `NEW` → `DETAILS_RECEIVED` → (`DEPOSIT_CLAIMED` → `DEPOSIT_VERIFIED` for custom tiers) → `PREVIEW_SENT` → `PAYMENT_CLAIMED` → `PAYMENT_VERIFIED` → `PUBLISHED` → `ARCHIVED`, or `CANCELLED` (KB section 10.3). | |
| **Claimed / verified payment** | Claimed = the customer says they paid (screenshot + transaction ID). Verified = confirmed in the bank app per SOP-PAY-01. Never deliver on a claim. | |
| **Brand credit** | The subtle "Made by DawaatLink" signature on every tier except Bespoke (Q-25). | |

## Wedding terms

| Term | Meaning |
|---|---|
| Nikkah (Nikah) | Islamic marriage contract ceremony |
| Mehndi (Rasm-e-Hina) | Henna celebration; each side may host its own |
| Baraat (Barat) | The groom's family arrives at the bride's family's event; often includes Rukhsati |
| Walima (Valima) | Reception hosted by the groom's family after the marriage |
| Engagement (Mangni) | Formal engagement ceremony |
| Dholki | Pre-wedding musical gathering, often at home; may have a restricted audience |
| Mayun (Mayoun) | Pre-wedding ritual before Mehndi |
| Dawatnama | Urdu for invitation letter; also the competitor COMP-02 |
| Shagun / Salami | Cash gifts at functions (possible later feature) |
| Dadke / Nanke | Paternal / maternal relatives; household groups |

## Payments and channels

| Term | Meaning |
|---|---|
| Raast / Raast ID | SBP instant payments; a Raast ID is a mobile-number alias for a bank account (payment v1) |
| Raast P2M QR | Merchant QR payments; the upgrade path after NTN registration |
| NTN / IRIS | National Tax Number from FBR, registered on the IRIS portal |
| wa.me link | WhatsApp click-to-chat URL with prefilled text; how hosts send household links at no API cost |
