# Agent-run online income options: what survives the evidence

Prepared for Chris DeWitt, SWAE Marketing. Research date: 2026-10-05. All URLs accessed 2026-10-05.

## How to read the evidence grades

- **P (primary, fetched):** the platform page was read in full. Only one page was reachable this way (the Etsy open-api GitHub discussion). Nearly every platform host was blocked by the sandbox egress proxy.
- **S (search-snippet):** a search result from the platform's own domain stated the fact in its snippet. Reliable for wording, not for completeness.
- **T (secondary):** only a third-party page says it. Treat numbers at this grade as indicative until re-verified.
- **Tooling note:** the Semrush MCP returned `no_api_units` on the first call, so there is no Semrush search-volume data in this report. Firecrawl was not used (no credits). WebFetch was blocked on: developers.printful.com, support.google.com, submit.shutterstock.com, help.redbubble.com, blog.redbubble.com, developer.chrome.com, vecteezy.com, sec.gov, make.wordpress.org, dashboard.gelato.com, developers.beehiiv.com, help.author.envato.com, notion.com, contributor.pond5.com, authorsguild.org, searchenginejournal.com, assetstore.unity.com, vorplabs.com, weekonelabs.com. Only github.com fetched. The re-verification list at the end covers what to read once the proxy is opened.
- **Process note for Chris:** the global rule to run a skeptic agent in parallel could not be followed inside this research subagent (no Agent tool available to it). The parent session should run one against this file before anything is acted on.

## Executive summary

1. Five options survive. In order: productized services billed through SWAE; a Shopify print-on-demand store driven by the Printful, Printify or Gelato APIs plus the Shopify MCP; digital products sold from an owned storefront (Shopify Digital Downloads, Gumroad, Payhip); Etsy digital and POD via the Etsy Seller App API tier or Printify's Etsy publisher; a Beehiiv newsletter as a marketing channel for the first three rather than as a standalone product.
2. The agent can run nearly every step of the POD and digital-product loops end to end: niche research, design generation and cleanup (Adobe Express tools), mockups, listing copy, pricing, product creation, order monitoring and customer email drafts. The steps that stay manual are one-time: identity verification, bank/tax setup, store creation, and approving anything customer-facing per Chris's own rules.
3. The hard problem in every marketplace-free option is demand. Printful's own survey of 68 POD store owners says marketing was the hardest part (S). Gumroad's third-party product analysis puts the median creator at $72/month with 44% of products at $0 (T). Nothing in the evidence shows an agent-only loop generating traffic without ad spend, SEO, or an existing audience.
4. Amazon Merch on Demand is rejected: no API, manual review (2 to 8 weeks, T), 10-design starting tier (T), and a reported June 2026 royalty change that halves the base royalty on a $19.99 shirt to $2.44 unless 15%+ of sales come from external traffic (T, three sources agree, none primary).
5. Redbubble is rejected: its User Agreement prohibits uploading "using any bot, scraper, or other automated means" (S), caps uploads at 30/day (S), and charges Standard-tier accounts 50% of monthly earnings (S).
6. Amazon KDP is rejected: no API, a title cap of two new titles per format per week since 2026-09-21 (S, KDP Community), mandatory AI-generated disclosure (S), and a saturated low-content category.
7. Faceless YouTube is rejected: the July 15 2025 "inauthentic content" policy names "AI-generated content made with generic or unoriginal templates that gives the impression of mass production" as ineligible (S), uploads through unaudited API clients are locked private (T, Google dev docs), and YPP thresholds double on 2027-02-01 (T).
8. TikTok is rejected on the same grounds: AI-generated videos are ineligible for Creator Rewards (T) and unaudited API clients post private only (S, TikTok dev docs).
9. Every major stock marketplace except Freepik, Vecteezy, 123RF and Dreamstime bans AI submissions. Shutterstock: "will not allow AI-generated content to be submitted by contributors" (S). Pond5, Epidemic Sound and Envato ban it (T). Freepik pays $0.04 to $0.07 per download (T). Rejected on economics.
10. Etsy's API is usable: the Seller App tier gives "automated, near-instant approval" for an active seller's own shop (S), including createDraftListing. Commercial access is effectively unobtainable (P: repeated unexplained denials through 2026-10-01, no Etsy staff response). Etsy requires AI disclosure in the description and "Designed by a seller" classification (S).
11. Canva Creators is rejected for now: Element Creator applications closed, Template Creator in beta with a months-long wait (S), and payouts from an opaque royalty pool.
12. Micro-SaaS, Chrome extensions, Shopify apps and WordPress plugins are buildable by agents but the revenue distributions are brutal (72% of Shopify apps under $1K MRR, T; 54% of Stripe-verified Indie Hackers products at $0, T). Shopify's 0% revenue share on the first $1M (S) is the only structural advantage. Deferred, not rejected.
13. Claude API cost for the agent loop is small relative to platform fees: roughly $0.10 to $0.20 per product at Sonnet 5.5 / Opus 5.5 pricing, call it $30 to $150 per month per loop. Cloud sessions and Routines run on Chris's plan, so marginal cost may be plan usage rather than API dollars.
14. The grifter claims ("$10K/month POD with AI", "faceless YouTube passive income", "KDP low-content empire") rest on self-reported income from people selling courses or tools. No audited income data exists for any option here except Beehiiv's platform-wide $19M paid-subscription total (T) and Shopify's $2.4B app-store merchant spend (T), neither of which says anything about a new entrant.
15. Recommended 30 to 60 day test: run productized services and one Shopify POD or digital store in parallel; treat Etsy as the second channel for the same catalog once the store has a few products that sell. Kill criteria are listed per pick.

## Chris's tooling, mapped to loop steps

