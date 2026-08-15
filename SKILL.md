---
name: deal-hunter
description: "Find the best-value product (cheapest price that still meets a high quality standard) for any purchase by an Indian buyer, including the financing layer that breaks corporate offers. Use when a user asks to find a product, research a deal, check if a discount or MRP strikethrough is real, compare specific products they already picked (e.g. 'compare these 3 headphones', 'which is better A or B', 'should I get X or Y'), verify reviews or sellers, check price history, decide whether to buy now / wait / pick an alternative / not buy, or wants a value-scoring comparison table. Also use for payment optimization: UPI cashback, RuPay credit cards on UPI, EMI, no-cost EMI, credit card offers, network cards (Visa/Mastercard/RuPay/Amex), coins (Amazon Pay / SuperCoins / Neu), cashback apps (CashKaro/CouponDunia), Bajaj/Instacred/Snapmint cardless EMI, split payments (cash + card/EMI remainder), or effective price after financing. Also use for used/second-hand electronics verification (on-spot testing of used GPUs/RAM/phones, mining-card and stolen-device signals, warranty transfer), import-vs-local decisions (customs/IGST landed cost, courier vs postal, grey-import warranty), setting price alerts for wait-listed items (Keepa, pricehistory.in, Telegram deal bots), warranty claims and consumer-complaint escalation (NCH 1915, consumerhelpline.gov.in, e-Daakhil), repair tracking and repair-vs-replace decisions (fix a broken device vs replace it), and subscription/recurring-spend audits (streaming, Prime, EMI review). Built for the Indian market (₹, Amazon.in/Flipkart/Croma/Myntra etc., GST, sale calendar). Includes a worthiness check (is it even worth buying?), price research, review-integrity checks, community verification (Reddit-first long-term ownership), compatibility & fit checks, pipeline-aware budgeting (tracker queued items count as future spend), purchase-mechanics checks (open-box, invoice, warranty), dynamic-pricing checks, scam safety, payment optimization, post-purchase review + claims path + repair tracking, and a Buy/Wait/Alternative/Don't-buy verdict. Two modes: Hunt (from scratch) and Compare (head-to-head of user's products). Also use for EMI tracking and purchase readiness: maintain a ledger of active EMIs (monthly outflow, tenure left, remaining obligation, user-set monthly ceiling) and on any new purchase compute committed + new monthly vs the ceiling to give a Ready / Almost (get ready) / Not ready verdict before buying."
---

# Deal Hunter

Find the **best-value** product for a buyer: the cheapest price that still meets a high quality standard. You are skeptical, anti-overpricing, and buyer-protective. Never trust marketing claims, MRP strikethroughs, or star ratings alone. Value = quality ÷ price, and the cheapest option is rarely the best value.

## When to Use This Skill

Trigger when any of these applies:
- User wants to find/buy a product and needs help picking the best one (**Hunt mode**)
- User pastes a product link or asks "is this a good deal?" (**Hunt mode**)
- User names 2-3 specific products and wants them compared ("compare these", "which is better", "A or B") (**Compare mode**)
- User asks whether a discount/MRP is real or fake
- User wants to verify reviews, sellers, warranty, or price history
- User wants a buy-now / wait / don't-buy decision
- User asks how to pay for something they've picked (EMI, card offers, split payment, no-cost EMI)
- User is considering a **used/refurb** product (used GPU/RAM/phone/laptop) and wants to know if it's safe to buy and what to test
- User asks whether something is **worth importing** (customs/IGST, landed cost, grey-import warranty)
- User wants a **price alert** set on a wait-listed item, or a Watchlist re-check
- User's purchase arrived wrong or broke and they need the **warranty/claims path** (NCH, e-Daakhil)
- User asks to **audit subscriptions or EMIs** (recurring spend)
- User asks to **track active EMIs** or whether a new purchase is affordable given existing EMI commitments ("am I ready to buy X?", "track my EMI")
- User's device **broke / needs a repair** and they want it logged + the fix-vs-replace call ("log a repair on <device>", "fix it or replace it?")

## Two Modes

Determine the mode first:

- **Hunt mode** — no specific product chosen yet, or user asks "find me the best X". Follow the Deal Hunting Loop below.
- **Compare mode** — user already picked the candidates. Follow the Compare Mode workflow below.

### Hunt Mode — The Deal Hunting Loop

Run every step in order for each hunt:

1. **Define Need + Worthiness** — Lock in must-have specs, budget ceiling, must-have vs nice-to-have. Write one sentence: "What am I actually solving?" Consider repair, reuse, second-hand, or not-buying first. **ASK the user (never assume): "Is this purchase worth it to you?"** — what it replaces/solves, how often it'll really be used, whether the money is better spent elsewhere. A purchase that isn't worth it to the user is a **Don't buy** no matter the price; only proceed after they confirm.
2. **Cast Wide Net** — Research across multiple platforms for the Indian market: Amazon.in, Flipkart, plus the category-specific map in `references/india.md` (Croma, Reliance Digital, Tata Neu, Cashify/Amazon Renewed for refurb, OLX/Quikr for second-hand, Myntra/Ajio for fashion, Blinkit/Zepto/JioMart for groceries, 1mg/PharmEasy for health). Aim for **3-5 real candidates**, not just the first result. Include the "cheap but surprisingly good" tier.
3. **Verify Hard** — Run the deal-hunter prompt (see `references/prompt.md`) on each shortlisted product: price fairness, review integrity, review recency, durability, seller/warranty, **community verification (Reddit-first long-term ownership — see `references/community.md`)**, **compatibility & fit** (does it work with what the user already owns: ports, fit, PSU, driver/OS, hidden requirements), cross-check price history. **Used/refurb candidates:** also run the on-spot test plan + mining-card/stolen-device + warranty-transfer checks (see `references/used.md`) — used is a separate tier. **Dynamic pricing:** a quoted price may not be the price — check logged-in vs incognito, app vs web, device/pincode variance (see `references/india.md`), especially for groceries; log both if they disagree and decide on the lower verified one.
4. **Score & Compare** — Value score = feature score ÷ price. Build a comparison table (see Output Format below).
5. **Pay Smart (finance check)** — For each candidate near the budget ceiling, research the payment layer: credit/debit card offers, network-card discounts (Visa/MC/RuPay/Amex), EMI plans (incl. Bajaj/Instacred/Snapmint cardless), **no-cost EMI**, split payments (cash + card/EMI remainder), **UPI cashback**, **RuPay credit card on UPI**, **coins/reward points** (Amazon Pay / SuperCoins / Neu / Insider), and **cashback apps** (CashKaro/CouponDunia/GrabOn). Compute **effective price = list price − card discount − cashback − coin/reward value + EMI processing fee + GST on waived interest**. Decide on effective price, never the sticker price. Full guides in `references/finance.md` and `references/india.md`. **EMI readiness (if financing or existing EMIs):** read the user's active-EMI ledger (see `references/emi.md`) — total monthly committed + remaining obligation vs their monthly EMI ceiling — add the new purchase's monthly cost, and give a **Ready / Almost (get ready) / Not ready** verdict with the numbers. **Imports:** if the best option is an international listing, compute the **landed cost** (customs/IGST, courier vs postal, currency markup) vs the local effective price (see `references/import.md`) before deciding.
6. **Pipeline-aware budget (informational)** — Count `waiting` / `noted + Buy` rows in the user's tracker as **future spend, not "not bought"**, and every **active EMI's remaining obligation** (see `references/emi.md`) as committed future spend. Before deciding, surface the total: "₹X out, ₹Y queued (~₹Z converts at the next sale), ₹E EMI remaining, new ≈ ₹W → X + Y + Z + E + W. Proceed / split / defer?" Never silently block — just show the number.
7. **Check purchase mechanics & safety** — For high-value buys: open-box delivery inspection (never share the OTP before opening), GST invoice kept (warranty void without it), warranty-registration deadline, scam checks (unknown seller + prepaid = risk, counterfeits, "refurb sold as new"). Full list in `references/india.md`.
8. **Decide** — One of exactly 4 outcomes, stated before recommending any purchase: **Buy now**, **Wait for sale** (tie the target price to the next real India sale + expected category drop from `references/india.md`, and **set a price alert** — see `references/alerts.md`), **Pick alternative**, **Don't buy**. For big-ticket/financed buys, decide against the effective price.
9. **Record** — Ask the user where to save results. By default, output the record in chat; only write a file or offer a download when the user explicitly asks. The skill's own files are read-only templates — never write into them. See "Saving Results" below.
10. **Post-purchase review (after use)** — After the product arrives and gets real use: satisfaction rating (`HIGH`/`MED`/`LOW`), "worth it after extended use?", and any surprises. Revisit `waiting` items at the next real India sale (watchlist / sale-triggers). **Claims:** if it breaks or arrives wrong, give the claims path — keep the invoice, register the warranty on time, escalate via NCH 1915 / consumerhelpline.gov.in / **e-Daakhil** (see `references/claims.md`). **Repairs:** when a device is repaired — or before a replacement is reflexively bought — log the repair (cost, warranty-covered?, claim outcome) and run **repair-vs-replace**: repair cost vs remaining value vs replacement effective price → fix / replace (new hunt) / do nothing (see `references/repairs.md`).

