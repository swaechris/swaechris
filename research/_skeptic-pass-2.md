# Skeptic pass 2: attack on 01-income-options.md and 02-agent-office-architecture.md

Date: 2026-10-05. Author: skeptic subagent (read-only). Inputs: the two reports and `_skeptic-pass-1.md`.

## Method and tooling

About 60 cited URLs were fetched with `curl -sL` through the session proxy (WebFetch stays blocked), tags stripped locally, and every quoted phrase searched for in the page text. The session's shared WebSearch budget (200 calls) was exhausted before this pass; no WebSearch calls were made here, and nothing in this report depends on a search engine. Where a cited URL 404'd, the correct page was found by crawling the site's own link list. Extracted pages are in the session scratchpad under `pages/`. Pages that still return 403 to every fetch: www.etsy.com/legal/*, help.etsy.com, help.redbubble.com, redbubble.com/agreement, blog.redbubble.com, and github.com/etsy/open-api (the GitHub proxy limits this session to its own repositories). The Promethean 2025 PDF was not available to me; the public 2026 edition page was.

Grades: **P** = page fetched and the quoted text found; **P-mis** = fetched, quote present but attributed to the wrong page; **X** = fetched, quoted text absent; **S** = search snippet only; **T** = secondary; **U** = could not check from here.

Arithmetic was recomputed for every cost, margin and fee figure in both reports. Where a number is wrong or unstated it is in the fix list.

---

## Part A: report 01 (income options)

### A1. Claims unsupported by the cited source (grade X or P-mis)

