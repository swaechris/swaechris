# Agent-run online income options: what survives the evidence

Prepared for Chris DeWitt, SWAE Marketing. Research date: 2026-10-05. All URLs accessed 2026-10-05.

## How to read the evidence grades

- **P (primary, fetched):** the platform's own page was fetched in full (via curl through the session proxy after WebFetch stayed blocked) and the quoted text was read from it. Fetched text is saved in the session scratchpad under `pages/`.
- **S (search-snippet):** a search result from the platform's own domain stated the fact in its snippet, and the page itself returned 403 to every fetch. Reliable for wording, not for completeness.
- **T (secondary):** only a third-party page says it. Numbers at this grade are indicative until re-verified.
- **Still unreadable after network was widened (403 to curl and WebFetch):** www.etsy.com/legal/* and seller-handbook, help.etsy.com, help.redbubble.com, redbubble.com/agreement, blog.redbubble.com, canva.com help, canvacreatorsupport.zendesk.com, help.author.envato.com, support.creativemarket.com, payhip.com, freepik.com/support.freepik.com, fontspring.com and foundrysupport.monotype.com. merch.amazon.com resource pages return 200 with an empty body (login wall). These stay at S or T and are listed for manual browser verification at the end.
- **Tooling note:** the Semrush MCP returned `no_api_units` on the first call, so there is no Semrush search-volume data here. Firecrawl was not used.
- **Process note for Chris:** the global rule to run a skeptic agent in parallel could not be followed inside this research subagent (no Agent tool available to it). The parent session ran one; its two flags (Etsy publish flow, Printify earnings table) were checked against the primary pages and are incorporated below.

## Executive summary

1. Five options survive. In order: productized services billed through SWAE; a Shopify print-on-demand store driven by the Printful, Printify or Gelato APIs plus the Shopify MCP; digital products sold from an owned storefront (Shopify Digital Downloads, Gumroad); Etsy digital and POD through the Etsy Seller App API tier or Printify's Etsy publisher; a Beehiiv newsletter as a marketing channel for the first three rather than a product in itself.
2. The agent can run nearly every step of the POD and digital-product loops: niche research, design generation and cleanup (Adobe Express tools), mockups, listing copy, pricing, product creation, order monitoring and customer-email drafts. What stays manual is one-time: identity verification, bank and tax setup, store creation, and approving anything customer-facing per Chris's own rules.
3. Demand is the hard part in every owned-store option. Printful's survey of 68 POD store owners: "most customers said it was marketing" (P). Printify's own table: new sellers at 0 to 6 months make "$0 to $100+" net per month and the average seller takes 165 days to reach the first $1,000 in revenue (P). A third-party scrape of 146,271 Gumroad products puts the median creator at $72/month with 44% of products at $0 (T).
4. Amazon Merch on Demand is rejected: no API, manual review, 10-design starting tier (T), and a reported June 1 2026 royalty change that halves the base royalty on a $19.99 shirt to $2.44 unless 15%+ of US sales come from non-organic traffic (T; three sources agree, Amazon's own page is behind a login).
5. Redbubble is rejected: its User Agreement prohibits uploading "using any bot, scraper, or other automated means" (S), caps uploads at 30/day (S), and charges Standard-tier accounts 50% of monthly earnings (S).
6. Amazon KDP is rejected: no API; mandatory disclosure of "AI-generated" content defined as "created by an AI-based tool ... even if you applied substantial edits afterwards" (P); a reported cap of two new titles per format per week since 2026-09-21 (T; KDP Community page is JS-only); a low-content category Amazon has throttled since 2023.
7. Faceless YouTube is rejected: the monetization policy says content must "Not be mass-produced, generic, repetitive, or manipulative" and that "channels where content feels interchangeable from video to video are not allowed to monetize" (P, updated July 15 2025); videos uploaded "from unverified API projects created after 28 July 2020 will be restricted to private viewing mode" (P); default upload quota is 100 `videos.insert` calls/day and more needs a compliance audit (P).
8. TikTok is rejected on the same grounds: "All content posted by unaudited clients will be restricted to private viewing mode" (P) and AI-generated videos are reported ineligible for Creator Rewards (T).
9. Shutterstock: "Shutterstock will not allow AI-generated content to be submitted by contributors for licensing on our platform" (P, dated July 16 2025). Pond5, Epidemic Sound and Envato ban it (T). Freepik, Vecteezy, 123RF and Dreamstime allow it at cents per download (T). Rejected on economics.
10. Etsy's API is usable for an own shop: the Seller App tier is "Automated, near-instant for eligible sellers" with "access to all public and OAuth-authenticated endpoints, scoped only to your registered shop" (P). The publish flow is `createDraftListing` then `updateListing` with `state` set to `active` (P). Commercial Access is effectively unobtainable (P: repeated unexplained denials through 2026-10-01, no Etsy staff reply). Etsy's AI disclosure rule and "Designed by a seller" classification are S (etsy.com 403s).
11. Canva Creators is rejected for now: Element Creator applications closed, Template Creator in beta with a months-long wait (S), and payouts from an opaque royalty pool.
12. Micro-SaaS, Chrome extensions, Shopify apps and WordPress plugins are buildable by agents, but the distributions are brutal: "The median listed app earns under $1,000 per month" (T, a Shopify app founder's analysis), and 54% of Stripe-verified Indie Hackers products report $0 (T). Shopify's 0% revenue share on the first $1,000,000 of gross app revenue (P) is the one structural edge. Deferred.
13. Claude API cost for an agent loop is small next to platform fees: roughly $0.10 to $0.20 per product at Sonnet 5.5 / Opus 5.5 pricing, $30 to $150 per month per loop. Cloud sessions and Routines run on Chris's plan, so the marginal cost may be plan usage rather than API dollars.
14. The "make money with AI" claims ("$10K/month POD", "faceless YouTube passive income", "KDP low-content empire") rest on self-reported income from people selling courses or tools. Gumroad's own terms now ban "false or unsubstantiated claims about a Product or its outcomes, including earnings" (P), which says something about how common they are. No audited per-creator income data exists for any option here.
15. Recommended 30 to 60 day test: run productized services and one Shopify POD or digital store in parallel; add Etsy as a second channel once the store has products with any sales signal. Kill criteria are listed per pick.

## Chris's tooling, mapped to loop steps

| Step | Tool that does it | Notes |
|---|---|---|
| Niche/trend research | WebSearch, Semrush MCP (when units exist), Shopify `run-analytics-query`, Google Trends via browser | Semrush out of API units today |
| Design/creation | Claude Design, Adobe Express/Firefly tools (generate, background removal, vectorize, generative expand), code for templates and spreadsheets | Firefly output is Adobe-licensed; check the plan's commercial terms and generative credit allowance |
| Mockups | Printful Mockup Generator API (10 req/60 s established, 2 req/60 s new stores, 20,000 files/day, P), Printify mockups, Gelato templates | |
| Listing copy, SEO | Claude | Etsy and Shopify SEO fields fillable by API |
| Pricing | Claude + platform cost APIs | |
| Upload/publish | Shopify MCP (`create-product`, `create-digital-product`, GraphQL), Printful Ecommerce Platform Sync API, Printify `publish.json`, Gelato `create-from-template`, Etsy Seller App | |
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
| Mockups | AGENT | Printful Mockup Generator API, rate-limited (P) |
| Listing/pricing | AGENT | Printful: "The ecommerce platform sync API allows you to automatically assign Printful products and print files to the products in your online store (Shopify, Woocommerce, etc.) that is linked to Printful" (P). Printify: `POST /v1/shops/{shop_id}/products/{product_id}/publish.json`, "The product publishing endpoint has a limit of 200 requests per 30 minutes" (P). Gelato: `create-from-template` endpoint (T; dashboard.gelato.com 403s) |
| Upload | AGENT | As above, plus Shopify MCP `create-product` and GraphQL for collections, metafields, SEO |
| Marketing | AGENT (organic, email), MANUAL-CHRIS (ad budget) | Klaviyo flows, blog content, Beehiiv; paid ads need a card and sign-off |
| Customer service | AGENT drafts, MANUAL-CHRIS approves | Gmail drafts; Printful covers reprints on manufacturing errors ("If a manufacturing error occurs, we cover a free reprint or refund", P) |
| Fulfillment | AUTOMATIC | Native to the integrations |
| Payouts/tax | MANUAL-CHRIS one-time | Shopify Payments identity, bank, tax settings |
| Store creation | MANUAL-CHRIS one-time | Shopify signup; no public API mints a store or app credentials (T) |

**Terms on automation and AI (P unless marked):**
- Printful API: "general rate limit of 120 API calls per minute"; Ecommerce Platform Sync writes "Up to 10 requests per 60 seconds"; Mockup Generator "Up to 10 requests per 60 seconds for established stores; 2 requests per 60 seconds for new stores ... 20,000 files per account in a 24-hour period". "The Products API is not intended and will never support creating and managing products in external platforms such as Shopify, WooCommerce and others. For managing your products from external platforms please refer to Ecommerce Platform Sync API." Printful plans: Free $0; Growth $24.99/month, free at $12K/year in sales, "Up to 33% off product pricing".
- Printful on AI designs (blog, P): "Copyright risks often come from prompts rather than the technology itself. Avoid generating art that directly references copyrighted characters, brand logos, or the recognizable style of living artists." It recommends reverse-image searches on final designs and disclosing AI use in product descriptions. No ban on AI designs.
- Printify API: "600 requests per minute" global; Catalog API 100/min; publish 200 per 30 min; "Requests resulting in an error response may not exceed 5% of your total requests." Personal Access Token "allows your application to connect to a single Printify Merchant account", generated under My Profile > Connections, no review. API Terms: license is "only for the purpose to develop, test and support an integration of Your Application with Printify"; you may "not bypass Printify API restrictions for any reason"; "Printify reserves the right to terminate or suspend Your access to the Printify API for any reason and at any time". No clause against automated product creation.
- Gelato: API available on the free plan (T; support.gelato.com article lists Gelato+ as optional).
- Shopify API License and Terms of Use (P): partners may "not bypass Shopify API restrictions for any reason, including automating administrative functions of the Merchant Store Admin" and may "not use the Shopify API to conduct any systematic or automated data collection activities (including scraping ...)". Using the Admin API through an authorized app (which is what the MCP is) is the intended path; the prohibition is on scripting the admin UI around the API.
- Shopify pricing (P): Basic "$39 USD/mo" monthly or "$29 USD/mo" yearly; "Online standard card rates 2.9% + 30¢"; "Third-party transaction fees 2%".

**Demand and saturation:**
- Printful survey of 68 POD store owners (P): "When asked about the single most difficult part of starting a print-on-demand business, most customers said it was marketing": marketing strategy 29%, finding the audience 21%, creating designs 15%, billing and taxes 13%.
- Printify (P): "print-on-demand sellers earn between $0 and $3,000 per month during their first 18 months"; new sellers (0 to 6 months) "$0 to $100+" net monthly; growing stores (6 to 18 months) "$1,000 to $3,000+"; "the average seller takes 165 days to hit their first $1,000 in revenue"; top sellers "publish an average of ten new listings weekly and typically launch 67 designs before reaching their first major sales goal". These are Printify's own aggregate claims with no methodology published; treat as the vendor's best case.
- Printful margin table (P): t-shirts base $10 to $15, retail $25 to $35, gross 45 to 55%, net 20 to 35%; mugs net 30 to 45%; posters net 35 to 50%. "For most POD sellers, that final number is significantly lower than the gross figure suggests."
- Market size: $11B to $15B for 2025/2026 depending on the vendor quoting it (P from Printful and Printify blogs citing research firms; low confidence).

**Costs:**
- Shopify Basic $39/month or $29 annual (P); card fees 2.9% + $0.30 (P).
- Bella+Canvas 3001 at Printful: $12.25 base + $4.95 US shipping, or $11.50 + $4.69 in a January 2026 figure (T; Printful's product page renders prices client-side and returned no price text). A $24.99 shirt nets roughly $8 before card fees and before any ad spend.
- Claude API: ~$0.10 to $0.20 per product for research, copy and QA at Sonnet 5.5 ($2/$10 per MTok) or Opus 5.5 ($4/$20); a daily Routine doing trend scans and order checks is a few dollars a day. Budget $30 to $150/month.
- Ad spend: assume $300 to $1,000/month to learn anything in 60 days. Printify's own case study: "Created 100 designs before spending a dollar on ads, then tested with a $100 Facebook ad budget" (P, anecdote).

**Time to first dollar and ceiling:** Printify's 165-day average to the first $1,000 in revenue (P, vendor claim) is the best available number. Ceiling for a single-niche store with no audience: Printify's own $0 to $100/month for the first six months. Ceiling with a real brand and ad engine: unbounded, but then it is an ecommerce business, not a hands-off loop.

**Risks:** trademark takedowns and permanent suspension (T); Shopify Payments reserves if dispute rate rises (T, 0.5 to 0.75% thresholds cited for Stripe); AI-art copyright is unprotectable in the US so designs can be copied freely (Printful blog, P, citing the Copyright Office).

**Grifter check:** The pitch is "AI designs + POD = passive income." The platforms' own numbers say designs are the cheap part and marketing is the expensive one. Every "$10K/month" claim found was from a tool vendor or course seller. Even Printify's top-seller tier ($10,000 to $80,000+/month) is labelled "18+ months" and "Building a recognizable brand".

### 2. Amazon Merch on Demand (no API; Chris uploads)

**Loop:**

| Step | Who | Reason |
|---|---|---|
| Research, design, copy, pricing, trademark pre-check | AGENT | |
| Application | MANUAL-CHRIS | Invitation/approval model, manual review 2 to 8 weeks (T); 2026 reviewers reportedly check for "low-effort AI artifacts" and expect portfolio links (T, single source) |
| Upload | MANUAL-CHRIS | No API. Chrome extensions exist (MerchAuto, Merch Titans, MerchGhost) but Amazon's own policy could not be read (login wall); Playwright uploads are a ban risk until it is |
| Tier gating | IMPOSSIBLE to bypass | Tier 10 = 10 live designs; 1 to 2 uploads/day at low tiers (T) |
| Marketing | AGENT (external traffic) | Now matters for royalty tier |
| Payouts/tax | MANUAL-CHRIS one-time | |

**Terms:** merch.amazon.com resource pages return an empty body without login (fetched, P for the fact that they are gated). Amazon publishes no separate AI rule per third parties; AI designs face the same IP, content and metadata checks (T).

**Demand/royalty:** Merch Titans, 2026-04-15 (T): "Starting June 1, 2026, the flat royalty system ... is gone. In its place: a three-tier structure"; Creator tier (<15% non-organic US sales) $2.44 on a $19.99 tee; Plus (15 to 34%, 10 units/month) $4.88; Premium (35%+, 10 units/month) $5.27; "Your tier is recalculated monthly using a trailing 60-day window." mydesigns.io and amzprep repeat the same figures. None is Amazon. The same article advertises "Coming Soon: Automated External Traffic from Merch Titans", so the source sells a product that benefits from the story. Approval rate "30 to 40%" (T, Merch Titans; weak).

**Verdict: rejected.** Manual gatekeeping at entry, tier caps, strict IP enforcement, no automation path, and an apparent royalty cut for anyone not driving their own traffic.

### 3. Redbubble (no API; Chris uploads)

**Terms (S, every Redbubble host returns 403):** users may not upload "using any bot, scraper, or other automated means for any purpose without written permission"; "You may upload up to 30 works per day"; violating accounts "will be immediately and permanently disabled". Fees: Standard tier 50% of monthly earnings, Premium 20%, Pro 0%, capped at $150 per payment period for Standard/Premium (S). AI art allowed; mass-uploaded unedited AI art "can trigger spam filters" and demotion (T).

**Verdict: rejected.** Automation is explicitly banned, half of earnings go to fees at the tier a new account lands in, and the cap makes volume impossible.

### 4. Etsy (digital downloads and POD)

**Loop:**

| Step | Who | Reason |
|---|---|---|
| Shop open, ID, bank | MANUAL-CHRIS one-time | Persona photo ID + selfie, Plaid bank link, $15 to $29 setup fee (S, etsy.com seller handbook; page 403s) |
| Research/design/copy | AGENT | |
| Listing | AGENT | Seller App (P, developers.etsy.com): "Any seller with an active Etsy shop in good standing who doesn't already have an active app"; "Eligible sellers are approved within minutes, with no manual review queue"; "access to all public and OAuth-authenticated endpoints, scoped only to your registered shop"; "Commercial use: Not permitted". Publish flow (P, listings tutorial): `createDraftListing` with quantity, title, description, price, who_made, when_made, taxonomy_id, image_ids; then "To make a listing active after uploading a required image, use the updateListing endpoint with the state parameter set to 'active'". Digital products: set `type` to "download" and use `uploadListingFile`. For POD, Printify's Etsy integration publishes with Printify's own OAuth app, so no Etsy API key is needed (T) |
| Commercial API access | IMPOSSIBLE in practice | GitHub discussion #1699 (P): denied repeatedly 2026-08-21 to 2026-10-01 with "generic" reasons, "AI canned responses" from support, no Etsy staff reply. Not needed for one own shop |
| Marketing | AGENT (Etsy SEO, email) | Etsy brings buyers; Offsite Ads are automatic |
| Customer service | AGENT drafts | |
| Payouts/tax | MANUAL one-time | Etsy Payments |

**Terms on AI (S; etsy.com/legal/creativity returns 403 to every fetch):** Etsy allows "seller-prompted AI creations ... generated using AI tools ... based on a seller's original prompts" and requires sellers to "disclose within their listing description if an item is created with the use of AI". AI items are "Designed by a seller", never "Made by". AI prompt bundles are prohibited. Third parties report Q1 2026 enforcement figures (12,000 listings removed, 8,500 warnings) that could not be verified (T, single source).

**Demand (P, Etsy Q4 2025 press release):** "Active sellers totaled 5.6 million, a 1.5% year-over-year decrease"; "Active buyers totaled 86.5 million, down 3.4% year-over-year"; "GMS per active buyer on a trailing twelve month basis was $121"; Etsy marketplace GMS for 2025 $10,460.7 million. 237M active listings is from the 10-K via search snippets (S). Digital downloads growth rate claims (25 to 30% YoY) are T and weak.

**Fees (T; etsy.com/legal/fees 403s):** $0.20 listing, 6.5% transaction, 3% + $0.25 processing, Offsite Ads 15% (optional under $10K/yr) or 12% (mandatory over). Combined 10 to 11% without Offsite Ads, 24 to 26% on attributed sales.

**Time/ceiling:** Etsy supplies traffic, so first sales inside 30 to 60 days are plausible for well-targeted digital listings (anecdotal). "Average successful seller" figures are survivorship numbers (T).

**Risks:** suspension for missing AI disclosure; shop tied to Chris's identity; Seller App revocable; IP takedowns remove listings without warning (T); the Q4 2025 release shows a marketplace with slightly shrinking buyer and seller counts, so new listings compete for a flat pool.

**Grifter check:** "100 AI listings in a weekend" is the pitch. The reality is a disclosure regime, a 24 to 26% fee stack when Offsite Ads fire, and a flat buyer base. Bulk unedited AI output is exactly what the standards target.

**Verdict: survives as a second channel.** Build the catalog on the owned store, then publish the best sellers to Etsy with disclosure.

### 5. Digital products on an owned storefront (Shopify Digital Downloads, Gumroad, Payhip, Lemon Squeezy, Whop, Notion)

Covers templates, Notion templates, printables, spreadsheets, planners, Lightroom presets (XMP), icon sets, fonts.

**Loop:** research, creation, listing, pricing, upload, email marketing, support drafts: AGENT. Store/account creation, KYC, tax: MANUAL-CHRIS one-time. Paid promotion: MANUAL approval.

**Platform facts:**
- Shopify Digital Downloads: free, Shopify-built, 5 GB per file (T, app store via review sites). The Shopify MCP's `create-digital-product`, `upload-digital-product-file` and `publish-digital-product` cover the publish step.
- Gumroad (P): "10% + $0.50 Per transaction for all sales through your profile or direct links"; "30% Per transaction when new customers find and buy from you through our discover marketplace"; "Since January 1, 2025, Gumroad handles ALL your tax obligations" as merchant of record. Prohibited list (revised September 16 2026) bans "AI services which includes selling access to AI tools, chatbots, image or content generation services, or subscriptions to AI services that are fulfilled outside of Gumroad" and "reselling private label rights products"; it does not ban AI-made products. Terms ban using "manual or automated software ... to 'scrape' or download data" and ban "false or unsubstantiated claims about a Product or its outcomes, including earnings, income ... claims that Supplier cannot substantiate" and fabricated social proof.
- Payhip: free plan 5% + processor fees; $29 plan 2%; $99 plan 0% (T; payhip.com 403s).
- Lemon Squeezy (P, pricing page): "5% + 50¢" with "no monthly charges for ecommerce features"; the site headlines a "2026 Update: Lemon Squeezy + Stripe Managed Payments". Third parties report signups waitlist-gated since mid-2026 and growth pushed to Stripe Managed Payments at 6.4% + $0.30 (T). Not a platform to build on now.
- Whop (P, Seller Terms): "our Financial Partners and applicable law require we verify your identity upon onboarding"; "You may not offer or list 'lifetime,' 'perpetual,' or indefinite-access Products"; excessive chargebacks allow suspension "without prior notice". Fees 2.7% + $0.30 + $0.10 (T). No AI policy found.
- Notion Marketplace (P): "Notion charges a 8% fee plus 40 cents per transaction"; "Creators will need to join the waitlist, get approved by the Notion team, and onboard with Stripe to start selling directly on Marketplace"; payouts biweekly, $20 minimum, 14-day hold; buyers can refund within 14 days and refunds are debited from the creator.
- Creative Market: curated application, 3 to 7 business days, AI allowed with a disclosure label (T; all Creative Market hosts 403).
- Fonts: MyFonts and Fontspring need foundry application and human review, 50% royalty; "auto-traced-looking curves can get rejected" (T).

**Demand:** InsightRaider's Gumroad analysis (T): "The median Gumroad creator earns $72 per month"; "44% of all Gumroad products generated exactly $0"; revenue "Calculated via ratings count × average price × industry conversion multiplier", so it is an estimate, not platform data; "Without an audience, the median time to first $500/mo is 6-12 months." Notion templates: "$0 to about $3,000 a month" (T).

**Costs:** Shopify Basic $39/month (P) or Gumroad at $0 fixed (P). Agent cost $30 to $100/month. Ad spend optional, but there is no organic traffic for a new store.

**Time/ceiling:** First dollar depends on a traffic source. With SWAE's existing audience a B2B template could sell in weeks (anecdotal). Ceiling: the Gumroad median says most products never pass $100/month.

**Risks:** chargebacks and friendly fraud on digital goods; processor reserves; uncopyrightable AI output gets copied; Discover-type marketplace fees of 30% (P).

**Grifter check:** "Sell Notion/Canva templates with AI, $5K/month" dominates YouTube and Medium. The one large dataset found shows a $72/month median, and Gumroad has written an earnings-claims ban into its terms. The success stories are real outliers with audiences.

**Verdict: survives**, conditional on a traffic source. The strongest version is B2B products for SWAE's own client base and local-business niche (SEO checklists, GBP post calendars, review-response scripts, site care documentation), where Chris already has distribution.

### 6. Amazon KDP (no API)

**Loop:** manuscript/interior/cover AGENT; upload MANUAL-CHRIS; marketing AGENT, Amazon Ads MANUAL.

**Terms (P, KDP Content Guidelines):** "We require you to inform us of AI-generated content (text, images, or translations) when you publish a new book or make edits to and republish an existing book through KDP ... You are not required to disclose AI-assisted content." "AI-generated: ... If you used an AI-based tool to create the actual content (whether text, images, or translations), it is considered 'AI-generated,' even if you applied substantial edits afterwards." "AI-assisted: If you created the content yourself, and used AI-based tools to edit, refine, error-check, or otherwise improve that content ... It is not necessary to inform us of the use of such tools."

**Low-content (P):** "A low-content book has minimal or no content on the interior pages ... designed to be filled in by the user"; examples: notebooks, planners, diaries/journals, prompt journals; "Low-content books are not eligible for the free KDP ISBN"; "we don't currently offer Release Date for low-content books"; the Low-content category box must be checked "or your book will be rejected".

**Title cap:** two new titles per format per week from 2026-09-21 (T; kdpcommunity.com renders client-side and returned no text; six third-party pages agree).

**Royalties (P, Paperback Royalty page):** "KDP now offers both a 50% or 60% royalty rate on paperbacks"; 50% "for list prices at or below" $9.98, 60% "at or above" $9.99; "(Royalty rate x list price) – printing costs = royalty"; worked example $15 list, 333 pages: $4.00. eBook 70% at $2.99 to $12.99 (T).

**Verdict: rejected.** Manual upload, weekly throttle, disclosure flag, and a low-content category that Amazon has been throttling since 2023.

### 7. Canva Creators

**Status (S; canva.com 403s):** Element Creator applications closed as of 2025; Template Creator "currently in BETA and taking early applications", portfolio required, "up to a couple of months" for an answer. Payment is a share of a monthly royalty pool weighted by Pro template exports, $10 threshold (S/T).

**Verdict: rejected for the 60-day window.** Apply anyway as a free background task.

### 8. Micro-SaaS, Chrome extensions, Shopify apps, WordPress plugins

**Loop:** build, test, listing copy, docs: AGENT. Store accounts, developer fees, review submissions, support escalation: MANUAL-CHRIS. Review: human reviewers.

**Terms:**
- Chrome Web Store (P): "We don't allow any developer, related developer accounts, or their affiliates to submit multiple extensions that provide duplicate experiences or functionality"; "An extension must have a single purpose that is narrow and easy to understand"; no unattributed testimonials; one appeal per violation.
- Shopify (P): "You keep 100% of your first $1,000,000 USD in gross app revenue earned from January 1, 2025, and 85% of earnings above that. All billing is subject to a 2.9% processing fee"; $19 one-time App Store registration; the $1M threshold is lifetime across Associated Developer Accounts; developers with $20M+ app earnings or $100M+ company revenue pay 15% on everything.
- WordPress.org (P, Plugins Team 2025 review): submissions "stabilising at around 330 submissions per week"; "12,713 plugins" reviewed in 2025; "69.5% of reviewed plugins were approved"; team goal "to keep the queue for a first review under one week"; "AI has lowered the barriers to entry without compromising plugin quality (since the 'barrier' for plugin approval has not been lowered)". No AI-plugin policy.

**Demand:** weekonelabs (T, written by a Shopify app founder): "roughly 18,000 listed apps ... with 500–800 new apps added every month"; "The median listed app earns under $1,000 per month, and a meaningful chunk earn nothing"; top 10% clear $100K+ ARR. Indie SaaS: 54% of Stripe-verified Indie Hackers products at $0 (T). Chrome extensions: category medians of $500 to $2,000/month (T, unsourced).

**Costs:** Chrome $5 one-time; Apple $99/year; Google Play $25 plus, for personal accounts created after November 13 2023, "a closed test for their app with a minimum of 12 testers who have been opted in continuously for at least 14 days" before production access (P); hosting; support time.

**Verdict: deferred.** Agents can build these and Chris already ships WordPress plugins, but the medians say most earn nothing and support is a human job. Shopify's 0% share is the reason to revisit after picks 1 and 2 are running.

### 9. Mobile/web apps with ads

AdMob eCPM: Tier-1 banners $0.50 to $1.50, interstitials $5 to $8, rewarded video $15 to $30 (T). Google Play policy lists "AI-Generated Content" as its own policy area and bans repetitive apps (P, policy index; detailed text not extracted). The 12-tester rule applies (P). **Rejected:** acquisition cost, store gating, and ad-only revenue needs scale no agent loop produces.

### 10. Paid newsletter (Beehiiv)

**Loop (P):** the Create post endpoint is "Available on beehiiv Pro and Enterprise plans"; "The above minimum request objects will create a post that publishes immediately with your default template to all free subscribers. Starting August 6, 2026, this behavior requires explicitly passing 'status': 'confirmed'"; omitted status now yields a draft even with `scheduled_at`. Pricing page (P): Free $0; Lite $49/month yearly; Pro $95/month yearly; "beehiiv takes 0% of your paid subscription and digital product revenue ... minus Stripe's standard processing fee of 2.9% + $0.30"; ad monetization "Avg. $39/mo" (beehiiv's own figure for Lite/Pro, no methodology). Older plan names (Launch/Scale/Max) in beehiiv's 2026 blog are superseded by the current Free/Lite/Pro page.

**Demand:** Ad Network reportedly needs 1,000+ confirmed subscribers (T). beehiiv reports $19M paid-subscription revenue across all creators in 2025 (T). No per-creator distribution.

**Verdict: survives only as a channel** feeding picks 1, 3 and 5. As a standalone product it needs an audience first, and API posting costs $95/month.

### 11. Faceless YouTube / TikTok automation

**YouTube terms (P, channel monetization policies):** "July 15, 2025: We're making a minor update to our 'repetitious content' policy to better clarify this includes content that is repetitive or mass-produced. We are also renaming this policy from 'repetitious content' to 'inauthentic content.'" Content must "Not be mass-produced, generic, repetitive, or manipulative. It should be made for the enjoyment or education of viewers, rather than for the sole purpose of getting views." "Generic or repetitive content includes content that looks like it's made with a template"; "channels where content feels interchangeable from video to video are not allowed to monetize". Reviewers look at "Main theme, Most viewed videos, Newest videos, Biggest proportion of watch time, Video metadata". Reused content policy unchanged. The specific "AI-generated content made with generic or unoriginal templates" wording appears in the search snippet of the same page (S) but was not in the fetched text; treat as S.

**YPP thresholds (P):** "1,000 subscribers with 4,000 qualified watch hours in the last 12 months, or ... 1,000 subscribers with 10 million qualified Shorts views in the last 90 days"; "Every channel that meets the threshold will go through a standard review process." Doubling on 2027-02-01 is T.

**API (P):** "All videos uploaded via the videos.insert endpoint from unverified API projects created after 28 July 2020 will be restricted to private viewing mode. To lift this restriction, each project must undergo an audit"; default quota "100 search.list calls, 100 videos.insert calls, and 10,000 units per day" (page last updated 2026-09-14); "To request quota beyond the default, an audit demonstrating compliance with the YouTube API Services Terms of Service is required."

**TikTok (P):** "All content posted by unaudited clients will be restricted to private viewing mode. Once you have successfully tested your integration, to lift the restriction on content visibility, your API client must undergo an audit"; error code `unaudited_client_can_only_post_to_private_accounts`. Creator Rewards excludes fully AI-generated videos (T). RPM claims ($10 to $25 finance niche) come from faceless-channel tool vendors (T, weak).

**Verdict: rejected.** The policy was written against this exact loop, the publishing API is gated behind a human audit, and the threshold to earn anything is a year of audience building.

### 12. Stock media (non-Adobe)

- Shutterstock (P, July 16 2025): "Shutterstock does not accept AI-generated content from our contributors ... Shutterstock will not allow AI-generated content to be submitted by contributors for licensing on our platform." Reasons: IP ownership cannot be assigned to an individual and model sources cannot be verified.
- Pond5: prohibits all AI-generated content (T; contributor.pond5.com returned 202 with no body). Epidemic Sound: no AI submissions (T). Envato: "does not allow authors to publish or submit AI-generated content" as standalone or primary component (T; help.author.envato.com 403s).
- Freepik: accepts AI with labeling; first batch 150 to 200 files; $0.04 to $0.07 per download (T; freepik.com 403s). Vecteezy: accepts AI with an "AI-Generated?" checkbox and program dropdown; photos must look real; near-duplicates rejected (S/T; vecteezy.com 403s). 123RF and Dreamstime accept with labeling (T).

**Verdict: rejected.** Where AI is allowed, pay is cents per download.

### 13. Unity Asset Store / Fab

Unity (P, Submission Guidelines 1.6): "Content generated with the aid of AI, completely or in part, must transparently disclose this information in the marketing data. The specific AI tools used and the content generated using AI must be disclosed in the 'AI description' field"; "Content generated by AI or AI-assisted content cannot use keywords or terms that would imply human effort (e.g., 'drawn', 'hand drawn', 'painted')"; "Unity reserves the right to reject submissions that are mass-produced using AI and lack sufficient differentiation or unique value relative to the publisher's existing catalog"; "photoscanned or AI-generated data is retopologized and optimized to a state that users can edit". Fab (P): "You will receive 88% of the revenue generated by your product sales"; payments "approximately 30 days after the end of each month ... when the amount to be paid is $100 USD or more". Fab's AI flag and pure-AI ban are T. **Rejected:** usable game assets need a human artist.

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

**Terms:** none. No platform, no AI disclosure regime, no tiering.

**Demand and pricing (P, Promethean Research 2025 Digital Agency Industry Report, PDF read):**
- "A third (36%) of digital agencies in our latest survey charged between $175-199/hr., while another third (32%) charged between $200-249/hr."; "28% of agencies raised prices from 2024 to 2025."
- "Agencies earn an average net margin of about 16% over this timeframe ... in 2024 ... the average agency earned a net margin of 14%." "Smaller agencies tend to earn higher net margins than larger ones." (Correction to the earlier draft, which repeated a third-party "13% net margin" figure.)
- "95% offered projects, 91% offered retainers, and 88% offered both"; "fast-growing agencies completed 24% more projects while serving 16% fewer retainer clients than average" (so the earlier third-party claim that retainer-heavy agencies earn 8 points more margin is not in this report and is dropped).
- "AI-related services grew steadily, from 10% in 2023 to 17% in 2025."
- "specialized agencies also tend to earn higher net margins than generalists."
- Local SEO retainers most commonly $500 to $1,000/month; GBP management $125 to $400/month per profile; website care plans $100 to $250/month (T, vendor pricing pages).

**Costs:** Claude usage for delivery (Opus for client-facing review, Sonnet for drafts), already-paid connectors, Chris's review time. No platform fees.

**Time/ceiling:** First dollar is as fast as the first existing client who adds a package: days. Ceiling bounded by how many clients SWAE can sign and how much review Chris's rule requires. Evidence for pricing: strong relative to everything else here.

**Risks:** quality failures reach real clients; Chris's approval rule caps throughput; AI-produced copy must pass the de-AI rules; scope creep; clients "increasingly expect cheaper services due to AI" (T).

**Grifter check:** "AI automation agency" is itself a grift category. The difference here is SWAE already is an agency with clients, a dashboard, and billing. The claim is narrow: existing services get cheaper to deliver, and new recurring packages can be delivered mostly by agents at market prices.

---

## Ranking and picks

### Pick 1: Productized recurring services through SWAE

**Verdict.** The only option where demand is proven, pricing is benchmarked by an industry survey (P), distribution exists, and no platform can revoke access or change royalties. The agent does the delivery; Chris does the approving. It is the least "passive", because every client-visible artifact needs his sign-off, so the design goal is packages whose deliverables batch into one weekly review.

**Minimum viable agent loop.** A weekly Routine per client: pull Semrush/GSC/GA data, draft the month's GBP posts and review responses, draft two local-SEO posts via WordPress.com MCP as drafts, run a monitored-site check, assemble a one-page report, and queue everything as dashboard task comments for Chris's working-hours approval. Billing via existing invoices.

**Manual steps Chris cannot avoid.** Approve pricing and packages; approve every client-facing post; sign new clients; handle escalations.

**Falsifiers in 30 to 60 days.** Fewer than two existing clients take an add-on at $250 to $500/month; Chris's review time per client per month exceeds two hours (then "agents do the work" fails on his time); a client rejects a deliverable for reading as AI.

### Pick 2: Shopify POD store (Printful or Printify API + Shopify MCP), one niche

**Verdict.** The most automatable physical-product loop available. Every step from research to publish has an API or MCP tool (P for Printful, Printify and Shopify), fulfillment is automatic, and no platform tier gates it. The weakness is that nothing brings buyers; Printify's own table says $0 to $100/month for the first six months (P). Net margins of 20 to 35% on tees (P, Printful) leave little room for paid traffic, so the niche must be one where organic or email reaches buyers.

**Minimum viable agent loop.** Weekly Routine: scan trends in one niche, generate 5 to 10 designs with Firefly/Express, vectorize and trademark-screen (reverse-image search per Printful's own advice), generate mockups via Printful, create products via the Printful Sync API or Printify publish, set collections/SEO via Shopify MCP, publish a blog post, send a Klaviyo campaign to any list, pull `run-analytics-query` and prune non-sellers monthly. Order emails drafted in Gmail for approval. Target Printify's benchmark cadence of ten listings a week.

**Manual steps.** Shopify signup and Shopify Payments identity; connect Printful/Printify; approve ad budget; sales tax decisions; respond to IP complaints.

**Falsifiers.** Zero orders in 60 days with 40+ products live and $300+ of ad or email reach; any IP complaint (process failure); cost per acquisition above gross margin after 30 days of ads.

### Pick 3: Digital products from an owned storefront, B2B-leaning

**Verdict.** Fully agent-producible and fully agent-publishable through Shopify Digital Downloads or Gumroad (P for fees). The $72/month Gumroad median (T) is the honest baseline for a product with no audience. The version that beats it uses SWAE's reach: products for local-business owners and small agencies, promoted through the newsletter (pick 5) and the SWAE site.

**Minimum viable agent loop.** Monthly: pick a product from a backlog, build it, QA it, write the listing and a landing page, publish via `create-digital-product`, add to Klaviyo flows, publish a supporting WordPress post, report sales.

**Manual steps.** Storefront account/KYC; refund policy; approve copy.

**Falsifiers.** Fewer than 10 sales total across three products in 60 days; refund/dispute rate above 1%; products copied and undercut within weeks (expected for uncopyrightable AI output; a signal to add a service component).

### Pick 4: Etsy as a second channel for picks 2 and 3

**Verdict.** Etsy supplies the buyers the owned store lacks, and the Seller App tier plus `createDraftListing` / `updateListing state=active` makes listing automatable (P). The cost is ID verification tied to Chris, a 10 to 26% fee stack, and a disclosure regime. List AI-made items as "Designed by a seller" with the disclosure sentence in every description.

**Minimum viable agent loop.** After pick 2 or 3 has products with any sales signal: register a Seller App, mirror the top products as Etsy listings with AI disclosure, sync via Printify for POD, monitor Etsy stats weekly through the API.

**Manual steps.** Shop open, Persona ID, Plaid bank, setup fee; production partner disclosure; responding to any Creativity Standards notice.

**Falsifiers.** A Creativity Standards warning or listing removal in the first 30 days; Etsy fees plus Offsite Ads pushing net margin below zero on POD; no Etsy sales after 60 days with 30+ listings.

### Pick 5 (channel, not product): Beehiiv newsletter

Run only in service of picks 1, 3 and 4. API posting needs the Pro plan at $95/month yearly (P); the Free plan is fine while an agent drafts and Chris pastes. Kill if it cannot reach 300 confirmed subscribers in 60 days from SWAE's existing contacts and site.

---

## Rejected options, one line each

- **Amazon Merch on Demand:** no API, manual gated entry, 10-design start, reported June 2026 royalty halving without external traffic.
- **Redbubble:** automated uploads banned by User Agreement; 50% fee at Standard tier; 30/day cap.
- **Amazon KDP:** no API; AI-generated disclosure defined to include heavily edited output; weekly title cap; low-content saturated.
- **Canva Creators:** Element applications closed; Template beta with months-long wait; opaque royalty pool. Apply anyway, it costs nothing.
- **Faceless YouTube:** inauthentic-content policy targets templated output; API uploads private until human audit; 100 uploads/day default quota.
- **TikTok:** API posts private until audit; AI-generated video excluded from Creator Rewards.
- **Stock media (Shutterstock, Pond5, Epidemic, Envato):** AI submissions banned.
- **Stock media (Freepik, Vecteezy, 123RF, Dreamstime):** allowed, cents per download.
- **Unity Asset Store / Fab:** disclosure regimes, mass-produced-AI rejection clause, assets need a human artist.
- **Mobile apps with ads:** 12-tester gate, $99 Apple fee, eCPMs that need 10K+ DAU.
- **Micro-SaaS / Chrome extensions / Shopify apps / WordPress plugins:** buildable, but medians under $1K/month and support is human work. Deferred.
- **Lemon Squeezy:** waitlist-gated and being steered to Stripe Managed Payments.
- **Whop:** fine as a checkout, no demand advantage; KYC before payout; no lifetime products.
- **Notion Marketplace standalone:** waitlist approval plus 8% + $0.40; folded into pick 3.
- **Fonts on MyFonts/Fontspring:** human foundry review; auto-traced curves rejected.
- **Lightroom presets:** folded into pick 3; not a separate business.

## Claude API cost model for the loops

Pricing from the claude-api skill (cached 2026-09-25): Opus 5.5 $4/$20 per MTok, Sonnet 5.5 $2/$10, Haiku 4.5 $1/$5. Per product (research 10K in, design brief and QA 10K in, listing copy 3K out, review 2K out) on Sonnet: ~$0.09; on Opus: ~$0.18. A daily Routine doing a trend scan, analytics pull and order check: ~$0.50 to $3 per run. Monthly per loop: $30 to $150 at API rates. Cloud sessions run on Chris's plan, so the practical cost is plan usage; the API figure is the ceiling. Image generation through the Adobe connector is billed in Adobe credits, not Anthropic; check the plan's generative credit allowance before scaling designs.

## Pages read in full this session (primary)

- YouTube: support.google.com/youtube/answer/1311392 (monetization policies); /answer/72851 (YPP eligibility); developers.google.com/youtube/v3/guides/quota_and_compliance_audits; developers.google.com/youtube/v3/revision_history
- Google Play: support.google.com/googleplay/android-developer/answer/14151465 (12 testers); play.google/developer-content-policy (index only)
- Etsy: developers.etsy.com/documentation/ (access tiers); /documentation/tutorials/listings; /documentation/essentials/authentication; investors.etsy.com Q4 and FY2025 results; github.com/etsy/open-api/discussions/1699
- KDP: kdp.amazon.com/en_US/help/topic/G200672390 (content guidelines, AI); /GGE5T76TWKA85DJM (low-content); /G201834330 (paperback royalty)
- Shutterstock: submit.shutterstock.com/help/en/articles/10594622
- Printful: developers.printful.com/docs/; printful.com/pricing; printful.com/blog (print-on-demand-mistakes, is-print-on-demand-profitable, how-to-sell-ai-art)
- Printify: developers.printify.com; printify.com/api-terms; printify.com/blog (is-print-on-demand-profitable, print-on-demand-statistics)
- Gumroad: gumroad.com/prohibited; gumroad.com/pricing; gumroad.com/terms
- Shopify: shopify.dev/docs/apps/launch/distribution/revenue-share; shopify.com/legal/api-terms; shopify.com/pricing
- Beehiiv: beehiiv.com/support/article/36759164012439 (Send API); developers.beehiiv.com/api-reference/posts/create; beehiiv.com/pricing
- TikTok: developers.tiktok.com/doc/content-posting-api-reference-direct-post
- Notion: notion.com/help/selling-on-marketplace
- Whop: whop.com/seller-terms
- Lemon Squeezy: lemonsqueezy.com/pricing
- Unity: assetstore.unity.com/publishing/submission-guidelines
- Fab: dev.epicgames.com/documentation/fab/publisher-get-started-in-fab
- Chrome: developer.chrome.com/docs/webstore/program-policies/policies
- WordPress: make.wordpress.org/plugins/2026/01/07/a-year-in-the-plugins-team-2025/
- Promethean Research 2025 Digital Agency Industry Report (PDF)
- Secondary sources read in full: merchtitans.com (June 2026 royalty article), insightraider.com (Gumroad statistics), weekonelabs.com (Shopify app benchmarks)

## Primary-source URLs still needing manual browser verification (403 or login wall to every fetch)

- https://www.etsy.com/legal/creativity (Creativity Standards; AI disclosure wording)
- https://www.etsy.com/seller-handbook/article/1275449912004 (Etsy's stance on AI creations)
- https://www.etsy.com/seller-handbook/article/1241780194948 (new-shop onboarding, Persona, setup fee)
- https://www.etsy.com/legal/fees
- https://help.etsy.com/hc/en-us/articles/41918478450967-How-to-Register-a-Seller-App-with-Etsy-s-API
- https://www.redbubble.com/agreement and https://help.redbubble.com/hc/en-us/articles/50959863016724 (automation ban; tier fees)
- https://blog.redbubble.com/2025/08/artist-account-tiers-and-fees/
- https://merch.amazon.com/resource/201858630 and /201846470 (content policy; royalty tiers, needs a Merch login)
- https://www.kdpcommunity.com/s/article/KDP-Title-Creation-Limits-Update (two titles per format per week; JS-rendered)
- https://www.canva.com/help/canva-creators-program/ and https://www.canva.com/creators/templates/
- https://help.author.envato.com/hc/en-us/articles/13313674070681 (Envato AI policy)
- https://contributor.pond5.com/faq/ (returned 202, empty)
- https://www.vecteezy.com/blog/contributor/ai-images-contributors
- https://support.freepik.com (contributor earnings) and https://www.freepik.com/legal/contributor
- https://support.creativemarket.com/hc/en-us/articles/201251700 and https://creativemarket.com/sell
- https://payhip.com/pricing
- https://www.fontspring.com/account/foundries/info and https://foundrysupport.monotype.com/hc/en-us/articles/360028863311-Get-Started
- https://dashboard.gelato.com/docs/ecommerce/products/create-from-template/
- https://www.sec.gov/Archives/edgar/data/1370637/000137063726000019/etsy-20251231.htm (10-K; active listings count)
- https://www.printful.com/custom/mens/t-shirts/unisex-staple-t-shirt-bella-canvas-3001 (price renders client-side)
