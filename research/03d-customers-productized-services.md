# Who buys fixed-price, agent-delivered marketing services: buyer segments, gaps and a catalogue

Prepared for Chris DeWitt, SWAE Marketing. Research date 2026-10-05. Every URL below was accessed 2026-10-05 unless marked otherwise. Follows `01-income-options.md`, which ranked productized recurring services through SWAE as pick 1.

## How to read the evidence grades

- **P (primary, fetched):** the page or data file was fetched in full through the session proxy and the number was read from it. Fetched text is in the session scratchpad under `pages/`. Census County Business Patterns (CBP) numbers were parsed from the Bureau's own bulk files (`cbp22us.txt`, `cbp22st.txt`).
- **S (search snippet):** a search result stated the fact and the page itself returned a block, a JavaScript shell or a redirect to every fetch. Reliable for wording, not for context.
- **T (secondary):** a third-party page is the only readable source. Indicative until re-verified.
- **Tooling note:** WebSearch hit its 200-call session cap partway through, and the Firecrawl connector returned "low on credits" on every call. Later gaps were filled with direct `curl` fetches only. DuckDuckGo's HTML endpoint was tried as a fallback and the proxy reset the connection. Pages that stayed unreadable are listed in section 6.
- **Process note:** the global rule to run a skeptic agent in parallel could not be followed inside this subagent (no Agent tool). The parent session should run one against sections 1 and 4 before anything here becomes a price list.

## Executive summary

1. The buyers who overpay most, relative to what they get, are small residential trades: roofing, siding and gutters, plumbing and HVAC, electrical, landscaping, remodeling. CBP 2022 counts 24,532 roofing, 9,191 siding, 109,601 plumbing/HVAC, 81,842 electrical, 117,109 landscaping and 133,345 residential remodeling employer establishments, and in every one of those codes 60 to 80 percent have fewer than five employees (P). These are the firms that bought HomeAdvisor leads at $287.99 a year plus a per-lead fee and got 110,372 FTC refund checks (P), that answer Pointbreak-style "your Google listing will be marked permanently closed" robocalls (P), and that sign 12-month Hibu, Thryv or Scorpion contracts they then cannot cancel (S, BBB complaint counts).
2. The trades' own associations say spend is low and the return on retention marketing is high. ACCA's Contractor of the Future study: contractors spending 12 percent or more of revenue on marketing net 9 percent profit versus 5 percent for those under 12 percent (P); ACCA's budget guidance says database marketing to lapsed customers returns $8 to $12 per dollar versus $3 to $4 for new-customer acquisition, "yet most contractors spend 70-80% of budgets chasing new customers" (P). That is the single clearest unserved gap: nobody sells a $200-a-month lapsed-customer program to a six-person HVAC shop.
3. Reviews and the Google Business Profile are where the money is being lost. BrightLocal's 2026 consumer survey: 89 percent of consumers expect owners to respond to reviews, 19 percent expect a same-day reply, 42 percent are unlikely to use a business that ignores reviews, and templated replies put off 50 percent (P). Whitespark's 2026 ranking-factors survey says review and behavioural signals grew in importance this year (P). Meanwhile GBP suspensions are rising: a 350-location franchise reports "nearly every new listing we create has been suspended almost immediately" with appeals stuck for three months (P, Local Search Forum), and Sterling Sky's suspension tickets doubled in the first half of 2024 (S).
4. Price bands are well documented and sit where an agent-delivered service with light QA is profitable: GBP management $125 to $400 per profile per month (P, Merchynt), $99/$249/$399 per location with no contract (P, GMB Gorilla), review-platform software $249 to $449 per location on 12-month terms (T, Podium and Birdeye), WordPress care $39 to $359 per site (P/S), small-business social packages $399 to $1,550 for 4 to 12 posts (P/S). Agencies bill $175 to $249 an hour (P, Promethean).
5. The best-fit catalogue is five offers that batch into one weekly review for Chris: a per-location GBP service, a review desk, a lapsed-customer email/SMS program, a local-pages-plus-site-care plan, and a quarterly seasonal campaign kit. Section 4 gives inputs, outputs, acceptance checks, QA minutes and prices for each. Target is 45 to 75 minutes of Chris's time per client per month on a two-offer bundle at $350 to $600.
6. Churn expectations: retainer agencies report 18 percent annual churn and 56-month client lifespans, agencies with 1 to 10 employees 32 percent (T, Focus Digital); 42 percent of agency leaders report average retainer tenure above two years and about a quarter report under one year (P, Promethean); 62 percent say onboarding access delays hurt client confidence (P, Promethean). Plan for a quarter of clients leaving inside 12 months and for onboarding (logins, GBP ownership, CRM export) being the point where most of them are lost.
7. Two segments with large counts rank lower than their size suggests: full-service restaurants (257,282 establishments, marketing a top-three pain point for 16 percent of operators, P, Toast) because budgets and survival rates are thin, and dentists (136,140 establishments, P) because Birdeye, Podium and vertical agencies already saturate them.

---

## 1. Ranked buyer segments

Counts are 2022 County Business Patterns employer establishments, parsed from the Census bulk files (P). CBP excludes firms with no employees; the SBA counts 28,477,518 nonemployer firms, 81.9 percent of all US firms (P, SBA Advocacy FAQ), so the true number of one-person trades is several times the CBP figure. Montana counts are from the state file (P) and are included because SWAE's current clients are there; nothing in the model limits sales to Montana.

Source for all counts: https://www2.census.gov/programs-surveys/cbp/datasets/2022/cbp22us.zip and `cbp22st.zip`, parsed 2026-10-05 (P). SBA FAQ: https://advocacy.sba.gov/wp-content/uploads/2024/12/Frequently-Asked-Questions-About-Small-Business_2024-508.pdf (P).

### Rank 1. Exterior residential trades with a season: roofing, siding and gutters, painting, awnings