| Step | Tool that does it | Notes |
|---|---|---|
| Niche/trend research | WebSearch, Semrush MCP (when units exist), Shopify `run-analytics-query`, Google Trends via browser | Semrush is out of API units today |
| Design/creation | Claude Design, Adobe Express/Firefly tools (generate, background removal, vectorize, generative expand), code for templates/spreadsheets | Firefly output is Adobe-licensed; check Chris's plan terms for commercial use |
| Mockups | Printful Mockup Generator API (10 req/min established stores, 2 req/min new, S), Printify mockups, Gelato templates | |
| Listing copy, SEO | Claude | Etsy and Shopify SEO fields fillable via API |
| Pricing | Claude + platform cost APIs | |
| Upload/publish | Shopify MCP (`create-product`, `create-digital-product`, GraphQL), Printful Sync API, Printify `publish.json`, Gelato `create-from-template`, Etsy Seller App | |
| Marketing | Klaviyo MCP, Beehiiv Send API (Pro plan), HubSpot, WordPress.com content | Paid ads need Chris's card and approval |
| Customer service | Gmail connector drafts, Shopify order tools | Drafts only, per Chris's approval rule |
| Payouts/tax | Platform-handled (Shopify Payments, Gumroad MoR, Etsy Payments) | Manual: bank, W-9/1099, sales tax nexus decisions |

---

## Option by option

### 1. Print on demand on a Shopify store (Printful / Printify / Gelato APIs)

**Loop:**

| Step | Who | Reason |
|---|---|---|
| Niche/trend research | AGENT | WebSearch, Shopify analytics, marketplace scans |
| Design | AGENT | Firefly/Express + vectorize; trademark screening via USPTO search in browser |
| Mockups | AGENT | Printful Mockup Generator API, rate-limited (S) |
| Listing/pricing | AGENT | Printful Ecommerce Platform Sync API creates Shopify products from a Printful store (S); Printify `POST /v1/shops/{shop_id}/products/{product_id}/publish.json` pushes to the connected Shopify shop, 200 req/30 min (T); Gelato `POST ecommerce.gelatoapis.com/v1/stores/{storeId}/products:create-from-template` (T, apis.io + support.gelato.com) |
| Upload | AGENT | As above, plus Shopify MCP `create-product` and GraphQL for collections, metafields, SEO |
| Marketing | AGENT (organic, email), MANUAL-CHRIS (ad budget approval) | Klaviyo flows, blog content, Beehiiv; paid ads need a card and sign-off |
| Customer service | AGENT drafts, MANUAL-CHRIS approves | Gmail drafts; Printful handles reprints/returns on quality issues |
| Fulfillment | AUTOMATIC | Order sync is native to the integrations |
| Payouts/tax | MANUAL-CHRIS one-time | Shopify Payments identity, bank, tax settings |
| Store creation | MANUAL-CHRIS one-time | Shopify signup; the MCP cannot create a store from an API call (T, apievangelist) |

**Terms on automation and AI:**
- Printful: API has a general limit of 120 calls/min; Ecommerce Platform Sync API 10 req/60 s; Mockup Generator 10 req/60 s established, 2 req/60 s new stores (S, developers.printful.com snippet). "The Products API is not intended and will never support creating and managing products in external platforms such as Shopify" (S); the Sync API is the right surface. Printful's blog on AI designs says pure AI output "usually do[es] not get copyright protection" and tells sellers to avoid prompts referencing copyrighted characters or brand logos (S, printful.com/blog). No ban on AI designs found.
- Printify: API access with a personal access token needs no approval or paid plan; OAuth multi-merchant apps are reviewed in about a week (T, apitracker/podvector). Global limit 600 req/min (T). API Terms of Service exist at printify.com/api-terms (S, not read).
- Gelato: API available on the free plan (T, support.gelato.com snippet via dodropshipping).
- Shopify: API License and Terms of Use govern all API use (S, shopify.com/legal/api-terms). The terms prohibit bypassing API restrictions including "automating administrative functions of the Merchant Store Admin" (T, paraphrase). Using the Admin API as designed is the intended path, so an MCP-driven store is within terms.

**Demand and saturation:**
- POD market size estimates range from $10.8B to $12.96B for 2025 (T, research firms; wide disagreement, low confidence).
- Etsy POD profit margins "25 to 40% per item" and "one shop with around 2,000 listings brings in roughly $1,000/month" (T, mydesigns.io). Self-reported.
- Printful survey of 68 store owners: marketing was the single hardest part (S, printful.com/blog).

**Costs:**
- Shopify Basic $39/month ($29 annual); card fees 2.9% + $0.30 online (T, consistent across sources).
- Bella+Canvas 3001 at Printful: $12.25 base, $4.95 US shipping first item; one January 2026 figure gives $11.50 + $4.69 = $16.19 landed (T, podvector/stylefactory). A $24.99 shirt nets roughly $8 before card fees and before any ad spend.
- Claude API: ~$0.10 to $0.20 per product for research, copy and QA at Sonnet 5.5 ($2/$10 per MTok) or Opus 5.5 ($4/$20) pricing; a daily Routine doing trend scans and order checks is a few dollars a day. Budget $30 to $150/month.
- Ad spend: assume $300 to $1,000/month to learn anything in 60 days. No evidence supports organic-only POD traffic for a new store.

**Time to first dollar and ceiling:** First sale within 30 days only with paid traffic or an existing audience (anecdotal). Ceiling for a single-niche store with no audience: low hundreds per month for the first year (weak, self-reported ranges). Ceiling with a real brand and ad engine: unbounded but then it is an ecommerce business, not a hands-off loop.

