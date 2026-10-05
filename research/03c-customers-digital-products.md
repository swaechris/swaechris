# Digital products: who overspends, what they buy, and where the gaps are

Prepared for Chris DeWitt, SWAE Marketing. Research date 2026-10-05. Every URL was accessed 2026-10-05 unless marked otherwise. Companion to `01-income-options.md` (pick 3, digital products on an owned storefront; pick 4, Etsy as a second channel).

## How to read the evidence grades

- **P (primary, fetched):** the page was fetched in full with curl through the session proxy and the quoted figure was read from it. Fetched text is saved in the scratchpad under `pages/`.
- **S (search snippet):** a search result from the platform's own domain stated the figure in its snippet. The page itself returns 403 to every fetch. Good for wording, unknown for date.
- **T (secondary):** a third party says it. Indicative until re-verified.
- **Tooling notes.** The Semrush MCP returned `no_api_units` on the one call made, so there is no Semrush volume data here. Firecrawl returned "Insufficient credits" on its one call. The session's WebSearch budget (200 calls, shared with earlier work) ran out part-way through the second round of Etsy result-count checks, so Etsy listing counts exist for only eight phrases; the rest are listed under "needs a manual browser read". Bing result counts were tried as a substitute and discarded: they count Bing's index, not Etsy listings. The Gumroad search endpoint (`gumroad.com/products/search?query=`) answered curl with JSON, so Gumroad supply counts are P for every phrase.
- **Skeptic note.** The global rule to run a skeptic in parallel could not be followed inside this subagent (no Agent tool). The parent session should run one against the claims below, in particular the ranking and the trades-kit gap.

## Executive summary

1. The buyers who repeatedly pay for organisation and aspiration products are, in order of evidence strength: couples planning a wedding, planner and productivity-system buyers (including the ADHD-labelled segment), teachers, real estate agents, job seekers, solo and micro business owners (trades and local services included), nursing students and new nurses, new parents, students, and craft-cutter owners. Fonts, presets, Procreate brushes and crochet patterns are listed and rejected or deferred.
2. Spend triggers are documented at primary grade: 2 million US weddings a year at a $34,000 average (The Knot, P); 3,606,400 births in 2025 (CDC, S); 5,671,836 business applications in 2025, of which 519,090 in construction and 483,258 in "other services" (Census BFS, P); 1,438,569 Realtors with median business expenses of $9,530 (NAR, P); teachers spending $895 a year out of pocket (AdoptAClassroom, P); 328,443 NCLEX-RN candidates in 2025 (NCSBN, P); 5.9 million Cricut active users (10-K, P).
3. Supply is saturated everywhere a buyer can be named in one word. Etsy shows 611,948 results for "printable planners", 273,285 for "daily planner", 86,291 for "adhd planner" and 59,625 for "real estate templates" (S). Gumroad returns 19,775 products for "notion template", 5,583 for "digital planner", 1,920 for "resume template" (P). Notion's own marketplace lists 30,000+ templates, 7,604 under Student Life alone (P). Creative Market lists 273K+ templates (S), Envato Elements 440,000+ graphic templates (S), Canva 3.6 to 4.5 million (T).
4. Thin supply exists only where the buyer is defined by occupation and workflow rather than by aesthetic: Gumroad has 130 results for "sop template", 114 for "landscaping", 99 for "roofing", 49 for "lawn care", 163 for "hvac", 200 for "plumbing" (P). These are also the buyers SWAE already serves (NSL Seamless Gutters, Precision General Construction, Rugged Ridge Contracting, Stumptown Detailing, Whitefish AutoGlass, Indigo Holiday Lighting, two storage businesses, a paint booth, per the SWAE Dashboard client list, P). The honest caveat: trades spend on software and labour and treat documents as free, and the Etsy price point for a cleaning-business forms bundle is $5 to $7. The money in this gap is the upsell into SWAE services, with the kit as the lead product.
5. The one structural gap on the consumer side is resume templates. The incumbent category leaders (Zety, Resume.io) sell a $1.85 to $2.95 trial that converts to $23.95 to $29.95 every four weeks, with years of BBB and Trustpilot complaints and a pending federal suit alleging coordinated practice (T). A one-time $9 to $15 purchase with a plain ATS-formatting guide competes against that subscription trap. Supply on Etsy is heavy, so the angle is the sales page on the owned store.
6. Platform risk is manageable if three lines are never crossed: no AI prompt packs on Etsy (banned, S), the AI disclosure sentence in every Etsy listing with the "Designed by a seller" attribute (S), and no health, legal or financial outcome claims on ADHD planners, nursing study guides, contracts or budget tools. Etsy's Cases policy lets buyers open quality cases for 100 days after first download (S), and the most common refund triggers on Canva templates are Pro elements and "I thought it was editable" (T).
7. Demand is still the bottleneck named in `01`. Etsy supplies buyers; an owned store does not. Every profile below therefore names the discovery channel the evidence supports: Pinterest for weddings and planners (The Knot: "most-used platform for inspiration", P; Pinterest: 7 billion wedding searches, P), TikTok for Gen Z buyers (The Knot: usage up 2.5x, P; Etsy: Millennial and Gen Z visits via TikTok and YouTube up roughly 5x, P), SWAE's own list for B2B.

---

## 1. Ranked candidate niches

Ranking weighs: documented spend trigger, demand signal, supply saturation, policy risk, and whether an agent can build a product that is correct without a human specialist. "Gumroad count" is the `total` returned by Gumroad search for that phrase (P, 2026-10-05, matches any product text so treat as an upper bound). "Etsy count" is from Google snippets of etsy.com/search pages (S, snippet date unknown).

### 1. Couples planning a wedding (invitation suites, planning kits, trackers)

