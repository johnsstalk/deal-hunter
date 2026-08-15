# Deal Hunter Community — Community Verification (Reddit-first)

Load this file for **every shortlisted product** before a verdict. Platform reviews are curated and gamed — communities are not. This is how you find out what a product is *really* like after weeks/months of real use, before spending money.

> [!abstract] The core rule
> **Store reviews tell you the launch story. Communities tell you the ownership story.** If a product has glowing ratings but a wall of "it broke after 3 months" posts, it is not a deal at any price. Verify in communities *before* the verdict, not after.

## Where to look (in priority order)

### 1. Reddit (primary)
Search the subreddit that matches the category, then filter for **long-term ownership** posts and old threads (sort by new, check 6+ month-old posts).

| Category | Subreddits |
|----------|------------|
| General purchases | r/BuyItForLife, r/IndianBeautyDeals (beauty), r/Frugal_Ind |
| PCs & parts | r/IndianGaming, r/BuildAPCIndia, r/IndianDeals |
| Used PC parts | r/IndianGaming (bazaar/market threads), TechEnclave buy-sell, Gamer's Loot, ZedUpgrade |
| Phones & gadgets | r/GadgetsIndia, r/Android, r/IndianDeals |
| Audio | r/headphones, r/audiophile, r/IndianGaming (peripheral threads) |
| Appliances / home | r/IndiaSpeaks (occasionally), category subs, r/BuyItForLife |
| Cameras | r/AskPhotography, r/india (tech megathreads) |

Search patterns that find the truth:
- `"<product>" review` — recency + depth filter
- `"<product>" after <N> months` / `"<product>" still working` — durability signal
- `"<product>" vs "<competitor>"` — head-to-head from real owners
- `"<product>" refund` / `"<product>" broken` / `"<product>" doa` — failure signals
- On the subreddit: `sort=new` on the search, then read the 6–18-month-old threads too

### 2. X (Twitter) & YouTube
- Search `"<product>" long-term` / `"<product>" review honest` — reviewers who buy their own units
- YouTube: look for **6-month/long-term review** videos, not just launch-day first impressions; check comment sections for owners reporting failures
- Red flag: all reviewers got the unit free from the same PR drop = launch-hype echo chamber

### 3. Indian tech forums & communities
- **TechEnclave** — the serious Indian hardware forum; search model names, owner threads, market-price threads
- **XDA Forums** — phones, custom ROM, hardware quirks
- **erodov** — older Indian gadget forum, good for legacy product durability reports
- **Indicarr / WhatsApp / Telegram deal groups** — deal alerts, not quality verdicts (use for price, not quality)

### 3b. Used & second-hand marketplaces
Used purchases skip platform protections — so community verification is *more* important, not less. Where the Indian used market actually lives:
- **TechEnclave buy-sell** — the serious hardware forum; check user join-date, heat score, and deal threads before wiring money
- **r/IndianGaming bazaar/market threads** — search `market` / `bazaar`; private sellers, cash-on-delivery preferred
- **Gamer's Loot** — established gaming hardware reseller; still verify the specific listing
- **ZedUpgrade** — Apple/Mac refurb specialist; confirm the grading and warranty terms
- **Flipkart/Amazon "renewed" & official refurb** — platform-backed (7-day return), safer than private sales, but the warranty is usually the refurbisher's, not the brand's

Private-sale rules: advance payment to an unknown seller = scam signal; **no-return is the norm** for private sales, so price in the risk and test before final payment. Full on-spot testing + warranty-transfer reality in `references/used.md`.

### 4. Complaint portals (last resort, high signal)
- **consumerhelpline.gov.in / National Consumer Helpline (NCH)** — registered complaints per brand/model
- **Consumer Voice / Local Circles** — category-level complaint reports
- **X @ brand handle** — "my X broke after Y months, no support" threads cluster here

## What you're looking for

- **Long-term ownership experiences** — someone who's used it for weeks/months, not a first-day reviewer
- **Recurring failure modes** — the *same* problem in multiple threads ("battery swelled", "card reader died", "band snapped")
- **Service-center reality** — how the brand's warranty actually behaves (does support respond? do they replace?)
- **Honest verdicts on hype** — "bought it because of reviews, would not rebuy"

## Paid-plant & astroturf detection

- **All-positive, launch-day accounts** — accounts created near launch, only posting hype
- **Coordinated phrasing** — several "reviews" using the same unusual phrases
- **Contradiction between store reviews and community** — 4.5★ on Amazon but "avoid this brand" consensus on Reddit = store reviews are gamed
- **Incentivized reviews** — refund-for-review, extra-warranty-for-review programs (Amazon "invite" review batches, "supplemented review" badge groups)
- **Giveaway/PR-drop echo chambers** — everyone reviewing the *same* unit from the same PR batch

## Weighting the evidence

| Signal | Trust |
|--------|-------|
| Multiple independent long-term ownership posts (6+ months) | **High** — decide on this |
| One detailed teardown/service story | Medium-High |
| Single "broke after a month" post | Medium — check for more |
| Launch-day hype / all-positive burst | Low — ignore for verdicts |
| Store reviews alone | Low — verify elsewhere |

## Used & second-hand specifics (what to dig for)

When the candidate is used/refurb, add these community signals on top of the normal ones:
- **Mining-card history** — "used for gaming only", GPU sag/card aesthetics, and owner threads on the specific model's used-market red flags; mining cards run hot 24/7 and fail early
- **Warranty-transfer reality** — will the brand honor a transferred warranty, or is it non-transferable/voided? Read owner reports, not the marketing line
- **Battery / degradation** — for phones/laptops: reported battery health, replaceability, and price of the replacement battery
- **IMEI / serial checks** — for phones: IMEI blacklist (stolen/blocked), check on brand portals; never buy prepaid-to-unknown for a device
- **Refurb-grading honesty** — "renewed" grading (e.g. Mint/Good/Fair) in Indian listings often means cosmetic damage; check the refund window and whether the warranty is the refurbisher's
- **Seller patterns** — brand-new accounts, one listing, "urgent, no questions" tone = red flags; established marketplaces/heat are the only soft safety net

## Recording it

- For the verdict, cite **which community and what it said** in the tracker row (e.g. `TechEnclave: 2 owner threads, 1 cracked after 8 mo`)
- The user's own Reddit research/drafts live under the `type/reddit-draft` tag — reuse those threads as evidence when relevant
- Link the strongest thread as the clipping if saving to the vault

## Related

- `prompt.md` — JOB 2.6 (community verification) is part of every analysis
- `india.md` — platform map + scam safety for the Indian market
- `tracker.md` — where the community verdict gets recorded