**Risks:** trademark takedowns (Amazon and Etsy automated scanning; "one trademark infringement ... Amazon can shut you down permanently", T); Shopify Payments reserves if dispute rate climbs (Stripe-style threshold ~0.5 to 0.75%, T); chargebacks on physical goods are low relative to digital; AI-art copyright is unprotectable in the US, so designs can be copied freely (S, printful.com citing the Copyright Office).

**Grifter check:** The pitch is "AI designs + POD = passive income." The evidence says designs are the cheap part, traffic is the expensive part, and the platform's own survey says so. Every "$10K/month" claim found was from a tool vendor or course seller.

### 2. Amazon Merch on Demand (no API; Chris uploads)

**Loop:**

| Step | Who | Reason |
|---|---|---|
| Research, design, copy, pricing, trademark pre-check | AGENT | |
| Application | MANUAL-CHRIS | Invitation/approval model, manual review 2 to 8 weeks (T); 2026 reviewers reportedly check for "low-effort AI artifacts" and expect portfolio/social links (T, single source) |
| Upload | MANUAL-CHRIS | No API. Chrome extensions exist (MerchAuto, Merch Titans, MerchGhost) but Amazon's own policy on them could not be fetched; Merch Informer's own ToS bans automated access (T). Playwright uploads are a ban risk until the Merch content policy is read |
| Tier gating | IMPOSSIBLE to bypass | Tier 10 = 10 live designs; 1 to 2 uploads/day at low tiers (T) |
| Marketing | AGENT (external traffic) | Now matters for royalty tier (below) |
| Payouts/tax | MANUAL-CHRIS one-time | |

**Terms:** Amazon publishes no separate AI rule; AI designs pass the same IP, content and metadata checks (T, two sources). Amazon "reserves the right to refuse service, terminate accounts ... at Amazon's sole discretion" (T, quoted from Amazon customer service page via search).

**Demand/royalty:** Reported June 1 2026 change to a three-tier royalty: Creator tier (default, <15% external traffic) $2.44 on a $19.99 tee, Plus (15 to 34% external, 10+ monthly sales) $4.88, Premium (35%+ external) $5.27 (T; merchtitans, mydesigns, amzprep agree; none primary). Approval rate "30 to 40%" (T, merchtitans; weak).

**Costs:** Free to join. Agent cost as above.

**Time/ceiling:** Weeks to months just to get in; tier progression needs sales. Ceiling at Tier 10 to 25 with Creator-tier royalties is tens of dollars a month (anecdotal).

**Risks:** manual gatekeeping at entry, tier caps, royalty cut, strict IP enforcement, ban for automation.

**Grifter check:** The "Merch empire" content is largely from tool sellers (Merch Titans, Merch Informer) whose products are upload bots and research tools. The June 2026 royalty change, if accurate, guts the passive case: you now need to drive your own traffic to earn what the old flat rate paid.

**Verdict: rejected.** Too much of the loop is manual or gated, and the economics worsened in 2026.

### 3. Redbubble (no API; Chris uploads)

**Loop:** research/design/copy AGENT; upload MANUAL-CHRIS; tier assignment IMPOSSIBLE to control directly.

**Terms:** Users may not upload "using any bot, scraper, or other automated means for any purpose without written permission"; 30 works per day across all accounts; violations lead to accounts being "immediately and permanently disabled" (S, help.redbubble.com / redbubble.com/agreement). AI art is allowed; mass-uploading unedited AI art "can trigger spam filters" and demotion to Standard tier (T).

**Fees:** Standard tier pays 50% of monthly earnings as a platform fee, Premium 20%, Pro 0%; fee capped at $150 per payment period for Standard/Premium (S, help.redbubble.com, 2025-08 blog). Tier criteria page not readable; third parties say it is based on sales history and account quality.

**Verdict: rejected.** Automation is explicitly banned, half of earnings go to fees at the tier a new account lands in, and the upload cap makes volume impossible.

### 4. Etsy (digital downloads and POD)

**Loop:**

| Step | Who | Reason |
|---|---|---|
| Shop open, ID, bank | MANUAL-CHRIS one-time | Persona photo ID + selfie, Plaid bank link, $15 to $29 setup fee (S, etsy.com seller handbook "Strengthening New-Shop Onboarding") |
| Research/design/copy | AGENT | |
| Listing | AGENT | Seller App tier: "automated, near-instant approval ... for active sellers in good standing," own shop only, no commercial use (S, help.etsy.com). `createDraftListing` needs quantity, title, description, price, who_made, when_made, taxonomy_id, image_ids (S, developers.etsy.com). For POD, Printify's Etsy integration publishes listings using Printify's own OAuth app, so no Etsy API key is needed at all (T) |
| Commercial API access | IMPOSSIBLE in practice | GitHub discussion #1699 (P): applicant denied repeatedly from 2026-08-21 through 2026-10-01 with "generic" reasons, support gave "AI canned responses," no Etsy staff replied. Not needed for a single own shop |
| Marketing | AGENT (Etsy SEO, email) | Etsy brings the buyers; Offsite Ads are automatic |
| Customer service | AGENT drafts | Etsy Messages has no agent-friendly API at Seller tier; browser needed |
| Payouts/tax | MANUAL one-time | Etsy Payments |

**Terms on AI:** Etsy's Creativity Standards allow "seller-prompted AI creations ... generated using AI tools ... based on a seller's original prompts" and require sellers to "disclose within their listing description if an item is created with the use of AI" (S, etsy.com/legal/creativity and seller handbook). AI items are listed under "Designed by a seller," never "Made by." AI prompt bundles are prohibited (S). A June 2025 change narrowed "Made by" to the seller's own original design, no templates (T). Third parties report January 14 2026 enforcement start with "approximately 12,000 listings removed and 8,500 warnings in Q1 2026" (T, single-source, unverified; treat as rumor until Etsy publishes it).