1. **Shopify API terms quote, line 72.** The report quotes the Shopify API License and Terms of Use as saying partners may "not bypass Shopify API restrictions for any reason, including automating administrative functions of the Merchant Store Admin", graded P. The fetched page (https://www.shopify.com/legal/api-terms, 57k characters, 81 mentions of "Shopify API") contains no "bypass" clause and no "automating administrative functions" or "Merchant Store Admin" text. The Partner Program Agreement (https://www.shopify.com/partners/terms) has one "bypass" sentence, about Shopify Checkout, not admin automation. The second quote on the same line ("not use the Shopify API to conduct any systematic or automated data collection activities (including scraping ...)") is on the page. Grade: X for the first quote, P for the second. The conclusion drawn from it (API through an authorised app is the intended path) is still reasonable, but it is an inference, not a quoted term.

2. **Printful Ecommerce Platform Sync quote, line 59.** "The ecommerce platform sync API allows you to automatically assign Printful products and print files to the products in your online store ... that is linked to Printful" is graded P. The text is not in the rendered HTML of https://developers.printful.com/docs/ (Redoc renders tag descriptions from a JS-loaded spec). It may be in the OpenAPI spec; it could not be confirmed here. Grade: U. The rate-limit quotes on line 68 (120/min, 10 per 60 s, 2 per 60 s new stores, 20,000 files/day, "will never support creating and managing products in external platforms") are all present. Grade: P.

3. **AI art copyright, line 89.** "AI-art copyright is unprotectable in the US so designs can be copied freely (Printful blog, P, citing the Copyright Office)". The cited post (https://www.printful.com/blog/how-to-sell-ai-art) does not mention the Copyright Office, protectability, or human authorship. Its copyright section is about prompts referencing characters, logos and living artists, plus reverse-image checks. Grade: X. The underlying legal point (the US Copyright Office requires human authorship) is true but needs the Office's own guidance as the source, and "copied freely" overstates: trademark, the human-authored parts of a design, and platform IP tools still apply.

4. **YouTube API private-mode rule, line 227.** The "unverified API projects created after 28 July 2020 ... restricted to private viewing mode" wording is on https://developers.google.com/youtube/v3/revision_history (entry dated July 28, 2020), not on the quota_and_compliance_audits page the sentence sits under. The quota figures (100 search.list, 100 videos.insert, 10,000 units/day; "Last updated 2026-09-14") are on the quota page. Grade: P-mis; fix the attribution. Note the rule is six years old, which is fine, but say so.

5. **Printify figures, line 77.** "165 days", "ten new listings weekly" and "67 designs" are on https://printify.com/blog/print-on-demand-statistics/, not on the profitability post that the "$0 to $100+" table comes from. Both posts are in the read list, so this is attribution only. Two wording issues: the page says top sellers "on competitive platforms like Etsy and eBay publish ten new listings every week" (a marketplace cadence, not a standalone-store one), and the 67 figure is "approximately 67 new listings before hitting the $1,000 GMV mark". Grade: P-mis for location; see B-ranking note on the misapplied benchmark.

6. **Etsy Commercial Access "effectively unobtainable", line 25 and 127.** Rests on one GitHub discussion (#1699) that this session cannot open (403 to curl; GitHub proxy scoped to session repos). One developer's thread does not support "effectively unobtainable" as a general finding. Grade: U for the thread, and the generalisation is overreach. Low stakes, since the report says Commercial Access is not needed for one shop.

7. **Promethean Research figures, lines 261 to 266.** Graded P from a "PDF read". I could not obtain the 2025 PDF. The public page https://prometheanresearch.com/digital-agency-industry-report/ is now the 2026 edition and reports different numbers: "Almost a third (29%) of the agencies in our latest survey charged between $175-199/hr"; agencies raising rates "28% in 2025 ... fell back to 20% in 2026"; "Only 8% or fewer rely on any single model exclusively". The 2026 teaser page adds "Agencies that reduced services grew 13% on average and posted 30% net margins". The 2025 quotes (36% at $175-199, 16% average net margin) may be accurate to the 2025 PDF, but a newer edition exists and the report should say which edition and refresh. Grade: U for the 2025 quotes; the 2026 figures above are P.

### A2. Claims graded higher than the evidence deserves

1. **Rejections of Amazon Merch and Redbubble rest on T and S figures.** Merch: the $2.44 / $4.88 / $5.27 tiers, the trailing 60-day window and "Coming Soon: Automated External Traffic from Merch Titans" are all on https://www.merchtitans.com/blog/amazon-merch-royalty-changes-june-2026 (Apr 15, 2026) exactly as quoted (grade P for "what Merch Titans says", T for the facts). Amazon's own page is login-walled. Redbubble's 50 percent Standard-tier fee and $150 cap are S (every Redbubble host 403s). Pass 1 said these must not be repeated as fact without the Merch dashboard announcement; 01 repeats them with caveats, then uses them as rejection grounds. A rejection that turns on a fee structure needs the fee page read in a browser first. See A4 for the bigger problem with these two rejections.

2. **"Demand is proven" for pick 1, line 283.** What is evidenced is agency rate benchmarks (Promethean) and the fact that SWAE has clients. Demand for the specific add-on packages ($250 to $500/month GBP, review-response, site-care bundles) is not evidenced anywhere in the report; the pricing for those packages is T from vendor pages (line 267). Say "most evidenced" and keep the falsifier (fewer than two clients take an add-on).

3. **Gumroad median $72/month, line 162.** Confirmed as quoted on https://insightraider.com/en/data/gumroad-statistics-2026 (dataset dated 2026-05-21; "Calculated via ratings count x average price x industry conversion multiplier"; "44% of all Gumroad products generated exactly $0"). The same page also says "The top 1% of Gumroad products (130 of 12,952 with sales) capture 77.3%", which implies only 12,952 of 146,271 products had any sales, which contradicts its own 44 percent zero-revenue figure. The dataset infers revenue from ratings, so a product with no ratings is scored $0. The report labels it T and "an estimate"; it should add that the source is internally inconsistent and biased toward $0 for unrated products. Correct the URL (the report's "insightraider.com (Gumroad statistics)" resolves to a 404 at the obvious paths; the real pages are /en/data/gumroad-statistics-2026 and /en/blog/best-sources-gumroad-statistics).

4. **Etsy AI policy and "Designed by a seller" strategy, lines 132 and 313.** All S. Pick 4 tells Chris to list AI items under a classification and disclosure sentence whose wording nobody in either pass has read on Etsy's page. Listing strategy on an S-grade policy is a suspension risk; the report says the pages need browser verification but still writes the loop as if settled.

5. **YouTube "generic or unoriginal templates" wording, line 223.** The report downgrades this to S saying it "was not in the fetched text". It is in the fetched text of https://support.google.com/youtube/answer/1311392: "AI-generated content made with generic or unoriginal templates giving the impression of mass production without adding the creator's original, authentic insights or perspective". Upgrade to P. This strengthens the rejection.

6. **Beehiiv "Starting August 6, 2026" status change, line 215.** Attributed to the Create post endpoint; the wording is on the support article (https://www.beehiiv.com/support/article/36759164012439), which is also in the read list. The API reference page only says "Available on the Pro and Enterprise plans". Attribution fix only.

### A3. Contradictions with pass 1 or with fetched primary pages

1. **KDP title cap.** Pass 1 established (Publishers Weekly, primary) a 3-new-titles-per-day cap since September 2023. Report 01 line 21 and 182 mention only a "two new titles per format per week since 2026-09-21 (T)" and omit the 2023 cap entirely. Add the 2023 cap as the P-grade fact and keep the 2026 per-week cap as unconfirmed.

2. **Ad spend floor.** Pass 1 item 7: Meta conversion campaigns need roughly 50 optimisation events per ad set per week to leave learning; $5/day does not get there. Report 01 pick 2 falsifier: "Zero orders in 60 days with 40+ products live and $300+ of ad or email reach". $300 over 60 days is $5/day. The kill criterion as written tests a campaign that cannot optimise, so a "fail" tells Chris nothing. Either raise the test budget (line 85 itself assumes $300 to $1,000 per month) or make the 60-day test email and organic only and say so.

3. **Margin stack.** Pass 1 item 6 asked for the full stack on one SKU. Line 83 gives base + shipping and stops: $24.99 minus ($12.25 + $4.95) = $7.79 "before card fees". It leaves unstated that this assumes the customer is not charged shipping, and omits the Shopify card fee ($0.72 + $0.30 = $1.02), the $39 plan amortised, returns and ad cost per order. On the stated assumptions net is about $6.77 before plan, ads and returns. Say it.

4. **Digital products below POD in the ranking.** Pass 1 Part 4 item 4: digital products are the lowest-friction, highest-gross-margin option. Report 01 ranks the Shopify POD store second and digital third, on the ground that POD is "the most automatable physical-product loop". Both face the same traffic problem; digital has no supplier API, no fulfilment, no reprints, no mis-print customer service, no Printful rate limits, and Chris has distribution for B2B digital. The report gives no reason physical should outrank digital for a hands-off goal. See Part C.

5. **Amazon's own Merch page.** Pass 1 fetched https://www.amazon.com/earn-with-amazon-merch/b?node=53635145011 (primary): application model, email on acceptance, monthly royalties, no acceptance rate. Report 01 line 106 says Amazon's pages are all login-walled. Cite the public page for the application model.

### A4. Internal inconsistencies and reasoning gaps

1. **Merch and Redbubble were rejected on the wrong basis.** Chris said he will batch-upload by hand. Report 01 rejects Merch for "no API", "no automation path", and Redbubble for "automation is explicitly banned" and the 30/day cap. None of those matters if Chris uploads. What the research should have evaluated, and did not: (a) Chris's time per upload and per batch, and the hourly value of that time against SWAE billing rates; (b) expected royalty at tier 10 (ten live designs; at the T-grade $2.44 Creator rate and any plausible sell-through, tier 10 is tens of dollars a month at best, which is the number that decides it); (c) the tier-up path and how long ten designs take to earn it; (d) Redbubble's actual fee schedule for a new account, read from the page, and the $150 cap's effect on volume; (e) what the agent contributes (research, design, copy, keyword packs, trademark screen, batch CSV) and whether that output is worth Chris's upload time; (f) ban exposure from design content rather than automation (AI-at-volume flags, IP strikes, forfeited royalties). Report 02 assumes both channels are in scope (line 22, phase 0, Builder outputs "upload pack for Merch/Redbubble"). The two reports disagree, and 01 is the one that needs rewriting: evaluate on the manual basis and either keep both as low-cost side channels for the same designs or reject them on economics, with the numbers.

2. **Etsy fee arithmetic, line 136.** "Combined 10 to 11% without Offsite Ads" is only true around $20 and above. 6.5% + 3% = 9.5% plus $0.45 fixed per order plus $0.20 per listing: on a $20 item that is 11.75%; on a $5 digital download it is 18.6%, and 33.6% with a 15% Offsite Ads attribution. Digital downloads are mostly low-ticket, so the pick 4 loop should quote the fee stack at $5 and $10, not just the percentage.

3. **Listing cadence benchmark misapplied, line 295.** "Target Printify's benchmark cadence of ten listings a week" comes from Etsy/eBay marketplace sellers, where listing count feeds discovery. On a standalone Shopify store nothing indexes new listings for buyers; cadence only matters once a traffic source exists. The loop should target designs per validated niche, not listings per week.

4. **Claude cost model, line 348 and 84.** Arithmetic checks: Sonnet 5.5 per product = (20K in x $2 + 5K out x $10) / 1M = $0.09; Opus 5.5 = $0.18. Prices confirmed on https://platform.claude.com/docs/en/about-claude/pricing (Opus 5.5 $4/$20, Sonnet 5.5 $2/$10, Haiku 4.5 $1/$5, Fable 5.1 $10/$50). The model counts one context load per product; a Claude Code run bills context on every turn (cached reads at 0.1x, 0.05x on Opus 5.5) and each fresh routine session pays a cache write. The per-product number is a floor; the "$30 to $150 per loop per month" range is plausible only because it is wide. Consistent with 02's figures in direction, see Part B.

5. **"Five options survive", line 16, and the hands-off goal.** The executive summary lists pick 1 first without saying what line 283 says plainly: it is the least passive option because every client-visible artifact needs Chris's sign-off. Chris's brief is hands-off. The honest framing is in the body; the summary, which is what gets read, omits it. Add one sentence to the summary and define the ranking metric (Chris hours per month per dollar of expected contribution margin), then rank on it. By that metric pick 3 (digital, B2B, existing distribution) likely rises and pick 1 is explicitly a "fastest cash, least passive" entry.

6. **Trademark screening, line 57 and 295.** "Trademark screening via USPTO search in browser" (line 57) and "trademark-screen (reverse-image search per Printful's own advice)" (line 295) are different things. Reverse image search finds visual copies and character references; it does not find word marks. Keep both steps and name them separately.

7. **Line 12 process note** says the research subagent could not run a skeptic. Fine, but the "two flags" from the parent's skeptic are not listed anywhere a reader can check. Minor.

### A5. Overreach that would embarrass Chris if repeated

- Quoting a Shopify terms clause that is not in the terms (A1.1).
- Telling a client or a prospect that agencies "earn an average net margin of about 16%" from a 2025 edition when the 2026 edition is public and says different things (A1.7).
- Stating Etsy's AI classification rules from search snippets while building a listing strategy on them (A2.4).
- "AI designs can be copied freely" with a citation that does not say it (A1.3).
- Any of the Merch royalty numbers without "reported by a tool vendor; Amazon's page not read".

### A6. What in report 01 is confirmed and survives (grade P unless noted)

- Printful API limits and the Products-API limitation; Printful plans ($0; Growth $24.99/month, free at $12K/year, up to 33% off); Printful AI-art guidance quotes; Printful survey of 68 store owners (29% marketing strategy, 21% audience, 15% designs, 13% billing/taxes); Printful margin table (tees 45 to 55% gross, 20 to 35% net; "significantly lower than the gross figure suggests").
- Printify API (600/min, catalog 100/min, publish 200 per 30 min, 5% error ceiling, "additional daily limit" unstated); Printify API Terms quotes; Printify tiers ($0 to $100+ at 0 to 6 months; $1,000 to $3,000+ at 6 to 18; $10,000 to $80,000+ at 18+, vendor claim); 165 days to first $1,000; ten listings a week on Etsy/eBay; 67 listings before $1,000 GMV; Megan Heckman "100 designs ... $100 Facebook ad budget" anecdote.
- Shopify pricing (Basic $39 monthly, $29 yearly, 2.9% + 30c, 2% third-party fee); app revenue share (0% to $1M lifetime, 15% above, 2.9% processing, $19 registration, $20M/$100M thresholds); the data-collection clause.
- Etsy Seller App tier (eligibility, "approved within minutes", "scoped only to your registered shop", "Commercial use: Not permitted"); publish flow (`createDraftListing`, `updateListing` state active, `type` download + `uploadListingFile`); Etsy Q4/FY2025 metrics (5.6M sellers, 86.5M buyers, $121 GMS per buyer, $10,460.7M marketplace GMS).
- Gumroad 10% + $0.50 direct, 30% Discover, MoR since 2025-01-01; prohibited list revised 2026-09-16 with the "AI services" and PLR lines; terms clauses on scraping and unsubstantiated earnings claims.
- Lemon Squeezy 5% + 50c, no monthly, "2026 Update: Lemon Squeezy + Stripe Managed Payments"; Whop identity verification, no lifetime products, chargeback suspension "without prior notice"; Notion 8% + 40c, waitlist, biweekly payouts, $20 minimum, 14-day hold.
- KDP AI-generated vs AI-assisted definitions; low-content rules; paperback 50%/60% at $9.98/$9.99 with the $15 / 333-page / $4.00 example.
- YouTube July 15, 2025 inauthentic-content update and all quoted lines (including the AI-templates line, upgrade to P); YPP thresholds and "standard review process"; API default quota and audit requirement; private-mode rule (on revision_history).
- TikTok unaudited-client private restriction and error code. Shutterstock July 16, 2025 ban. Unity 1.6 AI disclosure rules and mass-produced clause; Fab 88% and $100 threshold.
- Chrome Web Store duplicate-functionality and single-purpose rules; WordPress Plugins Team 2025 figures (330/week, 12,713 reviewed, 69.5% approved, AI line); Google Play 12 testers / 14 days for accounts after 2023-11-13.
- beehiiv Free / Lite $49 / Pro $95 yearly, 0% take on paid subs minus Stripe 2.9% + 30c, "Avg. $39/mo" ad figure (vendor); Send API on Pro/Enterprise; August 6, 2026 status change.
- weekonelabs (https://weekonelabs.com/blog/shopify-app-revenue-benchmarks-2026): "roughly 18,000 listed apps", "500-800 new apps added every month", "The median listed app earns under $1,000 per month", written by a Shopify app founder (T, quoted accurately).
- Picks that survive: pick 1 (with the hands-off caveat moved into the summary); pick 3 (strongest on evidence and on the hands-off metric); pick 4 (conditional on reading Etsy's Creativity Standards and fee page in a browser first); pick 5 as a channel. Pick 2 survives as a test, not as number two. Rejections that survive: KDP, YouTube, TikTok, Shutterstock/Pond5/Envato, Freepik-class stock on economics, Unity/Fab, mobile apps with ads, Canva Creators for the window, Lemon Squeezy as a platform to build on. Deferral of micro-SaaS/plugins survives. Merch and Redbubble rejections do not survive as written (A4.1).

---

## Part B: report 02 (agent office architecture)

### B1. Claims unsupported, misattributed, or unverifiable

1. **"Claude Projects ... thread caps are instructions, not enforced" (line 84).** Not found on https://code.claude.com/docs/en/claude-projects. The page describes an enforced turn limit ("Reached the turn limit": `CLAUDE_CODE_MAX_TURNS`) and advises asking Claude to "run a few at a time". Grade: U; soften or cite the sentence.

2. **"Routines on the desktop app also raise desktop notifications for project threads; cloud routines do not push to the phone" (line 240).** Not found on the Projects or Routines pages. Grade: U. The design conclusion (use the dashboard notification) still holds.

3. **"cloud sessions summarise web search results rather than passing raw pages (primary, fetched: secure-deployment doc)" (line 200).** The sentence "Web search summarization: Search results are summarized rather than passing raw content directly into the context" is on https://code.claude.com/docs/en/agent-sdk/secure-deployment as a general Claude Code protection, not a cloud-session statement. Minor; reword to "Claude Code".

4. **Workflows "1.5M projected tokens" Large-workflow threshold (lines 167 and 342).** The fetched workflows page confirms 16 concurrent agents by default, 4,096 items per call, 1,000 agents per run, `Date.now()`/`Math.random()` throwing, and a "Large workflow" warning, but the 25-agent / 1.5M-token figures were not in the extracted text. Grade: U for the numbers.

5. **Project Deal page "404'd on fetch" (line 328).** https://www.anthropic.com/features/project-deal returns 200 today and contains the quoted facts: 69 employees, 186 deals, "just over $4,000", Opus 4.5 vs Haiku 4.5 with "people represented by 'smarter' models got objectively better outcomes". Upgrade to P and drop the enterprisedna.co fallback. /research/project-deal is still 404.

6. **Shopify Basic "roughly $39 per month (secondary, widely reported, verify in-admin)" (line 303).** Report 01 has this at P from shopify.com/pricing ($39 monthly, $29 yearly). The two reports should agree; cite the pricing page.

7. **Automaton Agency and technically.dev graded "primary (fetched by curl)".** Both are self-published case studies (one by an agency selling agent services, one by a solo operator). Every quoted figure is present on the pages ($1,493 of $1,500; 243 leads; $6.14 vs $2.50 target; Day 16; $1.29 CPL on day 12; "by its own definition it's a failure"; 25 firms, about 96 sends, 0 sales, under $100 spent; "Last updated Aug 25, 2026"). Grade them P for the quote and self-report for the evidence; "primary" overstates what a vendor's own teardown proves.

8. **MAST (line 37).** The abstract confirms "1600+ annotated traces collected across 7 popular MAS frameworks" (MAST-Data), the taxonomy built from 150 traces, 14 modes, 3 categories, kappa 0.88. Fine; the report's own caveat on the percentage splits stands.

### B2. Facts confirmed on the primary pages (survive)

- Routines (https://code.claude.com/docs/en/routines): minimum interval one hour; on-the-hour starts can be late, pick 9:07; "Scheduled runs, including one-off runs: 100 per hour, your account"; Run now / API fires / one-off re-arm 30 per hour per routine; API fires 100 per hour per account; usage credits allow metered overage, otherwise runs are rejected; GitHub disconnect skips runs up to 72 hours; "Each repository you add is cloned on every run"; "Claude pushes its work to a branch prefixed with claude/"; rulesets apply to the connected GitHub access "so a rule that access can bypass doesn't block a run's push"; "Claude can use every tool from an included connector, including writes, without asking for permission during a run"; "A green status ... does not mean the task in your prompt succeeded"; connectors reach services through Anthropic's servers; fired prompt is the assigned task; "Breaking changes ship behind new dated beta header versions, and the two most recent previous header versions continue to work". The report's reading of the two pages disagreeing on the beta header is accurate: the API reference says the endpoint "accepts requests with and without it".
- Fire endpoint (https://platform.claude.com/docs/en/api/claude-code/routines-fire): no idempotency key ("If a webhook caller retries, the endpoint creates multiple sessions"); 65,536-character `text`; 400 when paused; 429 with Retry-After; token "One routine only; no read access"; billed to subscription usage.
- Pricing: model rates as listed; cache read 0.1x (0.05x Opus 5.5, 0.025x Fable 5.1); 5-minute write 1.25x, 1-hour 2x; web search $10 per 1,000; "approximately 30% more tokens" for Claude 4.7+ tokenizer; Managed Agents "$0.08 per session-hour", worked example "Claude Opus 5" 50k/15k one hour = $0.705.
- Managed Agents: `max_list_cost` in US cents as a string, enforced between model requests, `budget_reached`, create-only; `auto` "is not a human checkpoint"; intent read only from `user.message`; jitter up to 15% capped at 9 minutes; 1,000 deployments per org; run error types; `paused_reason`.
- Cloud sessions and environments: VM reclaimed after inactivity, including while waiting on a connector sign-in; API credentials on Pro/Max attached by the agent proxy to listed hosts; repo `.claude/settings.json`, `.claude/skills/`, `.claude/agents/` load in a one-repo session; user-level `~/.claude` does not.
- Hooks: `UserPromptSubmit` with top-level `"decision": "block"`; PreToolUse `permissionDecision` deny; exit code 2.
- Agent SDK hosting: "roughly $0.05 per hour" container, "1 GiB RAM, 5 GiB disk, and 1 CPU per agent", `maxTurns`, `SessionStore`, OTEL.
- arXiv 2609.01660 (all quoted numbers present: nine models, 10,664 trajectories, sixteen steps, logit slope -0.69 vs -0.44, 0.42 and 0.24); arXiv 2603.29231 (10 models, 23,392 episodes, 396 tasks, meltdown up to 19%, memory scaffolds "universally hurt"); Anthropic multi-agent (4x, 15x, 80% of variance); measuring agent autonomy (45 s median, over 40% auto-approve, 9% interrupts, "more than twice as often"); Project Vend 1 and 2 (tungsten, hallucinated Venmo account, onion contract, $10/hour below minimum wage, "faulty voting procedure", WSJ newsroom red-team, "weeks with negative profit margin were largely eliminated", Seymour authorised lenient treatment "about eight times as often as it denied"). The "profitable across three cities" wording is not on the page; it says "Another important number is: three" about locations and shows profit "combined across all locations". The "$1,000 into the red" WSJ figure is from Slashdot (S) as the report says.
- Klaviyo deliverability page: 0.1% / 0.3% Gmail thresholds, account disable on abuse patterns, new accounts flagged on first send to an uploaded list, affiliate marketing not allowed.
- Shopify versioning: quarterly releases, 12 months support, nine months overlap, fall-forward to oldest accessible stable version, 2026-10 latest stable on 2026-10-05. The "17:00 UTC" detail was not in the extracted text (U).
- Computer-use doc: both quoted sentences present.
- Design choices that survive on this evidence: no always-on orchestrator; one narrow routine per role; all state on a board plus the repo; writes gated by hooks committed in the repo; dry-run week per role; dead-letter after two failures; ads human-approved; PR-gated prompt and skill changes with evals; Managed Agents as the phase-2 candidate for money-touching roles because it is the only option with a platform-enforced per-session dollar cap.

### B3. Internal inconsistencies and arithmetic

1. **Phase cost vs roster.** Section 7 sums the seven-role roster to "roughly $65 per month" and labels it "Phase 0 to 1 total". Section 9 and summary item 12 put phase 1 at $90 to $180. The roster includes Researcher, Email and 20 builds, which is the phase 1 shape. Pick one number per phase. (Roster arithmetic itself is right: 12 + 5 + 12 + 17 + 8 + 9 + 3 = $66 at the stated token counts.)

2. **Ops cadence.** "Every 4 hours during 06:00 to 22:00" is five runs a day (06, 10, 14, 18, 22), 150 a month, not the 120 used in the roster. Summary item 11 says "every 4 to 6 hours". Pick one.

3. **Etsy.** Line 22, section 1.3, section 10 and Appendix B treat Etsy as off-limits for automation ("No Etsy ... API path that permits automation; packs only"; "If Etsy is ever added"). Report 01 establishes at P that Etsy's Seller App tier permits automating your own shop, including publish. 02 is wrong on this point and contradicts 01.

4. **Merch and Redbubble.** 02 keeps them in scope (packs, manual upload); 01 rejects them. See A4.1; whichever way 01 lands, 02 must match.

5. **Scope omits pick 1.** 02's scope line names POD, digital products and upload packs. Report 01's number-one pick is productized services, whose loop (01 line 285: a weekly routine per client pulling Semrush/GSC/GA, drafting GBP posts and review responses, queuing dashboard comments) is not designed anywhere in 02. Either add the client-services roles and their guards (posting hours, client-visible approvals, de-AI rules) or state that 02 covers picks 2 to 4 only.

6. **Etsy Creativity Standards (line 329).** "Templated designs removed from the allowed list retroactively; thousands of shops hit; bulk uncurated AI listings suspended" is a search snippet from a POD vendor blog (listadum). 01's S-grade reading of Etsy's own page says AI is allowed with disclosure. Downgrade 02's line to "vendor blog, unverified" or drop it.

7. **Deny-list gaps (section 5.8).** The list names `mcp__Shopify__delete*`, but the Shopify MCP in this session has no delete tool; destructive paths are `graphql_mutation` (covered by the "contains Delete" rule, which misses `productUnpublish`, `inventorySet`, `discountCreate` and archive-type mutations) and `bulk-update-product-status` (not listed). Also not listed for phase 0: `mcp__Klaviyo__send_campaign`, `mcp__Gmail__send_message`, `mcp__Gmail__reply`, `mcp__Gmail__forward`, `mcp__SWAE_Dashboard__archive-*`, `mcp__SWAE_Dashboard__bulk-update-tasks-tool`, `mcp__SWAE_Dashboard__comment-on-task-tool` on any client-visible task (always notifies). The hook list must be generated from the live tool names of the connectors attached to the routine, not written from memory.

8. **Haiku on customer text.** Section 7 argues against a customer-service role, then line 265 has Ops (Haiku 4.5) "draft replies to flagged messages". Section 10 cites Project Deal to say "do not put Haiku on anything adversarial". Customer messages are the injection surface the report itself names. Move message drafting to a Sonnet role with write tools denied, or leave it to Chris at phase 0.

### B4. Architecture challenge

**Is Routines-per-role workable given one-hour minimum, fresh sessions, and full-write connectors?**

- One-hour minimum: not a constraint for this design; nothing here needs sub-hour latency. Survives.
- Fresh session every run: the report treats it as a feature and is right that state must live on the board. Two costs it does not price: (a) every run pays a full cache write of the system prompt, CLAUDE.md, handbook and the tool definitions of every attached connector (this session alone exposes several hundred MCP tools; a routine with the dashboard, Shopify, Klaviyo, Drive and GitHub attached will carry tens of thousands of tokens of schemas before work starts), and (b) every run re-establishes connector auth; the cloud-sessions doc says a session waiting on an MCP sign-in counts as inactive and can expire during the wait. A connector whose token lapses (Adobe, Klaviyo, Shopify) stalls the role silently until the next run. Add "connector auth check at session start, write `connector_down` and exit" to every role, and a weekly manual check that all connectors are signed in. The report has the health check (6.1) but not the auth-expiry mechanism.
- Full write access: the mitigation is hooks in the repo's `.claude/settings.json`, which the cloud-sessions doc confirms load in a one-repo session. Two untested assumptions: (a) that `UserPromptSubmit` fires for a routine-delivered prompt (the routines doc says the saved prompt is delivered as the assigned task; the hooks doc describes the event for user input; whether it fires here is not documented); (b) that hook scripts in a cloned repo run before any tool call on Anthropic-managed infrastructure. Both are one-afternoon tests; run them before phase 0 and record the result in the handbook. If (a) fails, move the KILL check into a `SessionStart` hook that exits non-zero, or into a `PreToolUse` deny-all, and say which worked.
- Branch protection: the routines doc says rulesets apply to the GitHub access Chris connected, "so a rule that access can bypass doesn't block a run's push". If Chris's GitHub user is an admin with bypass, the routine can push to `main`. The PR gate only holds if the ruleset on `main` has no bypass actors, including Chris. State that as a setup step with a test.
- The Ops-fires-Builder chain (6.3): a routine run calling another routine's `/fire` endpoint needs that routine's bearer token available inside the Ops session. The API-credential feature attaches keys to listed hosts by proxy; whether `api.anthropic.com` can be listed, and whether the environment's network policy permits the call, is not established in the report. The simpler design: Builder and QA run hourly on a schedule and claim open tasks from the board (the fire-as-claim idea in reverse). Latency becomes up to an hour, which the design already tolerates, and no tokens move between routines. Recommend this for phase 0 and keep API firing for phase 1 if measured latency matters.
- Subagent/workflow fan-out inside a run: fine, but the report's own cited source says multi-agent runs use about 15x chat tokens; the cost model applies no multiplier for QA fan-out.

**Is $65 per month credible?**

- Arithmetic at the stated token counts is right ($66). The token counts are the problem. They count one context load per run. A Claude Code run bills context on every turn; with caching that is roughly (turns x context x cache-read rate) plus one cache write per fresh session plus outputs. Worked check for the Builder on Sonnet 5.5: 30 turns x 80k context x $0.20/M (cache read) = $0.48, plus one 80k cache write at $2.50/M = $0.20, plus 25k output at $10/M = $0.25, about $0.93 per run, 20 runs = $19. That is close to the roster's $17, so the per-role numbers are defensible as a floor when caching works. Across 190 fresh sessions a month the cache writes alone are $30 to $50 on Sonnet-class runs. A realistic phase 1 band is $100 to $250 at list rates, not $65, and the report should present $65 as the floor it is.
- The sentence "On a Max subscription this sits inside plan usage" has no source. Nothing fetched states what volume of routine runs a Max plan absorbs per week; the routines doc only says runs draw down the same usage and are rejected at the limit without usage credits. The right statement: "unknown until measured; run phase 0 for one week, read claude.ai/settings/usage, then size the schedule". The report says to measure (section 9) but still publishes the plan-fit claim.
- Adobe generative credits for the Designer are a separate metered cost not in any table (01 line 348 mentions it; 02 does not).

**Is the Laravel ledger the smallest thing that works?**

- No. For phase 0 the office needs a queue, a run log, a metrics series and an idempotency check. Already available without a schema change or a deploy: the dashboard's existing tasks and comments (queue and run log, with attachments for the per-run JSONL), the Google Drive connector (a Sheet or CSV as the metrics series, single writer = Ops), and the Shopify-side idempotency the report already specifies (deterministic handle plus `office.task_id` metafield, checked before create). The report rejects monday.com and Notion for adding a vendor, then adds three tables, five MCP tools and a lease protocol to a production Laravel app under Gate 1, test-exclusion and deploy rules, for a system whose roles run on non-overlapping schedules. The lease is solving a race the schedule design already avoids. Build the Laravel module when phase 1 shows two writers on one record or when the Sheet becomes the bottleneck, and say that in the plan.
- The one thing a spreadsheet cannot do well is "list open failures for the Ops role"; a dashboard task per failure with a `dead-letter` tag covers it.

### B5. Overreach that would embarrass Chris if acted on with money

- Starting routines with every connector attached and relying on a deny-list written from memory (B3.7).
- Letting a routine push to `main` because the ruleset allows admin bypass (B4).
- Publishing "$65 per month" or "fits in the Max plan" to anyone before a measured week (B4).
- Treating "Etsy cannot be automated" (02) or "Etsy can be automated as Designed by a seller" (01) as settled; the first is wrong on the Seller App, the second is unread policy.

---

## Part C: ranking logic

- Chris's stated goal is hands-off. Report 01 ranks the least hands-off option first and says so only in the body (line 283). The executive summary (line 16) must carry that sentence, and the report should state the metric it ranks on. A defensible metric: expected contribution margin at 90 days divided by Chris hours per month, with a floor on evidence grade. On that metric, pick 1 is "fastest cash, highest Chris time", pick 3 is "lowest Chris time with existing distribution", pick 2 is "most operational surface for the same traffic problem".
- Pick 2 above pick 3 is not justified in the text. Physical products add a supplier, shipping, reprints, mis-print support, rate limits and a 20 to 35 percent net band (Printful) against a digital product with no COGS and SWAE distribution. Swap them or give the reason.
- Pick 4 depends on S-grade Etsy policy. Keep it fourth but make the browser read a precondition, not a footnote.
- Merch and Redbubble: re-evaluate on the manual-upload basis (A4.1) before they appear in the rejected list.

---

## Part D: what survives, in one place

Report 01: every platform fact listed in A6 at grade P; the rejections of KDP, YouTube, TikTok, Shutterstock-class stock, Unity/Fab, mobile ads apps, Canva (window), Lemon Squeezy; the deferral of micro-SaaS and plugins; picks 1, 3, 4 (conditional), 5 (channel); pick 2 as a test. The cost-per-product arithmetic. The grifter-check framing.

Report 02: every platform fact listed in B2; the choice of scheduled narrow roles over an always-on orchestrator; board-plus-repo state; hooks as the enforcement layer; dry-run; dead-letter; phased gates with measured criteria; human-approved ad spend through phase 2; PR-gated prompts; Managed Agents as the phase-2 candidate for money-touching roles. The long-horizon reliability evidence as quoted.

---

## Part E: prioritized fix list

Items are ordered by how much a reader would be misled or lose money. Each gives file, location, correction and source.

1. **01, line 72.** Remove the "not bypass Shopify API restrictions ... automating administrative functions of the Merchant Store Admin" quote or re-source it; it is not in https://www.shopify.com/legal/api-terms (fetched 2026-10-05) nor https://www.shopify.com/partners/terms. Keep the data-collection quote. Grade the admin-automation point as inference.

2. **01, sections 2 and 3, lines 93 to 117 and 329 to 330.** Rewrite the Merch and Redbubble evaluations on the manual-upload basis Chris stated: Chris time per batch, tier-10 ceiling using the T-grade $2.44 Creator rate (https://www.merchtitans.com/blog/amazon-merch-royalty-changes-june-2026, Apr 15, 2026, vendor) with "Amazon's page unread" stated, Redbubble fee schedule read in a browser (https://blog.redbubble.com/2025/08/artist-account-tiers-and-fees/, 403 here), ban exposure from content rather than automation. Then accept as side channels or reject on numbers. Make 02 line 22, phase 0 and Appendix B match the outcome.

3. **02, line 22, section 1.3, section 10 Etsy row, Appendix B.** Replace "No Etsy ... API path that permits automation" with 01's P-grade finding: Seller App tier, own shop only, publish via `createDraftListing` then `updateListing` state active (https://developers.etsy.com/documentation/ and /documentation/tutorials/listings). Keep the AI-disclosure caution at S until the Etsy page is read.

4. **01, executive summary line 16 and Ranking section.** Add that pick 1 is the least hands-off option, name the ranking metric, and either swap picks 2 and 3 or justify POD over digital in writing. Source for digital's lower friction: 01's own platform facts (no COGS, Gumroad/Shopify Digital Downloads publish by tool) and pass 1 Part 4 item 4.

5. **02, section 7 (line 259), section 9 table, summary item 12.** Present $65 as a floor; add cache-write cost per fresh session and the 15x multi-agent multiplier for any fan-out; replace "fits inside plan usage" with "unmeasured; measure one week at claude.ai/settings/usage". Source: https://platform.claude.com/docs/en/about-claude/pricing (cache write 1.25x, reads 0.1x/0.05x) and https://www.anthropic.com/engineering/multi-agent-research-system (4x, 15x). Reconcile the roster's "Phase 0 to 1 total" with the phase 1 band.

6. **02, section 3.3 item 2 and Appendix B.** Replace the phase-0 Laravel office module with existing dashboard tasks and comments plus a Drive Sheet written only by Ops; defer the three-table module and lease protocol to a phase 1 trigger. No external source needed; this is the smallest-change rule in Chris's code standards.

7. **02, section 5.4 and 5.8.** Add the two tests (does `UserPromptSubmit` fire on a routine prompt; do repo hooks run before the first tool call on managed infrastructure) as phase-0 preconditions with recorded results; add a `main` ruleset with no bypass actors including Chris (source: routines doc, "a rule that access can bypass doesn't block a run's push"); regenerate the deny-list from live tool names and add `bulk-update-product-status`, `send_campaign`, Gmail send/reply/forward, dashboard archive/bulk tools, and mutation-name matching beyond "Delete".

8. **02, section 6.3.** Replace Ops-fires-Builder with scheduled hourly Builder/QA that claim open tasks from the board, or document how the fire token reaches the Ops session (environment API credential for api.anthropic.com, network policy) and test it. Source: https://code.claude.com/docs/en/cloud-environments (credentials attached by host) and the fire reference (token scoped to one routine).

9. **01, lines 261 to 266.** Label the Promethean quotes as the 2025 edition, fetch the 2026 edition (https://prometheanresearch.com/digital-agency-industry-report/: 29% at $175-199/hr; 28% raised rates in 2025, 20% in 2026; https://prometheanresearch.com/2026-state-of-digital-services-digital-agency-industry-research/: agencies that narrowed services grew 13% and posted 30% net margins) and quote the current figures.

10. **01, pick 2 falsifiers, line 299.** Replace "$300+ of ad or email reach" with either an email/organic-only test or an ad budget that can exit Meta's learning phase (pass 1 item 7; cite Meta's learning-phase help page when it is read). As written the kill test cannot distinguish a dead niche from an under-funded ad set.

11. **01, line 89.** Re-source the AI-copyright claim to the US Copyright Office's own guidance and soften "copied freely" to "the AI-generated portion has no copyright; trademark and human-authored elements still apply". The Printful post does not say this.

12. **01, line 136 and pick 4.** Give the Etsy fee stack at $5, $10 and $20 price points (9.5% plus $0.45 per order plus $0.20 per listing; 18.6% at $5 without Offsite Ads). Fees remain T until https://www.etsy.com/legal/fees is read.

13. **01, line 83.** State the free-shipping assumption and add the Shopify card fee: $24.99 tee nets about $6.77 before plan amortisation, ads and returns on the T-grade Bella+Canvas cost.

14. **01, lines 21 and 182.** Add the September 2023 three-titles-per-day KDP cap (Publishers Weekly, Sep 18, 2023, primary in pass 1) and keep the 2026 per-week cap as T.

15. **01, line 223.** Upgrade the YouTube "generic or unoriginal templates" wording to P; it is on https://support.google.com/youtube/answer/1311392.

16. **01, line 227; line 59; line 77; line 215.** Attribution fixes: private-mode rule to developers.google.com/youtube/v3/revision_history (July 28, 2020 entry); Printful Sync description marked U until found in the spec; 165 days / ten listings / 67 listings to printify.com/blog/print-on-demand-statistics/ with the "Etsy and eBay" qualifier; beehiiv August 6, 2026 change to the support article. Also line 162: InsightRaider URL is https://insightraider.com/en/data/gumroad-statistics-2026 and the source contradicts itself (12,952 with sales vs 44% at $0).

17. **01, line 295.** Drop "Target Printify's benchmark cadence of ten listings a week" for a standalone store; it is a marketplace figure.

18. **02, lines 84, 240, 167/342, 303, 328.** Mark the Projects "thread caps" and desktop-notification sentences U; mark the 25-agent / 1.5M workflow threshold U; cite shopify.com/pricing at P for $39; upgrade Project Deal to P at https://www.anthropic.com/features/project-deal (page is live).

19. **02, section 7 Ops row and section 6.3.** Fix the Ops run count (five per day on the stated window, 150 per month) and pick one cadence across the summary, roster and section 6.

20. **02, line 265.** Move customer-message drafting off Haiku, or off the office entirely at phase 0, consistent with the report's own Project Deal lesson and injection analysis.

21. **02, line 326 and 327.** Regrade the Automaton Agency and technically.dev cases as self-published reports (quotes verified) rather than "primary" evidence.

22. **01, line 25 and 127.** Regrade "Commercial Access is effectively unobtainable" to "one developer reports repeated denials (GitHub discussion #1699, not opened in this pass)".

23. **Both reports.** Add a line that Adobe Firefly generative credits are a metered cost outside the token tables.