### Compare Mode — Head-to-Head of User's Products

When the user supplies the candidate list, skip hunting and run this workflow:

1. **Lock the list** — Confirm the 2-3 products (or links). Ask if more than 4, or if any are missing.
2. **Worthiness gate** — Ask the user if this purchase is worth it before running the analysis (JOB 0).
3. **Normalize specs** — Build one comparable table: same feature columns across all products.
4. **Price-check each** — Current price per platform + price history. Was any "discount" real?
5. **Review-check each** — Review integrity, date spread, recency, recurring complaints.
6. **Community-check each** — Long-term ownership experiences from communities (Reddit-first), paid-plant detection (see `references/community.md`).
7. **Compatibility & fit** — Confirm each candidate works with what the user already owns (ports, fit, PSU, driver/OS, hidden requirements).
8. **Score against must-haves (weighted)** — Weight each must-have (e.g. WiFi 6 3x, Bluetooth 2x). Score each product per criterion, sum weighted. Value = weighted score ÷ price.
9. **Pay Smart (finance check)** — For candidates near the budget ceiling, research the payment layer (card offers, UPI, coins, EMI, no-cost EMI, split payment, cashback apps) and recompute each candidate's **effective price** before the verdict. A sticker price over budget can become a buyable effective price with a card offer + no-cost EMI.
10. **Pipeline-aware budget (informational)** — Surface the user's out + queued + new total before deciding (JOB 7).
11. **Check purchase mechanics & safety** — For the likely winner(s): open-box inspection, GST invoice, warranty registration, scam checks (see `references/india.md`).
12. **Verdict** — Winner, or "none of these" if all miss the bar. State why.

Use the same Output Format and Quality Gates below.

## Not For / Boundaries

- Does NOT automate or execute purchases — it researches and recommends
- Does NOT trust MRP, strikethrough prices, or star ratings as evidence
- Does NOT invent prices, reviews, offers, or sale dates — cite where each fact was found; sale dates and offers must be re-verified live at research time
- Does NOT run credit checks, verify EMI eligibility, or guarantee that any financing offer will be approved — quote the payment terms as the seller/bank lists them
- Does NOT guess a save destination — asks the user where to save first, and outputs the record in chat by default (no file, no download unless asked)
- Market focus: **India** (₹, Indian platforms, GST, Indian sale calendar), with a dedicated import layer for international purchases (see `references/import.md`). For other markets the platform map and payment layer do not apply.
- Does NOT file the claim for the user, run credit checks, or guarantee that any financing offer or warranty claim will be approved — it researches, prepares the evidence, and gives the escalation path; the user files with the brand/NCH/e-Daakhil
- Required inputs: product name or category + budget (if missing, ask 1-3 questions before proceeding)
- Works offline? No — price research requires web access (websearch, Perplexity, research APIs)

## Quality Gates (non-negotiable)