**Demand:** Etsy FY2025 10-K: 86.5M active buyers, 5.6M active sellers, 237M active listings (S/T via investors.etsy.com and sec.gov snippets; the 10-K could not be fetched). Digital downloads cited as fastest-growing category, 25 to 30% YoY (T, two aggregator sites; weak).

**Fees:** $0.20 listing, 6.5% transaction, 3% + $0.25 processing, Offsite Ads 15% (optional under $10K/yr) or 12% (mandatory over) (T, consistent). Combined 10 to 11% without Offsite Ads, 24 to 26% on attributed sales.

**Time/ceiling:** Etsy supplies traffic, so first sales inside 30 to 60 days are plausible for well-targeted digital listings (anecdotal). Average "successful" seller $43K to $46K/year is a survivorship number from third parties (T, weak).

**Risks:** suspension for missing AI disclosure or Creativity Standards violations; setup fee and ID verification tie the shop to Chris personally; the Seller App tier can be revoked; IP takedowns remove listings "immediately with no warning" (T).

**Grifter check:** "Etsy digital products with AI, 100 listings in a weekend" is the pitch. The reality is a disclosure regime that is actively enforced, a 24 to 26% fee stack when Offsite Ads fire, and a marketplace of 237M listings. Volume uploads of unedited AI output are exactly what the standards target.

**Verdict: survives as a second channel**, not a first. Build the catalog on the owned store, then publish the best sellers to Etsy with proper disclosure.

### 5. Digital products on an owned storefront (Shopify Digital Downloads, Gumroad, Payhip, Lemon Squeezy, Whop)

Covers templates, Notion templates, printables, spreadsheets, planners, Lightroom presets (XMP files), icon sets, fonts.

**Loop:** research, creation, listing, pricing, upload, email marketing, support drafts: AGENT. Store/account creation, KYC, tax: MANUAL-CHRIS one-time. Paid promotion: MANUAL approval.

**Platform facts:**
- Shopify Digital Downloads: free, Shopify-built, 5 GB per file, no bandwidth limit (T, apps.shopify.com via review sites). The Shopify MCP has `create-digital-product`, `upload-digital-product-file`, `publish-digital-product`, so the whole publish step is one tool chain.
- Gumroad: 10% + $0.50 per sale, 30% on Discover sales; merchant of record since 2025-01-01 (T, consistent). Prohibits selling "AI services ... access to AI tools, chatbots, image or content generation services" but not AI-made products (S, gumroad.com/prohibited).
- Payhip: free plan 5% + processor fees; $29 plan 2%; $99 plan 0% (T).
- Lemon Squeezy: 5% + $0.50 MoR; signups waitlist/invite-gated since mid-2026, Stripe pushing new growth to Stripe Managed Payments at 6.4% + $0.30 (T). Not a platform to build on now.
- Whop: 2.7% + $0.30 + $0.10; 3% platform fee only on access-app products; KYC required before cash-out (S, docs.whop.com / whop.com/seller-terms). No AI policy found.
- Notion Marketplace: 8% + $0.40 per transaction, biweekly payouts, 14-day hold (S, notion.com/help).
- Creative Market: AI products allowed with disclosure label (T); shop application curated, 3 to 7 business days (S, support.creativemarket.com).
- Fonts: MyFonts and Fontspring require foundry application and human review; 50% royalty; no AI rule found but "auto-traced-looking curves can get rejected" (T). Agent-made fonts are a quality gamble.

**Demand:** Gumroad third-party analysis of 146,271 products: median creator $72/month, fewer than 5% over $1,000/month, 44% of products at $0, top 1% capture most revenue (T, InsightRaider; methodology is scraping plus self-reports). Notion templates: "realistic earnings run from $0 to about $3,000 a month" (T). Digital goods have the highest dispute and refund rates; Stripe accounts in "digital info products" are being shut at "high levels" (T, one CPA blog; weak).

**Costs:** Shopify Basic $39/month or Gumroad at $0 fixed. Agent cost $30 to $100/month. Ad spend optional but, again, there is no organic traffic for a new store.

**Time/ceiling:** First dollar depends entirely on a traffic source. With SWAE's existing audience (clients, newsletter, site) a B2B template product could sell in weeks (anecdotal). Ceiling: the Gumroad median says most products never pass $100/month.

**Risks:** chargebacks and friendly fraud on digital goods; Stripe/Shopify Payments reserves; AI-generated files are uncopyrightable and get copied; marketplace (Discover) fees of 30%.

**Grifter check:** "Sell Notion templates / Canva templates / printables with AI, $5K/month" is the dominant pitch on YouTube and Medium. The one large dataset found (Gumroad) shows a $72/month median. The success stories cited ($500K from one Notion template) are real but are outliers with audiences.

**Verdict: survives**, conditional on a traffic source. The strongest version is B2B products aimed at SWAE's own client base and local-business niche (SEO checklists, GBP post calendars, review-response scripts, website care documentation), where Chris already has distribution.

### 6. Amazon KDP (no API)

**Loop:** manuscript/interior/cover AGENT; upload MANUAL-CHRIS (no API; automation tools exist but KDP terms could not be read); marketing AGENT/Amazon Ads MANUAL.

**Terms:** KDP requires disclosure of AI-generated content ("text, images, or translations created by an AI-based tool, even if you applied substantial edits afterwards"); AI-assisted content (AI used to "edit, refine, error-check, or improve" human-created content, or to brainstorm) needs no disclosure (S, kdp.amazon.com Content Guidelines). Title cap: two new titles per book format per week from 2026-09-21, reset Sundays 00:00 UTC (S, kdpcommunity.com "Update on KDP Title Creation Limits"; previously 10/week from October 2025 and 3/day from September 2023, T). Low-content books: notebooks, journals, undated planners; not eligible for free ISBN or series (S, kdp.amazon.com).