- **Buyer.** Engaged couples, 41% of the market now Gen Z (The Knot 2026 Real Weddings Study, P: https://www.theknotww.com/press-releases/the-knot-worldwide-unveils-2026-real-weddings-study). Planning is done by the couple with 13 hired professionals on average (P).
- **Trigger.** Engagement to wedding, roughly a 12 to 18 month window. "Approximately 2 million U.S. couples married in 2025"; "The average wedding cost in 2025 was $34,000"; 117 guests; "$292 per guest" (P, same URL).
- **Evidence of spend.** $100 billion US industry (P). "37% of couples reached out to more vendors than initially planned to find options that fit within their budget" (P), which is the DIY-template buyer's motive in one line.
- **Demand evidence.** Pinterest: "over 7 billion wedding-related searches" and "more than 16.7 billion wedding ideas" saved last year (P: https://newsroom.pinterest.com/news/wedding-trend-report-2026/). Pinterest trend lines in that report include "wish card template +205%" and "couple bingo card +175%" (P). The Knot: "Pinterest remains the most-used platform for inspiration among respondents, while TikTok usage has grown 2.5x in recent years" (P).
- **Supply saturation.** Etsy "wedding planner printable": "611,948 results" for printable planners generally (S, from a snippet of etsy.com/search?q=printable+planners); etsy.com/market pages exist for wedding_invitation_template, wedding_invitation_canva_template, editable_wedding_invitation, wedding_website_template (S). Gumroad: 325 for "wedding planner", 106 for "wedding invitation template" (P). Wedding supply on Gumroad is thin because the buyers are on Etsy and Canva; it is a channel mismatch rather than a gap.
- **Price band.** Etsy wedding invitation templates "starting at around $0.94 to $16.13, with many offerings at 20-75% discounts" (S, Google snippet of etsy.com/market/wedding_invitation_template). Printable wedding planner bundles on Gumroad: $2.50 for a 10-page checklist, $9.99 for 108 pages, $21.95 for 110 documents (S, Gumroad listing snippets).
- **Repeat purchase.** One wedding, many items: save-the-date, invitation, details card, RSVP, menu, program, seating chart, thank-you card, plus trackers. The suite is the repeat.
- **Policy risk.** Low. No claims. Avoid trademarked fonts and licensed florals; AI disclosure on Etsy if the artwork is AI-made.
- **Verdict.** Rank 1. Largest documented per-occasion spend, buyers already on Pinterest and Etsy, product is a coordinated suite that an agent can produce in Canva-compatible form. Saturated at the invitation level; less so at the planning-tool level (unverified, see section 5).

### 2. Planner and productivity-system buyers, including the ADHD-labelled segment

- **Buyer.** Mostly women (Etsy: "penetration of approximately 30% among adults who identify as women, and approximately 10% among adults who identify as men", 10-K, P: https://www.sec.gov/Archives/edgar/data/1370637/000137063726000019/etsy-20251231.htm). GoodNotes has "Over 25 million monthly active users" (P: https://www.goodnotes.com/press).
- **Trigger.** New year, back to school, a diagnosis, a new job. Search interest for "digital planner" peaks each January and settles at roughly half that level by mid-year (T: accio.com Google Trends summary).
- **Evidence of spend.** US diaries and planners market "USD 2.3 billion in 2025" and "approximately 48% of American adults use a physical diary or planner" (T, market-report vendors, low confidence). Cricut's 3.09 million paid subscribers at $9.99+/month (10-K, P: https://www.sec.gov/Archives/edgar/data/1828962/000182896226000010/crct-20251231.htm) show the same demographic paying monthly for a craft content library. CDC: "an estimated 15.5 million U.S. adults (6.0%) had a current ADHD diagnosis", "approximately one half received the diagnosis at age ≥18 years" (S: https://www.cdc.gov/mmwr/volumes/73/wr/mm7340a1.htm, page 403s to curl).
- **Demand evidence.** TPT search "digital planner": "30,000 + results" (P, fetched teacherspayteachers.com/browse). Goodnotes ran a 2025 "Ultimate 2026 Planner" contest with a $50,000 prize that drew "50,000+ unique submissions" (T, businessmodelcanvastemplate.com, weak). Goodnotes marketplace "transaction volume was up approximately 50% in 2025" (T, same source, weak).
- **Supply saturation.** Etsy: "273,285 results" daily planner; "229,564" weekly planner; "38,704" blank digital planner; "86,291" adhd planner; "611,948" printable planners (S). Gumroad: 5,583 "digital planner", 960 "goodnotes planner", 3,050 "habit tracker", 1,370 "meal planner", 470 "adhd planner" (P). Notion: 812 weekly planner, 389 monthly planner templates (P: https://www.notion.com/templates/category/personal-planner).
- **Price band.** Etsy GoodNotes planners "from under $1 to around $20 for bundle options" (S). Goodnotes templates "$3-15, with complex planners or large bundles reaching $20-30" (T, kajabi.com). Gumroad first-page medians: digital planner $19.99, goodnotes planner $13.99, adhd planner $13.99 (P, n=9 each, indicative only). A "250+ Planner Mega Bundle MRR" at $8 with 55 ratings is the most-rated planner item Gumroad returned (P), which says the floor is being set by resold master-resell-rights bundles.
- **Repeat purchase.** High by design: dated planners expire, stickers and inserts are add-ons, and buyers switch systems. Etsy's habitual buyers ("spent $200 or more and made purchases on six or more days in the past 12 months") are 5.9M people, 7% of active buyers, about 40% of GMS (P).
- **Policy risk.** Medium. "ADHD planner" as a product name is common on Etsy (86,291 results, S), but any claim to treat, manage symptoms of, or improve a condition is a health claim. Write it as an organisation tool "designed around short tasks and visual cues" and never as a treatment. Etsy's prohibited-items page could not be read; listed in section 5.
- **Verdict.** Rank 2. Biggest repeat-buying population with documented monthly-subscription behaviour, but the most saturated category in the report. Win only with a sharp sub-niche (an occupation, a life stage) and an owned-store email list; do not enter with a generic "2027 digital planner".

### 3. Solo and micro business owners, trades and local services (operations kits)

- **Buyer.** The owner-operator. "29,811,495 nonemployer firms in the U.S., which represents 82.3 percent of all small businesses" (S: https://advocacy.sba.gov/wp-content/uploads/2025/06/United_States_2025-State-Profile.pdf). SWAE's own client list is this buyer: NSL Seamless Gutters, Precision General Construction, Rugged Ridge Contracting, Stumptown Detailing, Whitefish AutoGlass, Indigo Holiday Lighting, Gearshift Paint Booth, Glacier Shrink Wrap & Storage, Jewel Basin Storage, Zoomie Dog Bus, Val The Phone Gal, Mountain HR Consulting (P, SWAE Dashboard `list-clients`).
- **Trigger.** Formation. Census BFS 2025 business applications: 5,671,836 total; 1,708,842 high-propensity; NAICS 23 construction 519,090; NAICS 81 other services (repair, personal services) 483,258; NAICS 56 administrative and support (includes janitorial and landscaping services) 377,364; NAICS 54 professional services 764,007; NAICS 72 food and accommodation 300,236 (P, computed from https://www.census.gov/econ/bfs/csv/bfs_monthly.csv, non-seasonally-adjusted monthly sums). 2019 total was 3,498,990, so formations are running 62% above pre-2020.
- **Evidence of spend.** Realtors (a parallel owner-operator group) report "$9,530: Total median business expenses" (NAR, P: https://www.nar.realtor/newsroom/experienced-realtors-anchor-the-industry-as-housing-affordability-remains-top-hurdle-new-nar-report). Contractor estimating survey: "38% of contractors still rely on Excel or Google Sheets as their primary estimating tool. Another 9% use paper and a calculator"; "Solo operators use spreadsheets 51% of the time" (T: https://estimatorsuite.com/research/2026-contractor-software-adoption-survey/, vendor survey, n=287, recruited through trade subreddits, so weight it low). Jobber reports "Digital payments accounted for more than 51% of all Jobber-processed transactions during Q1 2026" across "400,000 service professionals" (S, prnewswire/getjobber.com). QuickBooks: larger small businesses "spending 25 hours a week on manual data entry and reconciling data across apps" (T, Intuit survey of 630 firms with 10 to 99 staff).
- **Demand evidence.** Etsy market pages exist for contractor_invoice_template, construction_invoice, general_contractor_invoice_template, business_estimate_templates, cleaning_contract_template, clean_bid_template, lawn_care_contract (S). Gumroad: 6,241 "small business", 905 "invoice template", 793 "contract template", 599 "proposal template", 1,195 "sales tracker" (P).
- **Supply saturation.** Generic business templates: saturated (Gumroad 6,241 "small business", Etsy bookkeeping spreadsheets "from a few dollars to around $50", S). Trade-specific: thin. Gumroad 130 "sop template", 417 "cleaning business", 200 "plumbing", 163 "hvac", 114 "landscaping", 99 "roofing", 49 "lawn care", 165 "inventory spreadsheet" (P). Most of those matches are courses and ebooks; operating documents are rare among them.
- **Price band.** Etsy: contractor invoice template $6.66, job estimate template $5.50 (S); cleaning business forms bundles with 6 to 13 documents, price not shown in snippets; SOP bundles (8 areas) by DapoDigital, price not shown (S). Gumroad first-page medians: invoice template $44 and contract template $50, but those pages are dominated by $120 to $200 "225 Construction Project Management Templates in Excel" style packs with 0 to 1 ratings (P). Realistic Etsy band $5 to $25 single, $25 to $60 bundle.
- **Repeat purchase.** Low on the document; high on the relationship. The kit is a lead product for SWAE's services (website care, GBP management, review responses), which `01` priced at $125 to $1,000/month.
- **Policy risk.** Medium. Contracts need a "not legal advice, review with your attorney, laws vary by state" line and must not be sold as state-compliant. Bookkeeping sheets must not claim tax outcomes. No AI-prompt packs.
- **Verdict.** Rank 3, and rank 1 for SWAE specifically because distribution exists. Honest limit: the marketplace price for these documents is low and trades mostly do not browse Etsy for them; the evidence of demand is formations and admin pain rather than template sales. Treat as a lead magnet and tripwire, with the service as the product.

### 4. Real estate agents (marketing and listing templates)

- **Buyer.** 1,438,569 NAR members; "86% of REALTORS® are independent contractors"; median gross income $59,200; members with two years or less earn a median of $8,000; "$9,530: Total median business expenses" (P, NAR newsroom URL above). This is the textbook spend-before-you-earn buyer: new agents with $8,000 income and marketing to do.
- **Trigger.** Licence, new brokerage, each listing, each month's social calendar.
- **Evidence of spend.** Median business expenses above. Agent marketing spend "ranges from $500-$2,500" (T, housingwire summary of the NAR profile).
- **Demand evidence.** Etsy "real estate templates": "59,625 results" (S, snippet of etsy.com/search). Etsy market page real_estate_social_media_graphics exists (S). Gumroad: 557 "real estate template" (P). Notion has a real-estate category (P, category page fetched, count not rendered).
- **Supply saturation.** High on Etsy (59,625). Monthly content calendars ("June Real Estate Social Media and Marketing Templates", S) show sellers already run a subscription-like cadence.
- **Price band.** Not captured in snippets; Etsy listings in this category cluster around $5 to $30 for packs and $30 to $80 for "all-in-one" branding kits (observation from listing titles only, unverified; see section 5).
- **Repeat purchase.** High (monthly calendars, seasonal packs, per-listing flyers).
- **Policy risk.** Medium: Fair Housing wording in templates, MLS and brokerage compliance, REALTOR® trademark use. Agents are regulated; copy must avoid steering language and must leave room for required disclosures.
- **Verdict.** Rank 4. Strong buyer, proven repeat behaviour, very saturated. Enter with a trade-adjacent angle SWAE knows (local SEO for agents, GBP posts for agents) rather than another Canva Instagram pack.

### 5. Job seekers (resume and cover letter templates)

- **Buyer.** Anyone applying. BLS JOLTS: hires "5.2 million" in August 2026, running 5.1 to 5.6 million every month this year (S: https://www.bls.gov/news.release/jolts.nr0.htm). Every hire sits on top of many applicants, so the resume-buying pool is several times larger than the hire count.
- **Trigger.** Layoff, graduation, promotion attempt. Year-round, with a January and May bump (T, general).
- **Evidence of spend.** The category leaders charge "$1.85 to $2.95" for a trial "that automatically converts to a recurring subscription of roughly $23.95 to $29.95" every four weeks, "13 charges per year instead of 12" (T: resufit.com, jobsolv.com, Trustpilot pages for zety.com and resume.io). "BBB, Trustpilot, PissedConsumer, and five separate subreddits all document the same billing and cancellation complaints going back to at least 2018"; "A pending federal antitrust suit now alleges this pattern is coordinated across resume brands" (T: resumezap.io, single secondary source for the suit; verify before quoting to anyone).
- **Demand evidence.** "resume template receives 74,000 monthly searches" (T, Etsy-tool blog, tool unnamed). Etsy market pages for resume_template, word_resume_template, best_resume_templates, modern_resume_templates; "ATS friendly" is the dominant listing hook (S).
- **Supply saturation.** High on Etsy (count not captured; see section 5). Gumroad: 1,920 "resume template" (P), the first page dominated by niche career kits (offshore work, plant operations, Germany-ready CV) at $19.99 to $29 (P), which is the signal: occupation-specific kits are where Gumroad sellers have gone.
- **Price band.** Etsy: "various price points" (S); typical listings $5 to $15 (observation, unverified). Gumroad first-page median $27 for kits (P, n=9).
- **Repeat purchase.** Low per person; cover letter, references page, LinkedIn banner and interview prep sheet are the natural bundle.
- **Policy risk.** Low. Do not promise interviews or ATS pass rates. Do not use "ATS-approved" (no such certification exists).
- **Verdict.** Rank 5. The gap is in the pricing model; the templates themselves are plentiful. An owned-store landing page that says "one price, no subscription, no trial" against named incumbents is the whole pitch. Etsy search alone will not carry it.

### 6. Teachers (classroom printables, planners, behaviour and SEL resources)

- **Buyer.** K-12 teachers. TPT: "over 7 million educators", "approximately 4 million teacher-created resources", "over 1.5 billion downloads" (T, Wikipedia and TPT marketing). TPT seller survey of "nearly 8,000 educators": "86% of teachers expect to spend the same or more on resources in the 2025-2026 school year"; "55% of teachers said disruptive behavior has been getting worse over the past two years" (P: https://sellerblog.teacherspayteachers.com/top-teacher-priorities-for-2025-26/).
- **Trigger.** August, January, and every new unit.
- **Evidence of spend.** "$895 is the average amount teachers spent out-of-pocket on school supplies during the 2024-2025 school year"; "median school supply budget provided by their school is $200"; "97% of teachers said their budget was not enough" (P: https://www.adoptaclassroom.org/2025/06/09/2025-teacher-survey-spending-stats-classroom-needs/).
- **Demand evidence.** TPT "digital planner" search: "30,000 + results" (P). Etsy market pages teacher_printables, classroom_printables, editable_school_supply_list (S).
- **Supply saturation.** Extreme (4 million TPT resources, T). Gumroad 6,015 "teacher" (P).
- **Price band.** TPT resources typically $1 to $10 (observation; TPT sets a $1 minimum for paid items, unverified).
- **Repeat purchase.** Very high; teachers buy per unit and per year.
- **Policy risk.** Medium. Curriculum content needs subject accuracy; standards alignment claims (Common Core, state standards) must be true. TPT is a separate platform with its own seller terms and sits outside the Etsy and Gumroad plan; TPT's AI policy was not read.
- **Verdict.** Rank 6. Proven spend and repeat, but the platform is TPT, not Etsy or Gumroad, and curriculum needs a teacher's review. Classroom-management and teacher-planner items (non-curricular) are the safe subset.

### 7. Nursing students and new nurses (report sheets, study organisers)

- **Buyer.** "328,443 people took the NCLEX-RN for U.S. licensure in 2025", "192,916" first-time US-educated candidates (P: https://www.ncsbn.org/public-files/2025_NCLEXExamStats_Final.pdf). Nursing enrolment "571,521 students in 2025" (T, nursa.com citing AACN).
- **Trigger.** Clinical placement, NCLEX date, first job.
- **Evidence of spend.** Study guide bundles sell at $49.99 on Gumroad; report sheets at $3.69 on Etsy (S, listing snippets). No aggregate spend figure found.
- **Demand evidence.** Multiple Gumroad storefronts dedicated to nursing study products (nursejanx, introvertrn, nursingknowledge, thenicugemini) (S/P).
- **Supply saturation.** Gumroad 750 "nurse" (P). Etsy count not captured.
- **Price band.** $3 to $5 report sheets; $15 to $50 study bundles (S/P).
- **Repeat purchase.** Medium: report sheet, then study guide, then new-grad kit.
- **Policy risk.** High for study content: clinical errors are a liability and "pass the NCLEX" claims are outcome claims. Low for report sheets and organisers (no clinical content).
- **Verdict.** Rank 7. Report sheets and shift organisers only. Study guides need a nurse reviewer; without one, exclude.

### 8. New parents and baby-shower hosts (milestone cards, shower games, trackers)

- **Buyer.** Parents and the friend hosting the shower. 3,606,400 US births in 2025 (S: https://www.cdc.gov/nchs/pressroom/releases/20260409.html, 403 to curl).
- **Trigger.** Pregnancy announcement, shower (month 6 to 8), birth, each monthly photo.
- **Evidence of spend.** First-year cost "$20,384" (T: BabyCenter via ConsumerAffairs). Registry gift givers spend "about $130" on average (T, Babylist via Tinybeans).
- **Demand evidence.** Etsy market pages milestone_printable, baby_milestone_printable, monthly_milestone_cards_printable, baby_milestone_cards (S). Gumroad 5,606 "baby" (P, mostly unrelated matches).
- **Supply saturation.** High (dedicated Etsy market pages for every sub-phrase).
- **Price band.** "under $3 to around $11 for complete sets" (S).
- **Repeat purchase.** Medium (shower set, then milestone set, then first-birthday set).
- **Policy risk.** Low. Avoid licensed characters.
- **Verdict.** Rank 8. Real occasion, cheap product, heavy supply. Only as a suite that follows the parent from shower to first birthday, sold from the owned store with email.

### 9. Students (Notion and GoodNotes dashboards, study planners)

- **Buyer.** College and high-school students. NRF back-to-college "$1,437.79" per household (S/T, nrf.com).
- **Trigger.** August and January.
- **Demand evidence.** Notion marketplace counts: Student Life 7,604, Study Planner 5,571, Career Building 2,880, Student Dashboards 1,620 templates (P: https://www.notion.com/templates/category/school). Gumroad 1,218 "student planner" (P).
- **Supply saturation.** Extreme, and the buyer expects free (Notion's gallery is mostly free duplicates).
- **Price band.** $0 to $10.
- **Repeat purchase.** Low; students graduate out.
- **Policy risk.** Low.
- **Verdict.** Rank 9. Demand is real and supply is free. Exclude as a paid niche; usable as a lead magnet to build a list that ages into the planner and resume buyers.

### 10. Cricut and Silhouette owners (SVG bundles)

- **Buyer.** "nearly 5.9 million Active Users", "nearly 3.7 million cut on their connected machines in the last 90 days", "just over 3.09 million Paid Subscribers" (P, Cricut 10-K).
- **Trigger.** Every project; holidays.
- **Evidence of spend.** 3.09 million people paying Cricut monthly for a library of "more than 1.6 million images" (P).
- **Demand evidence.** Etsy market pages svg_bundle, svg_bundle_for_cricut, svg_files_for_cricut_bundle, free_svg_files_for_cricut (S).
- **Supply saturation.** Extreme; bundles of "1600+ designs" at "$0.75 to $8.00" (S). Gumroad 495 "svg bundle" (P).
- **Policy risk.** High. The top Etsy results in the snippet include "Frozen character SVG" and "Minions SVG bundles" (S), which are infringing; takedowns and suspension follow. Cricut Access competes at $9.99/month for 1.6 million licensed images.
- **Verdict.** Rank 10. Exclude. The price floor is under a dollar, the competitor is the platform's own subscription, and the visible top sellers are IP violations.

### 11. Knowledge workers and "second brain" buyers (Notion templates)

- **Demand evidence.** Notion: "30,000+ Notion templates", Marketing 4,943, Design 2,816, Startup 2,743, Product 2,672, Engineering 1,078, AI 981 (P: notion.com/templates and /category/work). Gumroad 19,775 "notion template", 1,505 "second brain", 12,380 "productivity" (P).
- **Supply saturation.** The highest ratio of supply to buyer in the report. Notion's own marketplace takes 8% + $0.40 and is waitlist-gated (`01`, P).
- **Price band.** Gumroad first-page median $25 (P, n=9); the most-rated Notion item returned was "Headquarters Notion Productivity Template" at $79 with 200 ratings (P).
- **Verdict.** Rank 11. Defer. Only as a B2B variant (a Notion client portal or ops hub for a trade business) inside the rank-3 kit.

### 12. Photographers and illustrators (Lightroom presets, Procreate brushes) and fonts

- Gumroad 4,611 "lightroom presets", 10,894 "procreate brushes", 21,133 "font" (P). Etsy presets "70-75% off" with "750+" and "350+" bundles (S). Presets need photographic judgement, brushes need an illustrator's hand, fonts need foundry review (`01`). **Exclude.**

### Also considered and excluded

- **Crochet and knitting patterns.** Etsy market pages for every sub-type (S); buyers average age 58.8 with $100K household income and $70 to $81 average online spends (T, Craft Industry Alliance 2025 yarn survey). A pattern must be test-stitched; an agent cannot. Exclude.
- **AI prompt packs.** Banned on Etsy: "AI prompt bundles ... are banned" (S, etsy.com/seller-handbook/article/1275449912004 via aitrace.org and tomsguide.com). Exclude everywhere; Gumroad also bans resold PLR (`01`, P).
- **Anything sold with an outcome claim** (budget sheets that "get you out of debt", planners that "manage ADHD", study guides that "pass NCLEX", contracts that are "legally binding in all 50 states"). Exclude the claim, keep the product.

---

## 2. Customer profiles and purchase journeys (top four)

Each profile ends with what the agents produce. Chris approves every customer-facing artefact before it ships.

### Profile A: The DIY-leaning engaged couple

**Who.** Engaged, 24 to 34, one of the two (usually the bride in a mixed-sex couple, by Etsy's 30% vs 10% gender penetration, P) does the planning. Budget pressure is explicit: 37% contacted extra vendors to fit a budget (P). Gen Z is 41% of the market and uses TikTok 2.5x more than before (P). They have a Pinterest board with hundreds of pins before they buy anything (Pinterest: 16.7 billion saves, P).

**What they overspend on.** Coordinated paper: they buy an invitation template, then a details card, then a seating chart, then a welcome sign, each from a different seller, each $5 to $16, and redo the set when the colour palette changes. They also buy planning printables they never fill in (the 108-page planner at $9.99, S).

**Journey.**

1. *Discovery.* Pinterest search ("sage green wedding invitation", "wedding seating chart template"), pin saves, then Etsy search from the pin or directly on the Etsy app (45% of Etsy GMS is app, P). Secondary: TikTok "how I made my own invitations in Canva", Google "editable wedding invitation template Canva".
2. *Consideration.* Compares 5 to 10 listings in a tab row. Decides on: matching suite availability, "editable in Canva", preview with real paper mockups, reviews mentioning "easy to edit", and whether the fonts are included. Fear: "will it look cheap", "can I edit it on my phone".
3. *Purchase.* Buys the invitation first, on sale (most listings show 20 to 75% off, S). Price band $8 to $16 for a suite, $3 to $6 for a single card.
4. *Use.* Opens the Canva link, hits a Pro element watermark or cannot find the font, messages the seller, requests a refund if the reply is slow (T: goldcityventures; "Buyers on Free Canva opening templates and seeing watermarks on every Pro element is a common issue"). Prints at home or uploads to a print service.
5. *Repeat.* Returns to the same shop for the details card, RSVP, menu, program, seating chart, thank-you, "if the first one worked". Then the shower and bachelorette hosts buy games from the same palette.

**Agents produce.**

- *Product spec.* One palette, one type pairing, 12 to 15 coordinated pieces delivered as Canva templates (free-tier elements only, fonts that ship free in Canva), plus PDF print-ready versions at 5x7 and A5, plus a Google Sheets planning pack (budget by The Knot's category breakdown, guest list with RSVP and dietary, seating chart, vendor tracker with the 13-vendor average, day-of timeline). Each file named with the piece and size.
- *Listing copy angle.* "Everything matches. Edit on your phone. Nothing in this kit needs Canva Pro." Lead with the suite, list the pieces, show the print sizes, state the editing tool, state the AI disclosure sentence if any artwork is AI-generated, and add the refund rule in plain words.
- *Preview images.* Image 1: the invitation on textured paper with an envelope and a ribbon, overhead, natural light (the Etsy norm). Image 2: the full suite laid out as a flat lay with every piece labelled. Image 3: a phone showing the Canva editor with the template open. Image 4: a "what's included" grid. Image 5: the spreadsheet on a laptop. Image 6: colour variants. Add a 10-second video of the template being edited.
- *Email flow (owned store).* Lead magnet: free wedding budget spreadsheet keyed to the $34,000 average and 117 guests. Email 1 (day 0): download plus "which season is your wedding". Email 2 (day 3): the 13 vendors to book, in order. Email 3 (day 7): invitation suite, 20% code. Email 4 (day 21): seating chart and day-of pieces. Email 5 (30 days before the date, if captured): thank-you cards. Pinterest: pin every preview image to a board per palette.
- *Lead magnet.* The budget sheet above, and a free "wish card template" (Pinterest +205%, P) that matches the suite.

### Profile B: The planner-system switcher (including the ADHD-labelled buyer)

**Who.** Woman, 25 to 45, owns an iPad or prints at home, has bought three planners in two years and used each for six weeks. May have an adult ADHD diagnosis (half of the 15.5 million diagnosed adults were diagnosed as adults, S) or self-identify with it. Buys on Etsy, TikTok Shop, Gumroad, and the GoodNotes in-app marketplace. Pays monthly for apps already.

**What they overspend on.** The new system. Dated planners that expire, sticker packs, "all-in-one life OS" bundles with 500 pages they will never open, and master-resell-rights mega bundles at $8 (the most-rated planner result on Gumroad, P).

**Journey.**

1. *Discovery.* January and August spikes (T). TikTok "plan with me" and "ADHD planner that finally worked" videos; Pinterest "digital planner GoodNotes aesthetic"; Etsy search "adhd planner" (86,291 results, S), "goodnotes planner 2027".
2. *Consideration.* Looks for: hyperlinked tabs, a video of someone flipping through it, "undated" (so it does not expire), a sticker set, and reviews saying "I still use this months later". Fear: "another one I abandon".
3. *Purchase.* $8 to $25. Buys the bundle when the single is $12 and the bundle is $19.
4. *Use.* Imports to GoodNotes or prints. Abandons within weeks if the daily page is too dense. Blames the planner, searches again.
5. *Repeat.* Buys the next system, or (the good outcome) buys the refill, the next year, the matching sticker pack, and the companion for the specific life area (meal, budget, cleaning).

**Agents produce.**

- *Product spec.* One hyperlinked PDF planner for GoodNotes and Notability (undated, 12 month tabs, weekly on one page, a "three things today" daily page), a printable US Letter and A5 version, a sticker PNG pack, and a 5-minute setup video. Sub-niche it by occupation or life stage (a nurse's shift planner, a teacher's week, a solopreneur's week) rather than by aesthetic. For the ADHD-labelled variant: short task boxes, visual timers, a "brain dump" page. Describe the design, never the condition's treatment.
- *Listing copy angle.* "Undated, so it starts the week you buy it. One page a week. Nothing to set up." Name the apps, name the devices, say "a PDF you keep, with no app subscription".
- *Preview images.* Image 1: the planner on an iPad with an Apple Pencil, a partially filled week in handwriting. Image 2: the tab system, annotated. Image 3: the weekly page close up. Image 4: "what's included" grid. Image 5: the printed version on a desk. Video: a 15-second flip-through tapping tabs. This is the established top-seller format on Etsy (S, listing snippets).
- *Email flow.* Lead magnet: a free one-page weekly (the "three things" page). Email 1: the free page and the one rule for using it. Email 2 (day 2): the flip-through video. Email 3 (day 5): the planner, with the bundle $5 above the single. Email 4 (day 14): "still using the page?" with the sticker pack. Monthly: one new free page, which is the retention mechanism and the repeat trigger. December: the next year's dated cover insert.
- *Lead magnet.* The free weekly page; on Gumroad, pay-what-you-want at $0+.

### Profile C: The owner-operator in a trade or local service (SWAE's own buyer)

**Who.** Owns a gutter, construction, detailing, auto-glass, holiday-lighting, storage or cleaning business with 1 to 5 staff. Formed in the last five years (formations up 62% on 2019, P). Estimates in a spreadsheet or on paper (47% of surveyed contractors, T, weak), invoices from a phone, keeps SOPs in their head. Spends on trucks, tools, software, and marketing when a slow month scares them. Already a SWAE client, or looks like one.

**What they overspend on.** Software they do not configure, lead-gen services that do not deliver, and marketing that is not measured. They underspend on documents, which is why this gap is poorly served: nobody sells a $29 kit because the buyers do not look for it. Etsy prices for cleaning-business form bundles ($5 to $7, S) confirm the ceiling on the document alone.

**Journey.**

1. *Discovery.* Not Etsy. SWAE's newsletter and site, a Google search in a panic ("roofing estimate template excel", "cleaning business contract template"), a Facebook trade group, YouTube.
2. *Consideration.* Wants it today, on the phone, in Google Sheets or a PDF they can fill in. Fear: "is this legal", "does it work on my phone", "do I look professional".
3. *Purchase.* $19 to $49 for a kit; $0 for a lead magnet in exchange for an email.
4. *Use.* Uses the estimate and invoice sheet immediately if it is pre-filled with their trade's line items (gutter: linear feet, downspouts, guards; detailing: packages by vehicle size). Never opens the SOP binder unless onboarding a hire.
5. *Repeat.* The repeat is the SWAE service: website care, GBP posts, review responses, a monthly report. The kit's job is to prove SWAE understands the trade.

**Agents produce.**

- *Product spec.* Per trade, a Google Sheets estimate and invoice workbook with the trade's own line items and a tax field; a Google Docs service agreement with a "not legal advice" line and blank state fields; a review-request text and email script set; a GBP post calendar (52 posts, seasonal to the trade and to Montana weather where that is the client's market); a hiring packet (job ad, interview sheet, first-week checklist); a one-page "what to send a customer when" SOP. Deliver as a Drive folder link plus a ZIP.
- *Listing copy angle.* "Built for [trade], with your line items already in it. Opens on your phone." On the owned store only; on Etsy only the invoice and contract pieces, at Etsy's price band.
- *Preview images.* Image 1: the estimate sheet on a phone in a work truck. Image 2: the workbook on a laptop with the trade's line items visible. Image 3: the folder contents as a grid. Image 4: the review-request text as a phone screenshot. No stock-photo tradesmen in clean shirts.
- *Email flow.* Lead magnet: the single trade estimate sheet. Email 1: the sheet and how to add a line item. Email 2 (day 3): the review-request script. Email 3 (day 7): the full kit at $29 to $49. Email 4 (day 21): "your Google Business Profile has not posted in X days" with the service offer. This flow is the bridge into pick 1 in `01`.
- *Lead magnet.* The trade estimate sheet, free.

### Profile D: The job seeker who has been burned by a resume subscription

**Who.** 22 to 45, applying for 20 to 100 jobs, has already paid a $2.95 "trial" and found a $25.95 charge four weeks later (T, multiple secondary sources). Searches on Google and Etsy, reads Reddit threads about "ATS", wants one file they own.

**What they overspend on.** Subscriptions they forgot to cancel, "ATS-approved" claims, and paid resume reviews.

**Journey.**

1. *Discovery.* Google "resume template free", "ATS resume template Word"; Etsy search "resume template"; TikTok "why your resume is getting rejected".
2. *Consideration.* Wants Word and Google Docs, a cover letter, "ATS friendly", and no subscription. Fear: "will the formatting break", "is this another trap".
3. *Purchase.* $5 to $15 on Etsy; $9 to $29 for an occupation-specific kit on Gumroad (P, first-page kits at $19.99 to $29).
4. *Use.* Edits in Google Docs, exports PDF, applies. Comes back for a cover letter when they get an interview.
5. *Repeat.* Low; the natural bundle is resume plus cover letter plus references plus a LinkedIn banner, and the natural upsell is a one-off human review (which SWAE could price as a service).

**Agents produce.**

- *Product spec.* One single-column ATS-safe layout in Word, Google Docs and Pages; matching cover letter and references page; a one-page "how to tailor this in 10 minutes" guide; occupation variants (trades, nursing, teaching, sales, admin) with the section order and verbs that fit each. No "ATS-approved" wording, no interview promises.
- *Listing copy angle.* "One price. Yours forever. No trial, no subscription." Name the formats. On the owned-store landing page, state the comparison against the four-week subscription model without naming competitors in a defamatory way: quote their own published prices.
- *Preview images.* Image 1: the resume on a plain background with a cover letter beside it. Image 2: the Google Docs editor open. Image 3: the three formats as icons. Image 4: the occupation variants. Image 5: "what's included".
- *Email flow.* Lead magnet: the free references page or the tailoring guide. Email 1: the file. Email 2 (day 2): the five formatting mistakes that break parsers (sourced to a named ATS vendor's docs, or cut). Email 3 (day 4): the kit. Email 4 (day 10): the cover letter add-on.
- *Lead magnet.* The tailoring guide.

---

## 3. Unserved and poorly served gaps

Each gap states the demand evidence, the supply evidence, and whether the buyers pay.

1. **Trade-specific operations kits (gutters, roofing, detailing, auto glass, holiday lighting, storage, cleaning, lawn care).** Demand: 519,090 construction and 483,258 other-services business applications in 2025 (P); roughly half of small contractors estimate in spreadsheets or on paper (T, weak); SWAE has a dozen such clients (P). Supply: Gumroad 49 "lawn care", 99 "roofing", 114 "landscaping", 163 "hvac", 200 "plumbing" (P), mostly courses; Etsy has cleaning and lawn-care contract pages at $5 to $7 (S). **Do buyers pay?** Little, for the document. They pay for software ($40 to $200/month) and for marketing. The gap is real and the direct revenue is small; the value is the list and the service upsell. Say so in the plan.
2. **One-time-purchase resume kits positioned against subscription traps.** Demand: 5.2 million hires a month (S), documented complaint history against the category leaders (T). Supply: heavy on templates, nobody is selling the pricing model as the product. **Do buyers pay?** Yes, $5 to $29, once. Needs an owned-store landing page and Google traffic; Etsy search will bury it.
3. **Occupation planners (nurse shift planner, teacher week, solopreneur week) instead of aesthetic planners.** Demand: 328,443 NCLEX candidates (P), 7 million TPT educators (T), 29.8 million nonemployer firms (S). Supply: "adhd planner" 86,291 on Etsy (S) versus 750 "nurse" on Gumroad (P); the aesthetic axis is saturated, the occupation axis less so (Etsy counts for "nurse planner" and "teacher planner" not captured; see section 5). **Do buyers pay?** Yes, $8 to $25, and they repeat yearly.
4. **Wedding planning tools (budget, guest, seating, vendor trackers) as a set, separate from invitations.** Demand: 2 million weddings, $34,000 average, 13 vendors (P). Supply: wedding printable planners exist at $2.50 to $21.95 (S), invitations are saturated; the spreadsheet-and-tracker set that matches the invitation suite is less common (unverified count). **Do buyers pay?** Yes, inside the suite; standalone trackers sell at $2 to $10.
5. **Delivery experience for digital buyers.** Demand: the most common support tickets are "can't download on the Etsy app", "didn't get all the files", "Canva says Pro" (T, goldcityventures and Etsy community threads). Supply: almost no seller fixes this. **Do buyers pay?** Not directly; it cuts refunds and raises reviews. On the owned store, deliver by email with a landing page and a short "open it here" video; on Etsy, put the mobile-app warning and a Canva-free-tier promise in image 2 and the first line of the description.
6. **Real estate agent local-SEO content kits (GBP posts, neighbourhood pages, review scripts).** Demand: 1.44 million agents, $9,530 median expenses, two-year agents earning $8,000 (P). Supply: 59,625 Etsy results for real estate templates (S), nearly all Instagram and flyer packs; GBP and local-search kits are rare (unverified). **Do buyers pay?** Yes, and monthly, but they are a regulated buyer and the copy must be Fair-Housing safe.
7. **Gaps that exist because buyers do not pay.** Student dashboards (Notion lists 7,604 free Student Life templates, P), generic Notion productivity systems (19,775 on Gumroad, P), SVG bundles (sub-$1 floor, S), and "AI prompt" products (banned on Etsy, S). Do not read thin paid supply in these as opportunity.

---

## 4. Product and design directives for the agents

**Formats.**
- Canva: share a template link; use only free-tier elements and fonts; test in a Canva Free account before listing. "Most Etsy buyers are on Canva Free and have never edited a template" (T, goldcityventures).
- Spreadsheets: Google Sheets link plus XLSX; formulas locked on calculation cells; an "Instructions" tab first (the best-reviewed Etsy budget sheets all have one, S).
- Planners: hyperlinked PDF for GoodNotes and Notability, plus a printable PDF at US Letter and A5; PNG sticker packs; undated by default with a dated cover insert each December.
- Documents: Google Docs plus DOCX plus PDF; contracts carry a plain "not legal advice; laws vary by state; have an attorney review" line.
- Notion: a duplicate link, plus a 3-minute setup video. Notion's marketplace needs waitlist approval and takes 8% + $0.40 (`01`, P), so sell from Gumroad or Shopify and host the template on a Notion page.
- Delivery: on Etsy, a single PDF in the download that contains the links (links break less than ZIPs on mobile); on the owned store, email delivery with a landing page and a short "open it here" video.

**Previews (what top sellers look like, S from listing snippets and market pages).**
- Image 1 is the product in use on the real surface: paper with props for wedding, an iPad with a pencil for planners, a phone for business forms, a laptop for spreadsheets.
- Image 2 is "what's included" as a labelled grid.
- Image 3 is the editor open (Canva or GoodNotes) to prove editability.
- One image states compatibility and the non-Pro promise in large type.
- A 10 to 15 second video (flip-through or editing) on every listing.
- Colour variants shown together in one image rather than as separate listings.
- No stock photos of people; no AI-generated hands or text in mockups.

**Pricing ladders.**
- Single piece $3 to $9; suite or planner $12 to $25; bundle $25 to $49; B2B kit $29 to $49 on the owned store, with the single trade sheet free as the lead magnet.
- Keep the Etsy "sale" convention (a struck-through price) since nearly every top listing uses it (S), without making the discount the identity of the shop.
- Gumroad: pay-what-you-want with $0 minimum for lead magnets; Gumroad keeps its 10% + $0.50 on refunds (T), so refund rarely and preempt with previews.
- Set the bundle $5 to $7 above the single to pull buyers up.

**Bundling.**
- Wedding: suite plus trackers. Planner: planner plus stickers plus companion (meal, budget, cleaning). Trades: estimate plus contract plus scripts plus calendar. Resume: resume plus cover letter plus references plus LinkedIn banner. Baby: shower plus milestone plus first birthday.
- Cross-niche: the planner buyer who is also a solopreneur; the wedding buyer who becomes the baby buyer. Tag the list by purchase and move them along.

**What gets refunded or reported (T unless marked).**
- Canva Pro elements showing watermarks; "I thought it was editable"; missing fonts; ZIP will not open on phone; "can't download in the Etsy app"; corrupted or missing pages (an Etsy Purchase Protection case: "If a file is corrupted, blurry, or missing pages, that is still a valid Purchase Protection case", S; cases allowed "for 100 days from the first download, or within 12 months of purchase, whichever comes first", S; "buyers must download the item before opening a case", S).
- Reports: licensed characters and brand names in SVGs and clipart; missing AI disclosure under Etsy's Creativity Standards ("sellers must disclose within their listing description if an item is created with the use of AI", S; attribute "Designed by a seller", S); copied templates; medical, legal or financial outcome claims; earnings claims (Gumroad bans "false or unsubstantiated claims about a Product or its outcomes", `01`, P).
- Prevention: a "before you buy" image, a compatibility line in the first sentence, test every file on a phone, and a scripted first reply that sends the file by email before any refund discussion.

**Copy rules.** Plain claims only. No "ATS-approved", no "manage your ADHD", no "pass the NCLEX", no "legally binding", no "get out of debt". State what is in the file, what it opens in, and what it does not need.

---

## 5. Unverified claims and sources needing a manual browser read

**Etsy pages (403 to every fetch; grade S or T above).**
- https://www.etsy.com/legal/creativity (Creativity Standards; the AI disclosure wording and "Designed by a seller").
- https://www.etsy.com/seller-handbook/article/1275449912004 (Etsy's stance on AI creations; prompt-bundle ban).
- https://www.etsy.com/legal/policy/cases-policy/243306189901 (Cases policy; 100-day window and download-before-case rule).
- https://help.etsy.com/hc/en-us/articles/360024112614-What-Can-I-Sell-on-Etsy and the prohibited-items policy (medical and health claim rules relevant to ADHD planners).
- https://www.etsy.com/legal/fees (digital listing and renewal fees).

**Etsy result counts to read in a browser (searches not completed; budget exhausted).** "wedding invitation template", "wedding planner template", "notion template", "resume template", "budget spreadsheet", "invoice template", "contractor invoice template", "cleaning business forms", "nurse report sheet", "nurse planner", "teacher planner", "baby milestone cards", "baby shower games", "sop template", "contract template", "canva instagram templates", "svg bundle", "crochet pattern", "lightroom presets", "goodnotes planner", "student planner", "real estate social media templates". The eight counts quoted above (adhd planner 86,291; real estate templates 59,625; printable planners 611,948; daily planner 273,285; weekly planner 229,564; blank digital planner 38,704; vertical weekly planner 31,026; undated weekly planner in art 1,900) came from Google snippets of etsy.com/search pages and carry no date.

**Third-party figures that should not be repeated to a client without a primary source.**
- Goodnotes marketplace "$48M" sales, "72,000" listings, "+50%" transaction volume, "50,000+" contest submissions (businessmodelcanvastemplate.com; Goodnotes' own press page gives only "Over 25 million monthly active users", P).
- "US diaries and planners market USD 2.3 billion" and "48% of American adults use a physical planner" (market-report vendors).
- "resume template receives 74,000 monthly searches" (Etsy-tool blog, tool unnamed).
- The pending federal antitrust suit against resume-builder brands (resumezap.io only).
- EstimatorSuite contractor survey (vendor, n=287, Reddit-recruited).
- BabyCenter $20,384 first-year cost (via ConsumerAffairs; babycenter.com not fetched).
- TPT "7 million educators", "4 million resources", seller-earnings distribution (Wikipedia and SEO blogs; TPT's own survey page is P only for the 2025-26 survey percentages).
- Nursing enrolment 571,521 (nursa.com citing AACN; AACN page not fetched).
- InsightRaider's $72/month Gumroad median (carried over from `01`, T).

**Pages that returned 403 or JS-only to curl this session.** cdc.gov (births release and the ADHD MMWR page), creativemarket.com, elements.envato.com, creativefabrica.com, getjobber.com reports, consumeraffairs.com, goodnotes.com/marketplace (404), notion.com/templates/category/life and /small-business (404; the category slugs that worked were /school, /work, /personal-planner, /real-estate, /side-hustle).

## Pages read in full this session (primary)

- Etsy FY2025 10-K: https://www.sec.gov/Archives/edgar/data/1370637/000137063726000019/etsy-20251231.htm
- Etsy Q2 2026 shareholder letter: https://www.sec.gov/Archives/edgar/data/0001370637/000137063726000079/q226shareholderletter.htm
- Cricut FY2025 10-K: https://www.sec.gov/Archives/edgar/data/1828962/000182896226000010/crct-20251231.htm
- The Knot Worldwide 2026 Real Weddings Study release: https://www.theknotww.com/press-releases/the-knot-worldwide-unveils-2026-real-weddings-study
- Pinterest Wedding Trends Report 2026: https://newsroom.pinterest.com/news/wedding-trend-report-2026/
- Census Business Formation Statistics monthly CSV: https://www.census.gov/econ/bfs/csv/bfs_monthly.csv (annual sums computed)
- NAR 2026 Member Profile release: https://www.nar.realtor/newsroom/experienced-realtors-anchor-the-industry-as-housing-affordability-remains-top-hurdle-new-nar-report
- AdoptAClassroom 2025 Teacher Spending Survey: https://www.adoptaclassroom.org/2025/06/09/2025-teacher-survey-spending-stats-classroom-needs/
- NCSBN 2025 NCLEX statistics PDF: https://www.ncsbn.org/public-files/2025_NCLEXExamStats_Final.pdf
- TPT seller survey 2025-26: https://sellerblog.teacherspayteachers.com/top-teacher-priorities-for-2025-26/
- TPT search page (digital planner, 30,000+ results): https://www.teacherspayteachers.com/browse?search=digital+planner
- Notion marketplace: https://www.notion.com/templates, /templates/creators, /templates/category/work, /templates/category/school, /templates/category/personal-planner
- Goodnotes press page: https://www.goodnotes.com/press
- Gumroad search endpoint, 70 queries: https://gumroad.com/products/search?query=... (counts saved in scratchpad `gumroad_counts.json` and `gumroad_prices.json`)
- EstimatorSuite contractor survey (vendor): https://estimatorsuite.com/research/2026-contractor-software-adoption-survey/
- SWAE Dashboard client list (internal MCP, `list-clients-tool`)