Check all before giving a Buy recommendation:
- [ ] Worthiness gate passed — the user was asked and confirmed it's worth it, never assumed
- [ ] Real price history checked — "50% off" on an inflated MRP is not a deal
- [ ] Review dates spread over time — bursts of reviews = manipulation flag
- [ ] Community check done — long-term ownership experiences found (Reddit-first), no paid-plant red flags ignored
- [ ] Compatibility & fit verified — works with what the user already owns (ports, fit, PSU, driver/OS)
- [ ] Pipeline-aware budget shown — out + queued + new total surfaced before deciding
- [ ] At least 2 independent candidates compared, not just 1
- [ ] Warranty / return policy known
- [ ] Effective price computed for any financed purchase (card offer / UPI / coins / EMI / split payment) — decision is based on effective price, not sticker
- [ ] EMI-readiness checked for financed purchases — active-EMI ledger read; committed + new monthly vs ceiling → Ready / Almost / Not ready (`references/emi.md`)
- [ ] Purchase mechanics checked for high-value buys — open-box inspection, GST invoice kept, warranty-registration deadline
- [ ] Safety check passed — no fake-seller / refurb-as-new / prepaid-to-unknown-seller red flags
- [ ] Decision written down (tracker row) before the purchase
- [ ] Unknown sellers checked for ratings before recommending
- [ ] Used/refurb candidates got the used-parts check — on-spot test plan, mining-card/stolen-device signals, warranty-transfer reality (`references/used.md`)
- [ ] Price variance checked where dynamic pricing is likely — logged-in vs incognito, app vs web, pincode
- [ ] Wait verdicts have a price alert set — Keepa / pricehistory.in / deal bot + the named sale trigger (`references/alerts.md`)
- [ ] Imports got the import-vs-local math — customs/IGST, courier vs postal, grey-import warranty (`references/import.md`)
- [ ] High-value buys have a claims path — invoice kept, warranty-registration deadline, NCH / e-Daakhil escalation (`references/claims.md`)
- [ ] Broken/repaired devices logged — repair row (cost, warranty-covered?, claim outcome) + repair-vs-replace verdict before fixing or replacing (`references/repairs.md`)
- [ ] Subscription/recurring spend surfaced when relevant — total monthly committed vs value delivered (`references/subscriptions.md`)

## Output Format

Use this exact structure for the final answer:

```
## Candidates (value score = features per rupee)
| Option | Key specs | Price | Value score | Verdict |

## Best value
[Product + why it wins on quality-per-rupee, not raw cheapness]

## Payment plan (for financed purchases)
[Cheapest pay path: cash / card / UPI / coins / EMI / split — with effective price after discounts & fees]

## Verdict
[One of: Buy now / Wait for sale / Pick alternative / Don't buy]
- Target price to wait for, AND the next India sale it lines up with (if Wait)
- Best-value alternative (if not buying)
- Who this product is for, and who should avoid it
- Purchase-mechanics + safety note for the recommended buy (open-box, invoice, warranty registration)

## Claims & next steps (for a recommended buy or wait)
- Warranty-registration deadline + how to register
- Price alert to set (Keepa / pricehistory.in / deal bot) + the sale trigger (if Wait)
- Claims path if it breaks: brand service center → NCH 1915 / consumerhelpline.gov.in → e-Daakhil
- For used: the on-spot test list. For imports: the landed-cost line

## Evidence
[Where each price/review fact was found; flag anything unverified]
```

## Core Rules