**Royalties:** eBook 70% at $2.99 to $12.99 (ceiling raised 2026-07-07, T) else 35%; paperback 60% at $9.99+ and 50% at $9.98 and below since 2025-06-10, minus print cost (S/T, kdp.amazon.com Paperback Royalty page in results; figures from third parties).

**Verdict: rejected.** Manual upload, 2/week throttle, disclosure flag, and a low-content category that Amazon has been throttling since 2023. Non-fiction written by agents is possible but competes with the same flood.

### 7. Canva Creators

**Status:** Element Creator applications closed as of 2025; Template Creator "currently in BETA and taking early applications," portfolio required, "up to a couple of months" for an answer (S, canva.com/help). Payment is a share of a monthly royalty pool weighted by Pro template exports, $10 threshold (S/T). An invite-only tier with 15 to 25% revenue share was reported for Q1 2025 (T, single source).

**Verdict: rejected for the 60-day window.** Application is manual and slow, and the payout is opaque. Worth applying as a background task; costs nothing.

### 8. Micro-SaaS, Chrome extensions, Shopify apps, WordPress plugins

**Loop:** build, test, listing copy, docs: AGENT. Store accounts, developer fees, review submissions, support escalation: MANUAL-CHRIS. Review: human reviewers (Shopify 2 to 6 weeks, T; WordPress.org first review under one week with queue near zero as of June 2026, T, make.wordpress.org snippet; Chrome Web Store review variable).

**Terms:** Chrome Web Store spam policy bans "multiple extensions that provide duplicate experiences or functionality" (S). Shopify: 0% revenue share on first $1M annual gross app revenue from 2025-01-01, 15% above (S, shopify.dev). Shopify shipped an AI self-review tool 2026-04-20 (T). WordPress.org has no AI-plugin policy; 17.4% of 2026 additions are AI-related (T).

**Demand:** Shopify App Store $2.4B merchant spend 2025 (T); 72% of apps under $1K MRR, median $2,400/year (T, weekonelabs/gapquery). Indie SaaS: 54% of Stripe-verified Indie Hackers products at $0; 2% over $100K MRR (T). Chrome extensions: productivity median $500/month, AI tools median $1,200/month (T, chromegoldmine; unsourced).

**Costs:** Chrome $5 one-time; Apple $99/year; Google Play $25 plus 12-tester 14-day closed test for personal accounts created after 2023-11-13 (S, support.google.com Play Console); hosting; support time.

**Verdict: deferred.** Agents can build these, and Chris already ships WordPress plugins, but the revenue distribution says most earn nothing and support is a human job. The Shopify 0% share is the one reason to revisit after the first two picks are running.

### 9. Mobile/web apps with ads

AdMob eCPM: Tier-1 banners $0.50 to $1.50, interstitials $5 to $8, rewarded video $15 to $30 (T, revenuelab/playwire). 10,000 DAU on a US-heavy mix "roughly $600 to $1,100 a day" (T) but getting 10,000 DAU is the whole business. Google Play policy bans repetitive apps and requires in-app reporting for AI-generating apps (S, support.google.com). **Rejected:** acquisition cost, store gating, and ad-only revenue requires scale no agent loop produces.

### 10. Paid newsletter (Beehiiv)

**Loop:** research, writing, scheduling: AGENT via Send API (`POST /v2/publications/:id/posts`, "available to publications on the Pro and Enterprise plans," `status: "confirmed"` required from 2026-08-06, S, beehiiv.com/support and developers.beehiiv.com). Growth: Boosts (20% of GMV to beehiiv, T), ads, cross-promo: partly AGENT. Paid subs: 0% beehiiv fee, Stripe 2.9% + $0.30 (T).

**Plan naming conflict:** search snippets variously name Launch/Scale/Max/Enterprise ($43 and $109/month annual) and Pro/Enterprise for API posting. Re-verify which tier unlocks post creation via API before budgeting.

**Demand:** Ad Network needs 1,000+ confirmed subscribers and a publishing history (T). beehiiv reports $19M paid-subscription revenue across all creators in 2025, up from $8M (T, reported from beehiiv). No per-creator distribution.

**Verdict: survives only as a channel.** A newsletter aimed at Montana/local-business owners or SWAE's niche feeds picks 1, 3 and 5. As a standalone product it needs an audience first.

### 11. Faceless YouTube / TikTok automation

**YouTube terms:** "As of July 15, 2025, YouTube updated its 'repetitious content' policy to better clarify that it includes content that is repetitive or mass-produced, and renamed this policy to 'inauthentic content.'" Violations include "AI-generated content made with generic or unoriginal templates that gives the impression of mass production, without adding the creator's original, authentic insights or perspective" (S, support.google.com/youtube/answer/1311392). Reused content and reaction videos unaffected (T). Enforcement: January 2026 wave terminated 16 channels with 35M combined subscribers (T, several outlets).

**API:** videos uploaded via an unverified API client are locked private; an API Compliance Audit is required for more than default quota; upload quota moved to a dedicated bucket of 100 calls/day on 2026-06-01 (T, developers.google.com snippet). YPP: 1,000 subs + 4,000 watch hours or 10M Shorts views in 90 days; doubling on 2027-02-01 (T).

**TikTok:** Creator Rewards excludes fully AI-generated videos (T); Content Posting API: "All content posted by unaudited clients will be restricted to private viewing mode" (S, developers.tiktok.com). RPM claims ($10 to $25 finance niche) are from faceless-channel tool vendors (T, weak).