- **Counts (P):** roofing 24,532 establishments (15,808 under five employees; Montana 152); siding contractors, the NAICS code that holds gutter installers, 9,191 (6,928 under five; Montana 110); painting 37,963 (28,292 under five; Montana 282). Awning installers have no NAICS of their own; they sit in 238390 "other building finishing" (7,960) and 238190 (6,277). Roofing annual payroll $13.3 billion, about $542,000 per establishment (P, CBP).
- **Revenue band:** roofing guidance treats "under five million a year" as the small tier and says those firms "usually spend seven to eight percent of revenue" on marketing (S, useproline.com via search; the page itself was fetched but the figure is on a sister article). Remodelers in the same housing stock report median revenue $1.7 million with five employees (P, NAHB/Eye on Housing, https://eyeonhousing.org/2025/09/who-are-nahb-remodelers/).
- **What they buy now:** pay-per-lead marketplaces and Local Services Ads. Roofing search cost per lead is quoted at $85 to $120 (T, WebFX) and $70 average with a $35 to $150 range (T, Watson); marketplace leads at $75 to $150 shared among several contractors (T, improveandgrow.com). Angi Leads: $15 to $85 per lead, a one-year contract with a 35 percent early-termination fee (T, hookagency.com/blog/angi-leads-reviews/).
- **What they overpay for or get scammed on:** the HomeAdvisor case is the primary record. HomeAdvisor "recruits service providers, such as general contractors and lawn care businesses", charges "an annual membership fee of $287.99, in addition to a separate fee for each lead", told them leads "result in jobs at rates much higher than it can substantiate", and resold affiliate leads "that did not come from HomeAdvisor's website" (P, https://www.ftc.gov/news-events/news/press-releases/2022/03/ftc-charges-homeadvisor-inc-cheating-businesses-including-small-businesses-seeking-leads-home). The FTC order was up to $7.2 million (P, https://www.ftc.gov/news-events/news/press-releases/2023/01/ftc-order-requires-homeadvisor-pay-72-million-stop-deceptively-marketing-its-leads-home-improvement) and 110,372 refund checks went to service providers (P, https://www.ftc.gov/news-events/news/press-releases/2023/11/ftc-returns-more-3-million-businesses-paid-homeadvisor-memberships-announces-claims-process). Vermont's AG made Angi stop calling contractors "Angi Certified Pro" and pay $100,000 in October 2025 (P, https://ago.vermont.gov/blog/2025/10/13/attorney-general-clark-settles-dispute-angi-over-misleading-marketing-practice). The Pointbreak robocall scheme sold "claim and verify" of a Google listing for $300 to $700 and a "guaranteed" placement program at $949.99 plus $169.99 or $99.99 a month (P, https://www.ftc.gov/news-events/news/press-releases/2018/05/ftc-action-halts-deceptive-robocalls-aimed-small-business-owners); 4,467 owners got refunds averaging $158.32 (S, FTC 2020 release). In May 2026 the FTC and Illinois sued Premium Home Service for creating "thousands of online business profiles for non-existent home-repair companies" with fabricated five-star reviews that "siphon customers from true local businesses" (P, https://www.ftc.gov/news-events/news/press-releases/2026/05/ftc-illinois-take-action-stop-deceptive-conduct-company-created-thousands-business-listings-fake). That last one matters for this segment: the honest local roofer is now competing in the map pack against fake listings, and the defence is a maintained, verified, well-reviewed profile.
- **What a fixed-scope service replaces:** the $300 to $700 "claim and verify" call, the $287.99-plus-leads marketplace membership, and the off-season silence. Offers 1 (GBP), 2 (review desk) and 5 (seasonal kit) in section 4.
- **Price band evidence:** GBP management $125 to $400 per profile per month, setup $300 to $500 (P, https://www.merchynt.com/post/google-my-business-management-pricing); $99 monitoring, $249 lite, $399 pro per location, no contracts (P, https://gmbgorilla.com/google-my-business-management-service/); reinstatement $750 and verification $750 as one-time services (P, https://renewlocal.com/prices/).
- **Churn and support burden:** seasonal. Expect cancellation attempts after the fall gutter and roofing rush; the counter is the seasonal kit that produces visible work in the slow months. Owner is on a roof during the day; support is text and evening email.
- **Verdict:** first. Chris already has a gutter client and an awning client, the FTC record on this buyer is the deepest of any segment, and the deliverables (GBP posts, review replies, seasonal pages) are the most mechanical.

### Rank 2. Mechanical trades with crews: plumbing, HVAC, electrical, 5 to 50 employees

- **Counts (P):** plumbing/heating/AC 109,601 establishments (Montana 710), of which 20,550 have 5 to 9 employees, 12,938 have 10 to 19 and 8,184 have 20 to 49; electrical 81,842 (Montana 536). Annual payroll $82.2 billion and $68.4 billion.
- **Revenue band:** the 5-to-49-employee bands are the $1 million to $10 million shops. No primary revenue distribution was fetched; treat as inference from payroll.
- **What they buy now and spend:** "the average HVACR contractor spends 6% of annual revenue on marketing and advertising" (S, phcppros.com summary of ACCA's Contractor of the Future study of 1,000-plus contractors; the fetched page confirms the profit split below). Contractors at 12 percent or more of revenue net 9 percent profit versus 5 percent below 12 percent (P, https://www.phcppros.com/articles/22596-acca-and-farmington-consulting-group-release-2025-contractor-of-the-future-study-results). ACCA's own budget guidance: invest 10 percent of gross revenue, 35 percent of it digital, 25 percent direct mail; "database marketing to lapsed customers delivers $8-12 return for every dollar spent, compared to $3-4 for new customer acquisition, yet most contractors spend 70-80% of budgets chasing new customers"; and "front-load 60-70% of marketing spend into peak 4-6 months" (P, https://hvac-blog.acca.org/smart-spending-how-to-allocate-your-2026-marketing-budget-for-maximum-roi/). HVAC search CPL $45 to $65, plumbing $40 to $55 (T, WebFX). ServiceTitan is quoted at $350 to $500 all-in acquisition cost per lead (T, via search summary; unverified).
- **What they overpay for:** the locked-in bundle vendors. Hibu "typically charges $1,100-$1,500/month" (T, mybrandingagency.com); Scorpion "$2,500-$6,000/mo" on 12-month contracts with large setup fees (T, same source family); Thryv requires a six-month initial term (T). BBB complaint counts: Thryv 352 in three years, Hibu 115, Scorpion 6 (S, BBB profiles; the profile pages block fetches). The recurring complaint shape is "told we were locked in until 2027" and "went from 80 leads a month to zero" (S). These are the clients who have been churned by a big vendor and are now suspicious of anyone with a contract.
- **What a fixed-scope service replaces:** the lapsed-customer program nobody sells them (offer 3), multi-location GBP for the shops with two or three branches (offer 1), and review response at scale, since a 20-tech shop collects reviews daily.
- **Price band evidence:** as rank 1, plus review-platform software they are already quoted: Podium core $249 a month for up to two locations, pro $599, 12-month minimum (T, socialpilot and businessnewsdaily); Birdeye $299, $349, $449 per location per month on annual contracts with $500 to $1,500 onboarding and add-ons (T, several third-party pricing pages; birdeye.com/pricing renders only in JavaScript).
- **Churn and support burden:** lower churn (year-round demand), heavier support (an office manager who will email). Expect requests to expand scope into ads, which SWAE should either price separately or refuse.
- **Verdict:** second. Highest ability to pay and the clearest association-backed gap (lapsed-customer marketing), but SWAE has no HVAC or plumbing proof yet and the vertical is crowded with trade-specific agencies. Sell with a case study from rank 1 first.

### Rank 3. Multi-location home-service operators and franchisees, 2 to 20 locations

- **Counts:** no clean NAICS count. Proxy from CBP: plumbing/HVAC and electrical establishments with 20 to 99 employees total 18,719 (P); many of those are multi-branch. A single Local Search Forum poster runs 350 franchise locations launching "4-6 new locations per month" (P, https://localsearchforum.com/threads/multi-unit-franchise-with-excess-of-suspensions.62383/).
- **What they buy now:** per-location listing management from Yext-style platforms or an in-house marketing coordinator. BrightLocal's managed local SEO is $799 to $1,299 per location per month (S, help.brightlocal.com; page blocked). Renew Local prices software-only management at $30 per location, falling to $18 at 31 to 50 locations (P).
- **The pain, in their words (P, same thread):** "over the past four+ months, nearly every new listing we create has been suspended almost immediately for 'deceptive content'", "some profiles ... stuck in 'appeal submitted' status for nearly three months", "Is there a way to get an actual representative to work with on the resolution?" Supporting signal: Sterling Sky's suspension-related support tickets doubled in H1 2024 versus the prior year (S); a 2024 Local Search Forum poll found 61 percent of affected businesses saw measurable drops in leads or calls during a suspension (S, via assetdigitalcom.com, unverified). Whitespark lists "Overlapping Service Areas on Multiple-Location GBPs" and "Showing Your Address on GBP When Business is a Service Area Business" among negative factors (P, https://whitespark.ca/local-search-ranking-factors/).
- **What a fixed-scope service replaces:** the coordinator's spreadsheet. Agents are good at exactly this: the same 12 checks on 20 profiles every week, flagged edits, suspension watch, a per-location post calendar.
- **Price band evidence:** $99 to $399 per location with volume discounts (P, GMB Gorilla, Renew Local); $750 per reinstatement (P, Renew Local).
- **Churn and support burden:** low churn once embedded; moderate support; one buyer, many profiles. Risk: Google policy changes and suspensions that no vendor can promise to fix. Price reinstatement by the hours it takes, with the outcome left to Google.
- **Verdict:** third. Smallest count, best unit economics per client, and the most agent-shaped work. Also the segment where a mistake (a bad bulk edit) does the most damage, so acceptance checks matter.

### Rank 4. Landscaping and lawn care, 1 to 20 employees

- **Counts (P):** 117,109 establishments, 83,049 under five employees; Montana 669. Payroll $38.5 billion.
- **Revenue band and spend:** Landscape Leadership guidance: companies under $2 million should spend 5 to 7 percent of revenue on marketing (S; the page fetched as a 504-character shell). Lawn & Landscape's 2025 State of the Industry reports mean and median revenue slipped in 2024 and "difficulty in raising prices" rose from 39 to 44 percent (S; lawnandlandscape.com returned 212 bytes to every fetch).
- **What they buy now:** Facebook (the top digital channel for cleaning and lawn businesses at 36 percent), lead-gen sites 20 percent, Google Search 17 percent, LSAs 15 percent (S, Jobber/Aspire summaries, unverified); HomeAdvisor named "small lawn care businesses" as its targets (P, FTC complaint).
- **What they overpay for:** marketplace leads during the two months a year they do not need them, and nothing in the eight months they do. Jobber reports 2024 "saw fewer jobs being scheduled" with revenue held by price increases (S, Jobber Home Service Economic Report, Feb 2025; page is a JavaScript shell).
- **What a fixed-scope service replaces:** the Facebook posting the owner's spouse does, review replies, and a spring-and-fall campaign kit. Offers 2 and 5.
- **Price band evidence:** social packages at $399 (4 posts), $599 (8), $899 (12) (S, BizIQ); $99 to $349 for 12 image posts (S, Socinova); LYFE $750 for 12 posts across Facebook and Instagram (P, https://www.lyfemarketing.com/social-media-marketing-packages/).
- **Churn and support burden:** highest seasonal churn of the list; low support. Pause-instead-of-cancel terms matter.
- **Verdict:** fourth. Large count, existing SWAE clients, mechanical deliverables, lower ticket.

### Rank 5. Residential remodelers

- **Counts (P):** 133,345 establishments, 108,412 under five employees; Montana 772. NAHB member remodelers: median five employees, $1.7 million median revenue, 15 jobs over $10,000 a year; 80 percent under $5 million (P, Eye on Housing).
- **Spend and sources:** 37 percent of leads from client referrals (S, NAHB); construction search CPL $100 to $264 (T).
- **Overpaying on:** same marketplaces as rank 1; HomeAdvisor's complaint names "kitchen remodeling" leads (P). Job values of $10,000-plus make one bad lead month expensive.
- **What a service replaces:** project-showcase content (before/after, which SWAE already produces for gutters), review desk, GBP. Offers 1, 2 and 5.
- **Price band:** as rank 1; higher tolerance for $500-plus because of job value.
- **Churn and burden:** moderate; owners want to approve photos of their work, which adds a touchpoint.
- **Verdict:** fifth. Good economics, but each client needs photo supply from the job site, which is the input agents cannot generate.

### Rank 6. Auto detailing and car wash

- **Counts:** 19,463 employer establishments in NAICS 811192, 10,745 under five employees; Montana 95 (P). IBISWorld counts about 57,900 businesses including nonemployers (T, via mmcginvest.com). Industry revenue about $14.6 billion in 2023 (T, same).
- **Spend:** marketing is "usually a smaller share (each under 5% of revenue)" of a car wash's costs (T, mmcginvest). Self-serve operators report summer carries 35 percent of business and spring 25 percent (T, Auto Laundry News survey via mmcginvest).
- **The gap:** retention. "The average auto detailing business retains only 22% of first-time customers for a second service" (T, regulr.ai citing the IDA 2025 Industry Survey; the IDA source could not be fetched and is listed in section 6). The same page cites IDA for referral programs producing 15 to 25 percent of new customers.
- **What a service replaces:** nothing they currently buy, which is the problem and the opportunity. A $199 lapsed-customer and membership email/SMS program (offer 3) is the whole pitch.
- **Price band:** $200 to $400 a month is the ceiling given sub-5-percent marketing share on sub-$1 million revenue.
- **Churn and burden:** moderate churn, low support. Chris has a detailing client, which is the proof.
- **Verdict:** sixth. Small tickets; worth it as a bundle with the existing client and as the test bed for offer 3.

### Rank 7. Independent full-service restaurants

- **Counts (P):** 257,282 full-service establishments; Montana 1,100. 
- **Spend and pain:** operators ranked inflation (20 percent), marketing (16 percent) and sourcing/hiring (16 percent) as top pain points; 46 percent "find advertising to be moderately or extremely challenging"; if spending slows, 47 percent would increase marketing, 46 percent offer deals (P, https://pos.toasttab.com/blog/data/2025-voice-of-restaurant-industry-survey, n=712 operators with 16 or fewer locations). Independents spend 3 to 6 percent of gross revenue on marketing (T, dogood.design).
- **What they buy now:** social posting, Yelp ads (Yelp settled a $15 million class action over one-way sales-call recording; S, dailyjournal), delivery-app placement.
- **What a service replaces:** the owner posting at 11pm. Review desk and weekly social are the fit; email is strong for restaurants with a list.
- **Price band:** $250 to $500. Socinova's $99 to $349 (S) shows the floor.
- **Churn and burden:** high churn because restaurants close and because margins are thin; moderate support (menu changes, hours). SWAE's pizza client is the proof.
- **Verdict:** seventh. Biggest count, weakest wallet.

### Rank 8. Dental and chiropractic practices

- **Counts (P):** dentists 136,140 establishments (Montana 508); chiropractors 40,179 (Montana 236). Dental payroll $59.6 billion.
- **Revenue and spend:** ADA HPI reports average GP gross billings of $942,290 (S) and GP income of $215,320 in 2025 with "practice expenses growing faster than reimbursement" (P, https://www.ada.org/resources/research/health-policy-institute/dental-practice-research/trends-in-dentist-income). Marketing 3 to 5 percent for established practices, 6 to 10 percent for growing ones (T).
- **What they buy now:** Birdeye and Podium at $249 to $449 per location per month on annual contracts (T), plus dental-specific agencies.
- **Gap:** review response quality and GBP. But the vendors are entrenched and the practice manager already has a tool.
- **Verdict:** eighth. High ability to pay, low underservice. Sell only on referral.

### Rank 9. Solo and small law firms

- **Counts (P):** 166,972 establishments, 120,321 under five employees; Montana 675. Payroll $130.7 billion, the largest of any segment here.
- **Spend:** small firms and solos spend $5,000 to $50,000 a year; 59 percent name referrals as their top lead source (S, Clio 2025 Legal Trends for Solo and Small Firms; clio.com pages blocked). Firms using online intake and scheduling saw 53 percent higher revenue (S, same).
- **Gap:** GBP and reviews, same as everyone. The catch is bar advertising rules: testimonials, "specialist" claims and disclaimers vary by state, so review responses and content need a lawyer's eye, which breaks the light-QA model.
- **Verdict:** ninth. Money is there; the QA burden is not light.

### Rank 10. HR consultancies and other B2B consultants

- **Counts:** 8,958 employer establishments in NAICS 541612 (6,565 under five employees; Montana 31) (P); IBISWorld counts 51,209 businesses including solos, with $29.0 billion revenue (P, https://www.ibisworld.com/united-states/industry/hr-consulting/1423/).
- **What they buy now:** LinkedIn content and a newsletter, usually done by the principal.
- **Gap:** consistency. The risk is that agent-written thought leadership reads as AI, which in a consultancy is fatal to credibility. SWAE's own de-AI rules apply at their strictest here.
- **Verdict:** tenth. Keep the existing HR client, do not build a segment around it.

### Rank 11. Residential and commercial cleaning

- **Counts (P):** janitorial 67,295 establishments (Montana 484); carpet cleaning 6,902.
- **Spend and sources:** 64 percent of leads from repeat customers, 60 percent referrals; Facebook 36 percent of digital leads (S, Jobber/Aspire, unverified). ISSA has a residential benchmarking study behind a paywall (S).
- **Verdict:** eleventh. Price sensitivity is high and the referral dependence means a retention email program (offer 3) is the only fit.

### Rank 12. Tattoo studios

- **Counts:** no NAICS; studios sit in 812199 "other personal care" (22,597 establishments, P) with many other businesses.
- **Evidence:** none fetched on marketing spend; the searches for a studio survey were lost to the search cap. Instagram dependence is an assumption from experience, flagged in section 6.
- **Verdict:** twelfth. SWAE's directory (Global Tattoo Guide) is a distribution channel to this segment, so a $99 "claim and keep your GBP and directory listing current" product could ride on it, but there is no spend evidence to size it.

---

## 2. Buyer profiles and journeys for the top four

What the agents produce and where Chris's QA goes is marked at each step. "QA" means Chris reads and approves; the standing rule that nothing client-visible goes out without his sign-off is assumed throughout.

### Profile A. The exterior-trades owner (gutters, roofing, siding, painting, awnings)

**Persona.** Owner-operator, crew of two to eight, works on site, answers the phone from the truck. Revenue $400,000 to $3 million. Marketing is the spouse or office manager plus whatever vendor last called. Has paid HomeAdvisor or Angi at some point and has a story about it. Has received the "Google specialist" robocall. Reviews come in bursts after jobs and nobody replies to them.

**Decision triggers.**
- Fall rush ends and the phone stops (gutters, roofing); spring thaw (painting, awnings). ACCA's advice to front-load spend into the peak four to six months (P) is the inverse of what this owner feels: the urge to buy marketing comes in the slow season.
- A one-star review that sits unanswered on the top of the profile. 31 percent of consumers now require 4.5 stars or better and 47 percent will not use a business with fewer than 20 reviews (P, BrightLocal 2026).
- A competitor's new website or a new franchise unit in town with 200 reviews.
- The marketplace contract renewing (Angi's one-year term with a 35 percent early termination fee, T).
- A GBP suspension or a fake competitor listing (the Premium Home Service pattern, P).

**Objections.** "I tried SEO and got nothing." "I don't want a contract." "I don't have time to send you stuff." "My nephew does our Facebook." "What do you mean by AI, will it sound like a robot?"

**What they find insulting.** Templated review replies (50 percent of consumers are put off by them too, P). Being asked for a 12-month commitment. Jargon reports. A post that gets the trade wrong (calling a seamless gutter a "gutter guard", a 3-tab a "laminate"). Being treated like a name on a call list.

**How they check credibility.** They Google SWAE and look at its own reviews and GBP. They ask "who else in my trade do you work for" and want to see that site and that profile. They call that client. They check how long the agency has been around and whether it has a street address. They notice whether the salesperson knows what a downspout is.

**Journey.**
1. **Discovery:** referral from another tradesman, a supplier rep, or a local Facebook group; occasionally a search for "gutter marketing" that lands on a SWAE case study. Agents produce the trade-specific case-study page and the monthly before/after posts that make the referral conversation easy. QA: Chris approves the case study once.
2. **Proof they need:** one client in their trade with a visible profile and a number ("reviews went from 14 to 61 in nine months"). Agents assemble the proof sheet from GA, GSC and GBP data. QA: 15 minutes per proof sheet, checking every number against the source.
3. **How they buy:** a phone call with Chris and a one-page order form, month to month, card on file through the dashboard. No proposal deck.
4. **Onboarding (the churn point):** GBP manager access, Facebook page role, website login, a 20-minute call to capture services, service area, pricing stance and what never to say. Promethean: 62 percent of agency leaders say access delays during onboarding damage client confidence (P). Agents produce the access checklist, the brand-and-trade brief, and the first month's calendar. QA: Chris reads the brief (20 minutes), because every later deliverable inherits it.
5. **Monthly touchpoints:** one text with the month's review-reply batch for approval; one email with the post calendar; one one-page report (calls, direction requests, review count, rating, posts published). Agents produce all three. QA: 30 to 45 minutes.
6. **Why they cancel:** the season ended; they could not see the link between posts and calls; a reply embarrassed them; they got a cheaper call. Counter: the seasonal kit produces visible work in the slow months, and the report leads with calls and direction requests, which GBP provides directly.

### Profile B. The mechanical-trades owner or office manager (plumbing, HVAC, electrical, 5 to 50 employees)

**Persona.** Owner in the office more than the field; an office manager or dispatcher owns the marketing login. Uses ServiceTitan, Housecall Pro or Jobber. Revenue $1 million to $10 million. Has had a Hibu, Thryv, Scorpion or LocaliQ contract and has either just left it or is counting the months. Has a customer database of several thousand households and does nothing with it.

**Decision triggers.** The bundle vendor's contract ends; a tech-count jump means more reviews than anyone can answer; a second branch opens and the GBP work doubles; shoulder season (spring and fall for HVAC) when the schedule empties; a suspension.

**Objections.** "We just got burned, why are you different." "Our CRM already sends review requests." "Posts don't bring us leads." "What happens if Google suspends us, are you responsible?"

**What they find insulting.** A sales call that opens with "I noticed your website". Any contract longer than 30 days. Reports that do not show calls. Being told their 6 percent spend is too low by someone who has not run a truck.

**How they check credibility.** References in a trade with trucks. The agency's own BBB record. Whether the agency will put the scope in writing and let them leave. Whether the first-month deliverables show up on time.

**Journey.**
1. **Discovery:** the office manager searches "who can answer our Google reviews" or asks in a trade Facebook group; a supplier or a rank-1 client refers.
2. **Proof:** a rank-1 case study plus a sample lapsed-customer email written for their trade. Agents draft the sample from public information about the shop. QA: Chris reads the sample (10 minutes).
3. **Buy:** a 30-minute call, a scope sheet, month to month. The lapsed-customer program needs a CRM export, so the order form names the file and the fields.
4. **Onboarding:** GBP access for each location, CRM export, review-platform access if they have one, a 30-minute call on services, seasonal offers, service area, licensing claims and what the techs are allowed to promise. Agents produce the brief, the segment logic for the email program (last service date, equipment age if present, service area) and the first sends as drafts. QA: Chris reads the brief and the first two emails (30 minutes).
5. **Monthly touchpoints:** review-reply batch (daily cadence for a 20-tech shop; see offer 2 for how approval works at that volume), two emails and one SMS to lapsed segments, GBP calendar per location, one report per location plus a rollup. QA: 45 to 60 minutes.
6. **Why they cancel:** a bigger vendor promises leads; the office manager leaves and the new one does not know what SWAE does (contact turnover is a named churn driver, P, Promethean); the email program is blamed for an unsubscribe complaint. Counter: a quarterly 20-minute review call with Chris, and an email program that is conservative on frequency.

### Profile C. The multi-location operator (franchisee or owner of 2 to 20 branches)

**Persona.** Regional operator or franchise marketing lead; has a corporate brand book and a list of what the franchisor forbids; launches new locations and needs each one verified, categorised and posting from day one. Knows what a suspension costs.

**Decision triggers.** A new location opening; a wave of suspensions; a franchisor audit of local listings; a corporate change that has to be pushed to every profile (hours, a new service, a rebrand); a coordinator resigning.

**Objections.** "Can you work inside our franchisor's rules?" "Who is liable if a bulk edit breaks something?" "We already have Yext/SOCi." "We need someone who can talk to Google."

**What they find insulting.** Being sold a single-location package. Any suggestion of keyword-stuffing names or fake addresses (both are listed negative factors and suspension triggers, P, Whitespark). A reinstatement "guarantee", because they know nobody can give one.

**How they check credibility.** They ask to see the change log and the per-location checklist. They ask what happens when Google changes a policy. They ask for a reference with more locations than they have.

**Journey.**
1. **Discovery:** Local Search Forum, franchisor marketing councils, a rank-2 client that grew.
2. **Proof:** a sample weekly audit across their existing profiles (read-only, from public data) showing category gaps, missing services, duplicate or overlapping service areas, unanswered reviews per location. Agents produce it. QA: Chris checks a sample of five locations (20 minutes).
3. **Buy:** per-location pricing with a floor, a written scope, a change-control rule (every bulk edit is staged, listed and approved before it runs), month to month.
4. **Onboarding:** location group access, brand rules ingested into the brief, per-location NAP and service-area confirmation, a pre-launch checklist for new units that avoids the known suspension triggers (unique local phone, address evidence, no overlapping service areas, verification cadence). Agents produce all of it. QA: 45 minutes on the brief and the first audit.
5. **Monthly touchpoints:** weekly audit summary (flags only), monthly post calendar per location, suspension alerts within the hour with a prepared appeal draft, monthly rollup report. QA: 15 minutes a week on flags, 30 minutes on the monthly rollup.
6. **Why they cancel:** a platform vendor bundles the same work; a bad bulk edit; the franchisor mandates a vendor. Counter: the change log and the staging rule are the product.

### Profile D. The landscaper or lawn-care owner

**Persona.** One to fifteen people, revenue $200,000 to $2 million, truck-and-trailer operation, half the customers are recurring maintenance and half are one-off installs. Marketing is Facebook, a yard sign and a Google profile that still shows last year's hours. Season runs April to October in Montana.

**Decision triggers.** March, when the phone has not started; a slow July; a competitor's spring mailer; a bad review from a one-off install customer; the marketplace renewing.

**Objections.** "I'm full in summer, I don't need marketing." "I can't afford $500 in winter." "Just do my Facebook."

**What they find insulting.** Stock photos of lawns that are not theirs. Posts that name plants that do not grow in zone 4. A winter invoice for nothing visible.

**How they check credibility.** Another landscaper's Facebook page. Whether the agency knows what a maintenance contract is. Price.

**Journey.** As Profile A with two changes: the kit is spring and fall, and the billing is seasonal (eight months on, four months paused at a lower "keep the lights on" rate that covers review replies and GBP only). Agents produce the two seasonal kits in February and August. QA: 30 minutes per kit, 20 minutes a month otherwise.

---

## 3. Unserved and poorly served gaps

Each gap lists the evidence, the price evidence, what competitors ship, and what buyers complain about.

### Gap 1. Review response, done daily, in the owner's voice, within the FTC rule

- **Evidence of demand:** 89 percent of consumers expect responses; 19 percent expect same day (up from 6 percent the year before) and 81 percent within a week; 80 percent are more likely to use a business that replies to every review; 42 percent are unlikely to use one that never replies; businesses that reply only to positive (45 percent) or only to negative (47 percent) reviews do worse than those that reply to all; templated or generic responses make 50 percent of consumers unlikely to choose a business (P, https://www.brightlocal.com/research/local-consumer-review-survey/). Owner response is the fifth most trusted review attribute at 37 percent (P, same). Whitespark 2026: review signals rose in importance (P).
- **Compliance edge:** the FTC's Consumer Reviews and Testimonials Rule (effective October 2024) bans buying reviews, undisclosed insider reviews, and using "unfounded or groundless legal threats, physical threats, intimidation, or certain false public accusations to prevent or remove a negative consumer review" (P, https://www.ftc.gov/news-events/news/press-releases/2024/08/federal-trade-commission-announces-final-rule-banning-fake-reviews-testimonials); penalties up to $51,744 per violation (S). A service that replies well and solicits reviews lawfully has a selling point against "we'll get you 50 reviews" vendors.
- **What competitors ship:** Podium and Birdeye ship software with AI-drafted replies, $249 to $449 per location on 12-month terms (T); GMB Gorilla includes "review responses" in its $99 monitoring tier (P).
- **What buyers complain about:** cost and contracts ("some small businesses have said that Podium's prices are prohibitive", S, businessnewsdaily); templated replies (P, BrightLocal consumer side).
- **Price evidence:** $99 to $249 per location (P, GMB Gorilla tiers).

### Gap 2. GBP management for multi-location trades, with suspension defence

- **Evidence:** section 1 rank 3 (P, Local Search Forum thread; S, Sterling Sky). BrightLocal's own research says just 35 percent of SMBs have a Google Business Profile at all (P, quoted inside the 2026 consumer survey page), which is a second, larger gap at the bottom of the market.
- **What competitors ship:** per-location dashboards (Yext, SOCi, BrightLocal $31 to $49 a month per location for software, P, https://www.brightlocal.com/pricing/) that still need a human to act; reinstatement as a $750 one-off (P, Renew Local).
- **Complaints:** "stuck in appeal submitted for three months", "no actual representative" (P).
- **Price evidence:** $99/$249/$399 per location, no contracts (P); $30 per location software (P); $799 to $1,299 managed (S).

### Gap 3. Lapsed-customer email and SMS for trades

- **Evidence:** ACCA: $8 to $12 per dollar on database marketing versus $3 to $4 on acquisition, while "most contractors spend 70-80% of budgets chasing new customers" (P). Detailing retains 22 percent of first-time customers (T, IDA via regulr). 64 percent of small businesses use email marketing (T, servicedirect.com); 41 percent of owners in a Constant Contact survey expect email to be their most valuable channel (S).
- **What competitors ship:** the trade CRMs (ServiceTitan, Jobber, Housecall Pro) ship the sending tool; nobody writes the sends or builds the segments for a six-person shop. Agencies sell email as part of a $2,000-plus retainer.
- **Complaints:** the search sweep found no vendor-specific complaint body here, which is itself the finding: there is no incumbent to complain about.
- **Price evidence:** none direct; Klaviyo-style software is $20 to $100 a month, and the labour is the product. Priced in section 4 by analogy to the $199 to $399 social tiers.

### Gap 4. Website care plus local landing pages

- **Evidence:** 11,334 new WordPress vulnerabilities in 2025, up 42 percent; 91 percent in plugins; 46 percent had no patch at disclosure; 17 percent carried a high risk of mass exploitation (P, https://patchstack.com/whitepaper/state-of-wordpress-security-in-2026/). WordPress runs 40.1 percent of all websites, a 58.6 percent CMS share (P, https://w3techs.com/technologies/overview/content_management). 17 percent of small businesses still have no website (S, Clutch 2025 press release; page blocked), and BrightLocal says only 40 percent of local businesses have a dedicated website while 54 percent of consumers visit the website after reading positive reviews (P, consumer survey page).
- **What competitors ship:** WP Buffs $89 to $359 (S), GoWP $39 to $99 per site with a $49 white-label add-on and "human edits" counted per month (P, https://gowp.com/pricing/), SiteCare $95 to $1,990 (S). None of them writes a city or service page every month.
- **Complaints:** care plans are invisible until something breaks; buyers cancel because nothing happens. Adding one visible page a month fixes the perception problem and feeds the GBP landing-page freshness factor Whitespark lists (P).
- **Price evidence:** $89 to $239 for care alone (S, WP Buffs); local SEO "basic" packages $500 to $900 a month including light GBP work (S, arc4.com).

### Gap 5. Seasonal campaign kits for seasonal trades

- **Evidence:** ACCA's "front-load 60-70% of marketing spend into peak 4-6 months" (P); self-serve car wash demand 35 percent summer, 25 percent spring (T); Lawn & Landscape price-raising difficulty (S); gutter and roofing seasonality is from SWAE's own client experience, not a fetched source (flagged in section 6).
- **What competitors ship:** 12-month social retainers that post the same way in January as in September.
- **Price evidence:** 4 to 12 posts a month at $399 to $899 (S, BizIQ); 12 posts at $750 (P, LYFE).

### Gap 6 (bottom of market). "Claim, verify and keep it honest" for the 65 percent with no GBP

- **Evidence:** 35 percent GBP adoption among SMBs (P, BrightLocal); the Pointbreak scheme sold exactly this service fraudulently for $300 to $700 (P); fake-listing competitors (P, Premium Home Service).
- **Price:** a one-time $149 to $299 setup plus the $99 monitoring tier is the honest version of the robocall pitch. Low revenue per client; useful as an entry product for the tattoo directory and for Montana trades.

---

## 4. Service catalogue: five fixed-scope offers

All prices month to month, cancel any time, with a pause option for seasonal trades. QA minutes are Chris's time per client per month, assuming agents draft everything and present it in one dashboard task per client per week during working hours. The target is 45 to 75 minutes per client per month on a two-offer bundle.

### Offer 1. Profile Keeper (GBP management), per location

- **For:** Profiles A, C, D; rank 1 to 5 segments.
- **Inputs:** GBP manager access; the onboarding brief (services, service area, hours, categories, what never to claim); 10 to 20 real job photos a month from the client (or a photo-request text the agent sends every Friday).
- **Monthly deliverables:** 4 posts per location (one offer, two job showcases, one educational); photo uploads; services and attributes refreshed; Q&A seeded and answered; weekly 12-point audit (categories, hours, name, address, service areas, suggested edits, duplicate check, suspension status); monthly one-page report (calls, direction requests, website clicks, review count and rating, posts published, audit flags).
- **Acceptance checks (agent runs before Chris sees it):** no keyword in the business name; no overlapping service areas across locations; every post names a real service from the brief; every photo is the client's; hours match the website; report numbers match the GBP export.
- **QA:** 20 minutes per location per month (post batch 10, report 5, flags 5). At 3-plus locations, 10 minutes per location.
- **Price band:** $149 per location for one, $119 at 2 to 5, $99 at 6-plus. Evidence: $125 to $400 (P, Merchynt), $99 to $399 (P, GMB Gorilla), $30 software (P, Renew Local).
- **Ties to:** Gap 2 and Gap 6.

### Offer 2. Review Desk

- **For:** all profiles; strongest for B and C.
- **Inputs:** GBP and Facebook access; the voice brief (a 300-word statement of how the owner talks, with three real replies they liked); the escalation list (what gets a call before a reply: threats, safety, legal, refunds).
- **Monthly deliverables:** a reply to every review within one business day; a weekly review-request send to completed jobs (from the CRM export or a job list the client texts) with no incentive language and no gating, per the FTC rule; a monthly sentiment digest (themes, names of techs praised, complaints to fix); flagging of suspect reviews for Google reporting.
- **How approval works at volume:** Chris pre-approves a reply standard per sentiment class (5-star, 4-star, 3-and-under without a complaint, complaint, escalation). Agents draft within that standard; anything in the complaint or escalation class waits for Chris; the rest is posted after a same-day batch glance. This is the one place where the "every client-visible artifact gets a sign-off" rule has to become "every class of artifact gets a sign-off, exceptions get one each", or the one-business-day promise fails.
- **Acceptance checks:** reply names the service and the reviewer and contains no phrase from the ai-tells list; no reply admits liability or discusses money; no incentive in any request; every complaint class reply has a Chris approval in the log.
- **QA:** 20 minutes a month for a single-location trade (daily 2-minute glance plus the digest); 40 minutes for a 20-tech shop.
- **Price band:** $129 single location, $99 per additional. Evidence: $99 tier includes review responses (P, GMB Gorilla); software alternatives $249 to $449 (T).
- **Ties to:** Gap 1.

### Offer 3. Win-Back (lapsed-customer email and SMS)

- **For:** Profiles B and D, detailing, cleaning.
- **Inputs:** CRM or invoice export (name, email, phone, last service date, service type, address); the offer the owner will stand behind in the slow season; the trade calendar (filter changes, tune-ups, aeration, fall cleanups, winterising).
- **Monthly deliverables:** two emails and one SMS to segments (12-plus months since service, seasonal service due, one-time customers never booked twice); a maintenance-plan or membership push once a quarter; a monthly report (sends, opens, replies, bookings attributed by reply or code, unsubscribes).
- **Acceptance checks:** segment counts match the export; every send has a working unsubscribe and the right sender; no send to anyone who opted out; the offer in the email matches the one on the website; opt-in status is recorded for SMS (TCPA consent: if the export cannot show consent, SMS is dropped and the client is told why).
- **QA:** 25 minutes a month (two emails 15, SMS 5, report 5); 40 minutes in month one.
- **Price band:** $199 a month plus the client's own sending-tool cost. Evidence: no direct benchmark; $8 to $12 return per dollar on database marketing (P, ACCA) is the pitch; social tiers at $199 to $399 (S) bracket the willingness to pay.
- **Ties to:** Gap 3.

### Offer 4. Site Care plus one local page a month

- **For:** Profiles A, B, D; any WordPress client.
- **Inputs:** hosting and WordPress admin access; a staging site (required; SWAE's own rule about never pushing to live without a preview applies); the keyword map or a list of towns and services.
- **Monthly deliverables:** plugin, theme and core updates on staging then live, with a visual check; uptime and malware monitoring; backups verified; one new city-or-service page with LocalBusiness or Service schema and real photos; one-page report (updates applied, vulnerabilities closed with Patchstack IDs, uptime, the new page's URL and indexing status).
- **Acceptance checks:** no placeholder image anywhere on a live page; `php -l` and a visual diff on staging before any live push; the page's claims (licensing, years in business, service area) come from the brief; schema validates; no "seamless" or trade-name word blocked by any validator.
- **QA:** 20 minutes a month (page 15, report 5).
- **Price band:** $249 a month. Evidence: care alone $89 to $239 (S, WP Buffs), $39 to $99 (P, GoWP); basic local SEO with light GBP $500 to $900 (S).
- **Ties to:** Gap 4.

### Offer 5. Season Kit (quarterly)

- **For:** Profiles A and D; detailing; restaurants with a seasonal menu.
- **Inputs:** the trade calendar; last season's photos; the one offer the owner will run; the slow-season dates.
- **Deliverables per kit:** 12 social posts (feed and story sizes, captioned under the client's caption rules), two emails, one landing page or GBP offer post, one printable (a door hanger or yard sign file), a two-week publishing schedule, and a 30-second talk track the owner can use on the phone.
- **Acceptance checks:** every claim traceable to the brief; every photo the client's or licensed; captions pass the de-AI catalogue; no corrective-reframe sentence shapes; offer dates and prices confirmed by the client in writing before anything is scheduled.
- **QA:** 30 minutes per kit; zero in between.
- **Price band:** $349 per kit or $129 a month on the annual calendar. Evidence: 12 posts at $750 (P, LYFE) and $399 to $899 (S, BizIQ) for monthly social; this is priced below them because it ships four times a year.
- **Ties to:** Gap 5.

### Bundles and the hour

| Bundle | Offers | Monthly price | Chris's QA per month |
|---|---|---|---|
| Trade Basic (Profile A, D) | 1 + 2 | $278 | 40 min |
| Trade Plus (Profile A, B) | 1 + 2 + 3 | $477 | 65 min |
| Shop (Profile B, 2 locations) | 1 (x2) + 2 (x2) + 3 | $665 | 95 min |
| Multi (Profile C, 10 locations) | 1 (x10) + 2 (x10) | $1,980 | 3 to 4 hours |
| Site (any WordPress client) | 4 + 5 | $378 | 50 min |

The multi-location bundle breaks the one-hour target by design; it is the one where the per-client revenue justifies it, and the weekly audit is the same work ten times.

### Kill criteria for the catalogue (60 days)

- Fewer than two existing clients take any offer at these prices.
- Chris's QA exceeds 90 minutes per client per month on a two-offer bundle after month two.
- A client rejects a review reply or a post as reading like AI more than once.
- A GBP suspension traced to a SWAE edit.

---

## 5. Price and spend reference table

| Item | Figure | Source | Grade |
|---|---|---|---|
| Agency hourly rates | 36% at $175-199, 32% at $200-249 | Promethean 2025 Digital Agency Industry Report PDF, https://prometheanresearch.com/wp-content/uploads/2025/05/2025-Promethean-Research-Digital-Agency-Industry-Report-V1.02.pdf | P |
| Retainer tenure | 42% of agency leaders above two years; about a quarter under one year; 62% say onboarding access delays hurt confidence | https://prometheanresearch.com/client-retention-rate/ | P |
| Agency churn by model | retainer 18%/yr, 56-month lifespan; 1-10 employee agencies 32%/yr; month-to-month services 41%/yr | https://focus-digital.co/average-marketing-agency-churn/ | T |
| GBP management | $125-400/profile/mo; setup $300-500 | https://www.merchynt.com/post/google-my-business-management-pricing | P |
| GBP management | $99 / $249 / $399 per location, no contracts | https://gmbgorilla.com/google-my-business-management-service/ | P |
| GBP software + one-offs | $30/location/mo; $425 review dispute; $750 verification; $750 reinstatement | https://renewlocal.com/prices/ | P |
| BrightLocal software | $31-49/mo per location (annual) | https://www.brightlocal.com/pricing/ | P |
| BrightLocal managed | $799-1,299/location/mo | help.brightlocal.com (blocked) | S |
| Podium | $249/mo (2 locations), $599 (5), 12-month minimum | socialpilot.co, businessnewsdaily.com | T |
| Birdeye | $299/$349/$449 per location/mo, annual; onboarding $500-1,500 | wiserreview.com, contractortoolstack.com | T |
| WP Buffs | $89 / $179 / $239 / $359 | search snippet of wpbuffs.com/plans (page renders in JS) | S |
| GoWP | $0 / $39 / $99 per site; white label $49 | https://gowp.com/pricing/ | P |
| SiteCare | $95 to $1,990+ | search snippet | S |
| LYFE social | $750 / $1,350 / $1,550 per month | https://www.lyfemarketing.com/social-media-marketing-packages/ | P |
| BizIQ social | $399 (4 posts) / $599 (8) / $899 (12) | search snippet | S |
| Socinova social | $99 / $199 / $349 | search snippet | S |
| HomeAdvisor fees | $287.99/yr plus per-lead; mHelpDesk $59.99/mo | FTC 2022 complaint release | P |
| Angi Leads | $15-85/lead; 1-year term, 35% early termination | https://hookagency.com/blog/angi-leads-reviews/ | T |
| Pointbreak scheme | $300-700 one-time; $949.99 + $169.99 or $99.99/mo | FTC 2018 release | P |
| CPL by trade (search) | HVAC $45-65, plumbing $40-55, roofing $85-120 | webfx.com | T |
| HVAC marketing spend | average 6% of revenue; 12%+ spenders net 9% vs 5% | phcppros.com (ACCA study summary) | P (profit split), S (6%) |
| ACCA budget guidance | 10% of gross revenue; lapsed-customer ROI $8-12 vs $3-4 | https://hvac-blog.acca.org/smart-spending-how-to-allocate-your-2026-marketing-budget-for-maximum-roi/ | P |
| CMO Survey | marketing 9.4% of revenue (2025) | singlegrain.com summary | T |
| Gartner CMO Spend | 7.7% of revenue, flat | demandgenreport.com | T |
| Restaurants | marketing a top-3 pain point (16%); 46% find advertising hard; 47% would raise marketing if spending slows | https://pos.toasttab.com/blog/data/2025-voice-of-restaurant-industry-survey | P |
| Remodelers | median 5 employees, $1.7M revenue, 15 jobs over $10k | https://eyeonhousing.org/2025/09/who-are-nahb-remodelers/ | P |
| Dentists | GP income $215,320 (2025); expenses up 4.9% vs revenue up 1.4% over five years | ADA HPI page | P |
| Small law firms | $5k-50k/yr marketing; 59% referrals top source | Clio 2025 (pages blocked) | S |
| Consumer review behaviour | 89% expect responses; 19% same day; 42% avoid non-responders; 50% put off by templates; 31% require 4.5+; 47% need 20+ reviews; only 35% of SMBs have a GBP; 40% of local businesses have a website | https://www.brightlocal.com/research/local-consumer-review-survey/ | P |
| Local ranking factors | review and behavioural signals up in 2026; overlapping service areas and SAB address display are negative factors | https://whitespark.ca/local-search-ranking-factors/ | P |
| WordPress security | 11,334 vulns in 2025 (+42%); 91% plugins; 46% unpatched at disclosure | https://patchstack.com/whitepaper/state-of-wordpress-security-in-2026/ | P |
| WordPress share | 40.1% of all sites; 58.6% of CMS | https://w3techs.com/technologies/overview/content_management | P |
| SMB websites | 83% have one, 17% offline (2025) | Clutch press release (blocked) | S |
| BBB business scams 2025 | businesses lose money 18.5% of the time; median loss $931; fake invoice #2 ($532); "worthless problem-solving service" #5 (32.2% susceptibility, $1,500) | https://bbbmarketplacetrust.org/wp-content/uploads/2026/08/Risk-Report-2025-US.pdf | P |
| SBA | 28.5M nonemployer firms (81.9%), 6.27M employer firms | SBA Advocacy FAQ PDF | P |
| Business applications | 5.62M in 2025 vs 5.2M in 2024 | census.gov BFS (snippet) | S |

---

## 6. Unverified claims and sources needing a manual read

**Claims used above at S or T that should be read in a browser before they appear in anything client-facing:**

1. IDA 2025 Industry Survey: 22 percent of first-time detailing customers return. Only seen via regulr.ai. Find the IDA source (the-ida.com) and confirm the question wording and sample.
2. ACCA "average HVACR contractor spends 6% of revenue on marketing": the phcppros page fetched confirms the 12 percent profit split; the 6 percent figure came from a search snippet of the same article family. Confirm in ACCA's own study summary.
3. Clio 2025 Legal Trends for Solo and Small Firms: $5,000 to $50,000 marketing spend and 59 percent referrals. clio.com blocked every fetch.
4. Clutch 2025: 83 percent of small businesses have a website. clutch.co blocked.
5. Lawn & Landscape 2025 State of the Industry: revenue dip and price-raising difficulty. lawnandlandscape.com returned 212 bytes.
6. Landscape Leadership 5 to 7 percent marketing spend under $2 million revenue: page returned a shell.
7. Birdeye and Podium prices and contract terms: both pricing pages are JavaScript-only; all figures are third-party.
8. WP Buffs tiers: wpbuffs.com/plans renders prices in JavaScript; figures are from the search snippet.
9. BBB complaint counts for Thryv (352), Hibu (115), Scorpion (6), Angi (2,064 over three years, "35% fake/dead leads"): bbb.org profile pages block fetches; the Angi figures came from a secondary summary and the "35 percent" is an interpretation, not a BBB statistic.
10. Sterling Sky "suspension tickets doubled in H1 2024" and the Local Search Forum poll "61% saw lead drops during suspension": sterlingsky.ca returned 216 bytes; the poll was quoted by assetdigitalcom.com.
11. Cost-per-lead benchmarks by trade (WebFX, Watson, Foundry CRO) and the ServiceTitan "$350-500 per lead all-in" figure: agency blog content; use only as ranges.
12. "64% of small businesses use email marketing" (servicedirect.com) and the Constant Contact 41 percent figure: vendor surveys, sample sizes unknown.
13. Cleaning and lawn lead-source percentages (64 percent repeat, 60 percent referral, Facebook 36 percent): Jobber and Aspire content, methodology unseen.
14. CMO Survey 9.4 percent and Gartner 7.7 percent: both are from summaries, and both skew to firms far larger than any buyer here.
15. Gutter, roofing and awning seasonality: taken from SWAE's own client experience; no fetched source. The report should say so if it is quoted.
16. Tattoo studios' Instagram dependence: assumption; the searches to test it were lost to the search cap.
17. Google Local Services Ads pricing and dispute rules: the Google help pages fetched contain only the intro text (the pricing article renders in JavaScript). LSA lead-cost complaints are therefore unsourced in this report.
18. Thryv, Hibu, Scorpion and LocaliQ client counts: not obtained; investor pages blocked.

**Pages fetched in full (P), for the record:** FTC HomeAdvisor complaint (2022), order (2023) and refunds (2023); FTC Pointbreak (2018); FTC Premium Home Service (2026); FTC Your Yellow Book (2014); FTC fake-reviews rule (2024); Vermont AG Angi settlement (2025); BBB 2025 Scam Tracker Risk Report PDF; SBA Advocacy FAQ PDF; Census CBP 2022 US and state bulk files; Promethean 2025 report PDF and client-retention page; ACCA HVAC blog budget article; phcppros ACCA study summary; Toast 2025 Voice of the Restaurant Industry; Eye on Housing NAHB remodelers; ADA HPI dentist income page; IBISWorld HR consulting overview; BrightLocal 2026 Local Consumer Review Survey and pricing page; Whitespark 2026 Local Search Ranking Factors; Patchstack State of WordPress Security 2026; W3Techs CMS overview; Merchynt, GMB Gorilla, Renew Local, GoWP and LYFE pricing pages; Local Search Forum franchise-suspension thread and BrightLocal 2025 study thread; Thumbtack community thread on charges for unresponsive leads; Hook Agency Angi Leads review; mmcginvest car wash overview; Focus Digital churn page; regulr.ai detailing retention page.

**Reddit:** not used, per policy.