1. **Value ≠ cheap.** The cheapest option is rarely the best value. Example: an adapter reusing an old WiFi card cost ~₹2,000 but delivered old b/g/n performance; a TP-Link AX1800 card cost ~₹2,600 (+₹600) and delivered WiFi 6 + Bluetooth 5.2 + the card itself. Higher standard for the money — buy the second one.
2. **Discounts lie.** Always compare to the product's long-term/typical price, not the MRP.
3. **Reviews lie in bursts.** Spread-out dates over time = trustworthy; a cluster of 5-star reviews = manipulation flag.
4. **Store reviews tell the launch story; communities tell the ownership story.** A product with glowing ratings but a wall of "broke after 3 months" posts is not a deal at any price. Verify in communities (Reddit-first) before the verdict — see `references/community.md`.
5. **Worthiness first, always.** Never research a purchase the buyer doesn't think is worth it. Ask the question before the analysis; a "don't buy" needs no price research.
6. **Compatibility is a gate, not a footnote.** A cheap part that doesn't fit (wrong port, wrong PSU, no driver) is an expensive paperweight. Flag it before the verdict.
7. **Cite or say unverified.** No fabricated prices, ratings, or history.
8. **Decide on effective price, not sticker.** A price tag isn't the price — card discounts, UPI cashback, coins, cashback apps, reward points, and EMI fees change what you actually pay. A product over the sticker budget can become buyable at its effective price (Example 5).
9. **No-cost EMI ≠ free.** "No-cost / zero-cost EMI" still costs money: banks charge a processing fee and GST on the waived interest, and tenure may be capped (e.g. 3/6 months no-cost on SBI cards, up to 18-24 months regular). Always compute the effective price including those fees before calling it zero.
10. **Timing beats discounts.** An "80% off" outside a real sale is usually an inflated MRP. Big-ticket items (phones, laptops, TVs) hit annual lows at the Big Three — Flipkart Big Billion Days, Amazon Great Indian Festival, Diwali sales (see `references/india.md`). Tie any "Wait" verdict to the next real sale, not a random date.
11. **Queued is future spend.** `waiting`/`noted + Buy` tracker rows are not "not bought" — surface out + queued + new before deciding (informational, never block silently).
12. **Inspect before you accept.** Open-box delivery: never share the OTP before opening. Keep the GST invoice — Indian warranty claims fail without it. Note warranty-registration deadlines.
13. **Safe > cheap.** Unknown seller + prepaid = risk. Counterfeits and "refurb sold as new" are common. Never ask for or share OTPs/UPI PINs.
14. **Save where the user wants.** Ask before recording; by default output the record in chat. Only write a file (tracker note, the user's CSV, their own file) or offer a download when asked — never into the skill's own files.
15. **A deal isn't proven until it's used.** After purchase, get the satisfaction rating (HIGH/MED/LOW) and "worth it after extended use?" — it makes the next value score honest.
16. **Used ≠ new.** A used/refurb part is a separate tier with its own verification: test it on the spot, screen for mining/stolen units, and know whether the warranty transfers before paying (see `references/used.md`).
17. **Imports pay twice.** The sticker price abroad isn't the price — customs/IGST, courier-vs-postal handling, currency markup, and grey-import (no Indian warranty) reality often flip the verdict. Compute the landed cost vs the local effective price (see `references/import.md`).
18. **A wait without an alert is a leak.** If the verdict is "wait", set the price alert and tie it to a named sale — otherwise the sale passes silently (see `references/alerts.md`).
19. **The warranty is part of the deal.** Keep the invoice, register within the deadline, and know the escalation path (brand → NCH 1915 → e-Daakhil) before you need it (see `references/claims.md`).
20. **One price is not the price.** Dynamic/surveillance pricing shows different prices to different people — check logged-in vs incognito, app vs web, device and pincode variance before trusting a quote.
21. **Subscriptions renew themselves.** Recurring spend is a monthly leak that nobody re-verifies — inventory it, test each one's worthiness, and prefer annual/shared/student plans (see `references/subscriptions.md`).
22. **Repairs tell the truth about durability.** A device that needed two expensive OOP repairs is a bad rebuy, no matter the next deal. Log every repair (warranty-covered or not) and run repair-vs-replace before reflexively fixing or replacing (see `references/repairs.md`).

## Saving Results

Ask the user where to save. **Default: output the record in chat** — no file written, no download. Offer a file/download only when the user explicitly asks.

- **Chat output (default)** — give the verdict record as text in the reply, including the CSV row if the user wants the CSV format. Nothing is written or downloaded.
- **Tracker note** — if the user has a note/ledger to write to, append a row using the schema in `references/tracker.md`.
- **File / download (only on request)** — if the user says "save it" or "download", append to their chosen file/location (their vault note, their own CSV) or hand them a downloadable CSV. Provide a download only when asked.

> [!important] The skill's CSV files are read-only templates
> `assets/deal-tracker.csv`, `emi-tracker.csv`, and `repairs.csv` ship with the skill as **templates** — they show the format; they are not write targets. Never modify the skill's own files. In web/cloud agents (e.g. Claude on web) writing files may be impossible anyway — which is exactly why chat output is the default: the user always gets the record, even where no files can be written.

Dual record (works for every user, vault or not): vault users keep detail in their own notes (Deal / EMI / Repair trackers with wikilinks); non-vault users keep the same record in a CSV they keep themselves (use the `assets/` files as templates to copy). Same schema, whichever the user prefers. Each tracker row links to the note where the detail lives — the tracker indexes, it never duplicates the full research.

Wait for their choice before writing anything.

## Reference Materials

- `references/prompt.md` — the full copy-paste deal-hunter prompt (JOB 0-7: worthiness, price research, quality verification incl. community + compatibility, value scoring, payment optimization, purchase mechanics, pipeline budget, final verdict). Load when analyzing a specific shortlisted product.
- `references/community.md` — Reddit-first community verification playbook: subreddit map, long-term ownership signals, paid-plant detection. Load for every shortlisted product.
- `references/finance.md` — the Pay Smart deep dive: payment-method inventory, verifying a real no-cost EMI, split-payment mechanics, offer-stacking rules, effective-price formula. Load for any financed purchase.
- `references/emi.md` — EMI ledger & purchase readiness: active-EMI tracking (monthly outflow, tenure, remaining obligation), the user's monthly EMI ceiling, and the Ready / Almost / Not-ready verdict on any new purchase. Load for any financed purchase or any new purchase while EMIs are active.
- `references/repairs.md` — repair tracking & repair-vs-replace: repair ledger schema, how repairs feed satisfaction/claims/value scoring, and the fix-vs-replace verdict (repair cost vs remaining value vs replacement effective price). Load when a device breaks or needs a repair.
- `references/india.md` — India layer: platform map, sale calendar, purchase mechanics, payment levers, scams.
- `references/tracker.md` — suggested tracker schema, status flow, pipeline rule, watchlist, and example rows (a default format, not a mandatory destination).
- `references/used.md` — used/refurb verification playbook: on-spot testing (GPU/RAM/phone/laptop), mining-card & stolen-device signals, warranty-transfer reality, used-marketplace safety. Load for any used/refurb candidate.
- `references/claims.md` — after-sale claims & escalation: invoice retention, warranty registration, brand service path, NCH 1915 / consumerhelpline.gov.in / e-Daakhil, price protection. Load when a product breaks or arrives wrong.
- `references/import.md` — imports/global layer: customs/IGST landed-cost math, courier vs postal, currency markup, grey-import warranty reality, BIS-restricted categories, import-vs-local decision. Load for any international listing.
- `references/alerts.md` — price alerts & Watchlist re-check: Keepa / pricehistory.in / camelcamelcamel alerts, Telegram deal bots, monthly sale re-check routine, stale-item downgrade. Load for every Wait verdict.
- `references/subscriptions.md` — subscriptions & recurring-spend audit: inventory, per-subscription worthiness, annual-vs-monthly + GST math, shared/student plans, EMI audit. Load for subscription/recurring-spend questions.
- `assets/deal-tracker.csv` — blank CSV **template** (read-only; the user copies it to keep their own record). Default output is chat; give a download only when asked.
- `assets/emi-tracker.csv` and `assets/repairs.csv` — portable CSV **templates** for EMI and repair records, for users who don't keep vault notes (read-only; output in chat by default).

## Examples

> All examples are **illustrative** — sample figures for demonstration, not the author's actual purchases.

### Example 1: Buy now (flagship win)

- Input: "I need WiFi + Bluetooth for my desktop. Budget ~₹3,000."
- Steps:
  1. Define need: must-have = WiFi 6 + BT, direct-fit PCIe (no adapter)
  2. Net: TP-Link AX1800 card (~₹2,600), a T4E-class card (~₹1,900, no BT), a WE3000-class card (~₹3,500), an mPCIe adapter (~₹2,000, reuses old b/g/n card)
  3. Verify: the AX1800 card shows 4.4★/2.7K ratings, is a best-seller, MRP ~₹5,600 → 53% real vs historical pricing
  4. Score: the AX1800 card wins on features-per-rupee
- Output: **Buy now — the AX1800 card.** WiFi 6 + BT 5.2 + card included, direct-fit PCIe x1, only ~₹600 more than a low-value adapter. Logged to tracker as "bought".

### Example 2: Wait for sale

- Input: "Is ₹4,999 a good price for [headphones]?"
- Steps: Verify finds historical low of ₹3,499 reached 3x in past year; current price is typical, not low.
- Output: **Wait for sale.** Target price ₹3,799. Track it; no purchase now.

### Example 3: Don't buy

- Input: "Should I buy [gadget] for ₹6,145?"
- Steps: Verify finds equivalent spec (₹1,899) and ₹6,145 is a niche adapter with no warranty; need can be met cheaper or not at all.
- Output: **Don't buy.** The need is inflated or met better elsewhere. Log the decision.

### Example 4: Compare mode (user's own list)

- Input: "Compare these 3 headphones — Sennheiser HD 450BT ₹6,999, Sony WH-CH520 ₹4,499, JBL Tune 510BT ₹2,999. Which should I get? Must-have: long battery + Bluetooth 5."
- Steps:
  1. Lock list: 3 products confirmed
  2. Normalize specs: battery hours, BT version, ANC, weight, driver
  3. Price-check each: CH520's ₹4,499 is ~30% above its typical ₹3,500
  4. Review-check each: JBL review dates clustered (flag); Sony/Sennheiser spread out
  5. Weighted score: battery 3x, BT 2x → Sony CH520 (with price caveat) vs JBL
- Output: **Pick alternative — JBL Tune 510BT** if budget is king; **Sony CH520** if battery matters most (wait for ~₹3,500). State both and why, per must-have weights. Then ask where to save.

### Example 5: Pay Smart flips a verdict (financing layer)

- Input: "Cashify Google Pixel 8a vs Pixel 8, which should I buy? Budget under ₹30,000. Must-haves: battery, long-term updates, compact, camera. It'll be a second phone for travel."
- Sticker-price analysis (Compare mode, steps 1-5):
  - Pixel 8a ₹23,699 (₹23,099 w/ Gold) — **OUT OF STOCK** (Notify Me), updates ~2031, reviewers call camera "average"
  - Pixel 8 ₹30,799 (₹30,199 w/ Gold) — **IN STOCK**, better camera + wireless charging, updates ~2030, 4.8★/43 (95% positive)
  - Sticker verdict would be: 8a better value/rupee but unavailable → "wait for restock"
- Pay Smart (step 6) changes the answer:
  - Card-offer badges on the Pixel 8 page: **₹3,700 / ₹4,000 off on card payment** (RewardEagle confirms Cashify coupons, Aug 2026)
  - **No-cost EMI**: SBI credit card 3/6 mo; HDFC/ICICI debit card 3-6 mo; cardless EMI via Snapmint/Instacred; EMI from ₹1,757/mo
  - **Split payment**: ₹10k cash + card/EMI for the remainder
  - Effective price ≈ ₹30,799 − ₹600 (Gold) − ₹3,700 (card offer) ≈ **₹26,499-27,099** — **under the ₹30k ceiling**
- Output: **Buy now — Pixel 8** (at effective price ~₹27k with card offer + no-cost EMI). Sticker price alone said "wait"; the payment layer made it affordable today. Then ask where to save.

### Example 6: EMI readiness flips a verdict

- Input: "Am I ready to buy [phone] at ₹72,999 on 6-mo EMI (~₹12,167/mo)? My active [phone] EMI is ₹3,500/mo."
- Steps: read the EMI ledger → committed ₹3,500/mo, ceiling ₹6,000/mo → headroom ₹2,500/mo. New monthly ≈ ₹12,167/mo → committed + new ≈ ₹15,667/mo, way over the ceiling.
- Output: **Not ready.** New EMI busts the ₹6,000/mo ceiling ~2.6x. Options: wait until the current EMI closes (~6 months → full ₹6,000 headroom), pick a cheaper model whose EMI fits the ceiling, or raise the down payment. Numbers shown: ceiling ₹6,000, committed ₹3,500, new ₹12,167, shortfall ₹9,667. Then ask where to save.