**Verdict: rejected.** The policy was written against this exact loop, the publishing API is gated behind a human audit, and the threshold to earn anything is a year of audience building.

### 12. Stock media (non-Adobe)

- Shutterstock: "will not allow AI-generated content to be submitted by contributors" (S, submit.shutterstock.com).
- Pond5: prohibits all AI-generated content, escalating to termination (T). Epidemic Sound: no AI submissions (T). Envato Market/Elements: "does not allow authors to publish or submit AI-generated content" as standalone or primary component (T quoting help.author.envato.com).
- Freepik: accepts AI with mandatory labeling; first batch 150 to 200 files; $0.04 to $0.07 per download (T). Vecteezy: accepts AI with "AI-Generated?" checkbox and program dropdown; photos must look real; near-duplicates rejected (S, vecteezy.com/blog). 123RF and Dreamstime accept with labeling (T). Wirestock distributes AI to several and takes 15% (T).

**Verdict: rejected.** Where AI is allowed, pay is cents per download and the agent would be competing with people uploading 13,000 images (T, Medium).

### 13. Unity Asset Store / Fab

Unity: AI-aided submissions allowed; must disclose tools and modifications in the "AI description" field; purely AI images cannot be the main marketing images; rejections for anatomical errors, resemblance to third-party work (S, assetstore.unity.com). Fab: mandatory "Created with AI" flag; pure prompt-generated assets reportedly banned, hybrid allowed with disclosure; 88/12 split (T, strayspark/3dvf). **Rejected:** usable game assets (rigged models, materials, tested code) are beyond what the available tooling produces without a human artist.

### 14. Productized services sold through SWAE (agents do the work, SWAE bills)

**Loop:**

| Step | Who | Reason |
|---|---|---|
| Service design and pricing | AGENT drafts, MANUAL-CHRIS decides | |
| Lead gen | AGENT (HubSpot, Semrush prospecting, email drafts) | Outreach sent only after approval |
| Proposal | AGENT drafts via SWAE Dashboard proposal tools | Chris approves |
| Delivery (content, GBP posts, review responses, site care reports, schema, local pages, monthly SEO reports) | AGENT | WordPress.com MCP, HubSpot, Klaviyo, Semrush, Adobe tools, dashboard tasks |
| Client-facing posting | MANUAL-CHRIS approval, working hours only | Chris's standing rule |
| Billing | SWAE Dashboard invoices, existing processor | Already in place |
| Tax | Already handled by SWAE | |

**Terms:** none. No platform, no AI disclosure regime, no tiering. Client contracts are SWAE's.

**Demand and pricing:**
- Promethean Research 2025 Digital Agency Industry Report: 36% of agencies bill $175 to $199/hr, 32% $200 to $249/hr; 28% raised prices 2024 to 2025; average net margin 13%; retainer-heavy agencies report ~8 points more margin than project-based (T, but from an industry survey rather than a creator claim; strongest demand evidence in this report).
- Local SEO retainers: most common tier $500 to $1,000/month (T, swydo). GBP management: $125 to $400/month per profile (T, merchynt and others). Website care plans $100 to $250/month (T).
- The same report notes "clients increasingly expect cheaper services due to AI advancements," which is the risk and the opportunity: margins on agent-delivered work can stay high if pricing moves to outcomes rather than hours.

**Costs:** Claude usage for delivery (Opus for client-facing review, Sonnet for drafts), already-paid connectors, Chris's review time. No platform fees.

**Time/ceiling:** First dollar is as fast as the first existing client who adds a package: days. Ceiling is bounded by how many clients SWAE can sign and how much review Chris's rule requires. Evidence quality for pricing: strong relative to everything else here.

**Risks:** quality failures reach real clients; Chris's approval rule caps throughput; AI-produced copy must pass the de-AI rules; scope creep.

**Grifter check:** "AI automation agency" is itself a grift category (sell a course on selling AI agencies). The difference here is SWAE already is an agency with clients, a dashboard, and billing. The claim being made is narrow: existing services get cheaper to deliver, and new recurring packages (GBP posting, review responses, monthly content, site monitoring reports) can be delivered mostly by agents at market prices.

---

## Ranking and picks

### Pick 1: Productized recurring services through SWAE

**Verdict.** This is the only option where demand is proven, pricing is benchmarked by an industry survey, distribution exists (current clients, dashboard, proposals), and no platform can revoke access or change royalties. The agent does the delivery; Chris does the approving. It is also the least "passive," because every client-visible artifact needs his sign-off, so the design goal is packages whose deliverables batch cleanly into one weekly review.

**Minimum viable agent loop.** A weekly Routine per client: pull Semrush/GSC/GA data, draft the month's GBP posts and review responses, draft two local-SEO blog posts via WordPress.com MCP as drafts, run a monitored-site check, assemble a one-page report, and queue everything as dashboard task comments for Chris's working-hours approval. Billing via existing invoices.

**Manual steps Chris cannot avoid.** Approve pricing and packages; approve every client-facing post; sign new clients; handle escalations.

**Falsifiers in 30 to 60 days.** Fewer than two existing clients take an add-on package at $250 to $500/month; Chris's review time per client per month exceeds two hours (then the "agents do the work" claim fails on his time, not the agent's); a client rejects a deliverable for reading as AI.

### Pick 2: Shopify POD store (Printful or Printify API + Shopify MCP), one niche

**Verdict.** The most automatable physical-product loop available. Every step from research to publish has an API or MCP tool, fulfillment is automatic, and no platform tier gates it. The weakness is that nothing brings buyers; the store needs either ad spend or an SEO/content engine the agents build over months. Margins of roughly $8 on a $25 shirt (T) leave little room for paid traffic, so the niche must be one where organic or email reaches buyers.

**Minimum viable agent loop.** Weekly Routine: scan trends in one niche (WebSearch, Etsy/Amazon bestseller pages in browser), generate 5 to 10 designs with Firefly/Express, vectorize and trademark-screen, generate mockups via Printful, create products via Printful Sync API or Printify publish, set collections/SEO via Shopify MCP, publish a blog post via Shopify, send a Klaviyo campaign to any list, pull `run-analytics-query` and prune non-sellers monthly. Order emails drafted in Gmail for approval.

**Manual steps.** Shopify signup and Shopify Payments identity; connect Printful/Printify; approve ad budget; sales tax decisions; respond to IP complaints.

**Falsifiers.** Zero orders in 60 days with at least 40 products live and $300+ of ad or email reach; an IP complaint on any design (process failure); cost per acquisition above gross margin after 30 days of ads.

### Pick 3: Digital products from an owned storefront, B2B-leaning

**Verdict.** Fully agent-producible (templates, spreadsheets, checklists, XMP presets, Notion templates) and fully agent-publishable through Shopify Digital Downloads or Gumroad. The Gumroad median of $72/month (T) is the honest baseline for a product with no audience. The version that beats the baseline uses SWAE's existing reach: products for local-business owners and small agencies, promoted through the newsletter (pick 5) and the SWAE site.

**Minimum viable agent loop.** Monthly: pick a product from a backlog, build it, QA it, write the listing and a landing page, publish via `create-digital-product`, add to Klaviyo flows, publish a supporting WordPress post, report sales.

**Manual steps.** Storefront account/KYC; refund policy decisions; approve copy.

**Falsifiers.** Fewer than 10 sales total across three products in 60 days; refund/dispute rate above 1%; products copied and undercut within weeks (expected for uncopyrightable AI output; a signal to move toward products with a service component).

### Pick 4: Etsy as a second channel for picks 2 and 3

**Verdict.** Etsy supplies the buyers the owned store lacks, and the Seller App API tier (or Printify's Etsy publisher) makes listing automatable. The cost is ID verification tied to Chris, a 10 to 26% fee stack, and a disclosure regime that is enforced. Only list AI-made items as "Designed by a seller" with the disclosure sentence in every description.

**Minimum viable agent loop.** After pick 2 or 3 has products with any sales signal: register a Seller App, mirror the top products as Etsy listings with AI disclosure, sync via Printify for POD, monitor Etsy stats weekly through the API.

**Manual steps.** Shop open, Persona ID, Plaid bank, setup fee; production partner disclosure; responding to any Creativity Standards notice.

**Falsifiers.** A Creativity Standards warning or listing removal in the first 30 days; Etsy fees plus Offsite Ads pushing net margin below zero on POD items; no Etsy sales after 60 days with 30+ listings.

### Pick 5 (channel, not product): Beehiiv newsletter

Run only in service of picks 1, 3 and 4. Confirm which plan unlocks the Send API before paying. Kill if it cannot reach 300 confirmed subscribers in 60 days from SWAE's existing contacts and site.

---

## Rejected options, one line each

- **Amazon Merch on Demand:** no API, manual gated entry, 10-design start, reported June 2026 royalty halving without external traffic.
- **Redbubble:** automated uploads banned by User Agreement; 50% fee at Standard tier; 30/day cap.
- **Amazon KDP:** no API; two titles per format per week; AI disclosure flag; low-content saturated.
- **Canva Creators:** Element applications closed; Template beta with months-long wait; opaque royalty pool. Apply anyway as a free background task.
- **Faceless YouTube:** the inauthentic-content policy targets templated AI output; API uploads private until human audit; 2027 threshold doubling.
- **TikTok:** AI-generated video excluded from Creator Rewards; API posts private until audit.
- **Stock media (Shutterstock, Pond5, Epidemic, Envato):** AI submissions banned.
- **Stock media (Freepik, Vecteezy, 123RF, Dreamstime):** allowed, but cents per download.
- **Unity Asset Store / Fab:** disclosure regimes plus pure-AI ban on Fab; assets need a human artist.
- **Mobile apps with ads:** store gating (12 testers, $99), eCPMs that need 10K+ DAU.
- **Micro-SaaS / Chrome extensions / Shopify apps / WordPress plugins:** buildable, but 54 to 72% earn nothing; support is human work. Deferred, revisit for Shopify's 0% share after picks 1 and 2 run.
- **Lemon Squeezy:** waitlist-gated and in maintenance mode under Stripe.
- **Whop:** fine as a checkout, no demand advantage; KYC before payout.
- **Fonts on MyFonts/Fontspring:** human foundry review; auto-traced curves rejected.
- **Lightroom presets, Notion templates as standalone:** folded into pick 3; not separate businesses.

## Claude API cost model for the loops

Pricing from the claude-api skill (cached 2026-09-25): Opus 5.5 $4/$20 per MTok, Sonnet 5.5 $2/$10, Haiku 4.5 $1/$5. Per product (research 10K in, design brief and QA 10K in, listing copy 3K out, review 2K out) on Sonnet: ~$0.09; on Opus: ~$0.18. A daily Routine doing a trend scan, analytics pull and order check: ~$0.50 to $3 per run. Monthly per loop: $30 to $150 at API rates. Cloud sessions run on Chris's plan, so the practical cost is plan usage; the API figure is the ceiling. Image generation through the Adobe connector is billed by Adobe credits, not Anthropic; check the plan's generative credit allowance before scaling designs.

## Primary-source URLs to re-verify once network access is widened

Platform terms (highest priority):
- https://support.google.com/youtube/answer/1311392 (YouTube monetization policies, inauthentic content wording)
- https://www.etsy.com/legal/creativity (Creativity Standards) and https://www.etsy.com/seller-handbook/article/1275449912004 (Etsy's stance on AI)
- https://help.etsy.com/hc/en-us/articles/41918478450967-How-to-Register-a-Seller-App-with-Etsy-s-API (Seller App tier)
- https://www.etsy.com/seller-handbook/article/1241780194948 (new-shop onboarding, Persona, setup fee)
- https://kdp.amazon.com/en_US/help/topic/G200672390 (KDP content guidelines, AI definitions)
- https://www.kdpcommunity.com/s/article/KDP-Title-Creation-Limits-Update (2 titles/format/week)
- https://kdp.amazon.com/en_US/help/topic/GGE5T76TWKA85DJM (low-content books)
- https://www.redbubble.com/agreement and https://help.redbubble.com/hc/en-us/articles/50959863016724 (automation ban; tier fees)
- https://blog.redbubble.com/2025/08/artist-account-tiers-and-fees/
- https://merch.amazon.com (content policy and services agreement; also the June 2026 royalty announcement, which was only seen second-hand)
- https://submit.shutterstock.com/help/en/articles/10594622-content-policy-updates-ai-generated-content
- https://www.vecteezy.com/blog/contributor/ai-images-contributors
- https://help.author.envato.com/hc/en-us/articles/13313674070681-AI-generated-content-policy-for-Market-and-Elements
- https://contributor.pond5.com/faq/
- https://assetstore.unity.com/publishing/submission-guidelines and https://dev.epicgames.com/documentation/fab/publisher-get-started-in-fab
- https://developer.chrome.com/docs/webstore/program-policies/policies
- https://shopify.dev/docs/apps/launch/distribution/revenue-share and https://www.shopify.com/legal/api-terms
- https://gumroad.com/prohibited and https://gumroad.com/terms
- https://whop.com/seller-terms/
- https://www.notion.com/help/selling-on-marketplace
- https://www.canva.com/help/canva-creators-program/ and https://www.canva.com/creators/templates/
- https://support.creativemarket.com/hc/en-us/articles/201251700-Open-a-Shop-on-Creative-Market

APIs and pricing:
- https://developers.printful.com/docs/ (Sync API, Mockup Generator limits) and https://www.printful.com/api
- https://printify.com/api-terms/ and https://developers.printify.com/ (publish endpoint, rate limits)
- https://dashboard.gelato.com/docs/ecommerce/products/create-from-template/
- https://developers.beehiiv.com/api-reference/posts/create and https://www.beehiiv.com/support/article/36759164012439-using-the-send-api-and-create-post-endpoint (which plan unlocks it)
- https://developers.google.com/youtube/v3/guides/quota_and_compliance_audits and https://developers.google.com/youtube/v3/revision_history
- https://developers.tiktok.com/doc/content-posting-api-reference-direct-post
- https://support.google.com/googleplay/android-developer/answer/14151465 (12-tester rule)

Demand data:
- https://www.sec.gov/Archives/edgar/data/1370637/000137063726000019/etsy-20251231.htm (Etsy FY2025 10-K: buyers, sellers, listings, GMS)
- https://prometheanresearch.com/wp-content/uploads/2025/05/2025-Promethean-Research-Digital-Agency-Industry-Report-V1.02.pdf
- https://make.wordpress.org/plugins/2026/01/07/a-year-in-the-plugins-team-2025/
- https://insightraider.com/en/data/gumroad-statistics-2026 (methodology check on the $72/month median)
- https://weekonelabs.com/blog/shopify-app-revenue-benchmarks-2026/ (methodology check on 72% under $1K MRR)

Fetched and read in full this session (primary): https://github.com/etsy/open-api/discussions/1699

## Sources consulted by search (secondary and snippet)

Listed so the parent session can spot-check. Dates accessed 2026-10-05.
- POD: printful.com/blog (statistics, AI copyright, mistakes), printify.com/blog, podvector.ai, stylefactoryproductions.com, mydesigns.io, dodropshipping.com, support.gelato.com, apis.io
- Etsy: vorplabs.com/agent-tools/etsy-api, help.erank.com, indiesellersguild.org, craftybase.com, closo.co, listadum.com, growtsy.com, pixpipe.app, ngini.com, businessofapps.com
- Merch/KDP/Redbubble: merchtitans.com, mydesigns.io, amzprep.com, bebolddigital.com, merchbanao.com, publishersweekly.com, janefriedman.com, authorsguild.org, publishflow.ai, kdptools.io, michielschuer.medium.com, lavaritte.com
- Digital products: theleap.co, swell.is, dodopayments.com, userjot.com, ruzuku.com, drry.com, latuos.com, eden.so, checkoutpage.com, insightraider.com, designrevision.com, itechguides.com
- Video/newsletter: searchenginejournal.com, musically.com, socialmediatoday.com, outlierkit.com, techtimes.com, vidiq.com, air.io, ppc.land, blotato.com, vorplabs.com, storrito.com, emailtooltester.com, sacra.com, outrank.so, mrktcorrect.com
- Stock/assets: dynamoi.com, lastplaydistro.com, rastock.ai, autokeyworder.com, xpiksapp.com, jamoimages.com, strayspark.studio, 3dvf.com, blog.promise.legal
- Software/apps: weekonelabs.com, gapquery.com, shopthemedetector.com, eseospace.com, harshrastogi.tech, therepository.email, caseyrb.com, palant.info, bleepingcomputer.com, extensionpay.com, chromegoldmine.com, konabayev.com, boringriches.com, techstartups.com, revenuelab.fyi, playwire.com, testerscommunity.com
- Services: swydo.com, prometheanresearch.com, agiled.app, merchynt.com, claremontsoftware.com
- Payments risk: chargeflow.io, jamesbakercpa.com, chargebacks911.com
