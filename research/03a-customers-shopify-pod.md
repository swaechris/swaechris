# Who buys dumb merch, and what to sell them: customer profiles for an agent-run Shopify POD store

Prepared for Chris DeWitt, SWAE Marketing. Research date: 2026-10-05. All URLs accessed 2026-10-05. Builds on `01-income-options.md` section 1 (owned Shopify store, Printful/Printify APIs, demand is the bottleneck, net 20 to 35% on tees per Printful's own margin table).

## How to read this

**Evidence grades.** **P** = primary page fetched in full this session via curl through the session proxy (stripped text saved under the session scratchpad `pages/`). **S** = the fact appeared in a search-result snippet from the originating domain and the page itself could not be fetched. **T** = secondary (trade press, aggregator, vendor blog). Every number below carries one of these.

**Tooling notes, so nobody repeats the dead ends.**
- Semrush MCP: `keyword_research` returned `no_api_units` ("The user has an active Semrush subscription, but does not have enough API units"). No search-volume data in this report. Units can be added at https://www.semrush.com/mcp-access.
- Firecrawl: "Insufficient credits" on the first scrape. Not used.
- WebSearch: the session hit its 200-call budget two-thirds of the way through. Everything after that point is curl only. Items that would have been one more search are listed in section 5.
- Google Trends: `trends.google.com` returned HTTP 429 on both attempts (API and explore page). No trend curves here; the one search-interest figure is from Axios citing Google data (T).
- Marketplace supply counts: etsy.com (search and /market pages), redbubble.com, teepublic.com, zazzle.com and spreadshirt.com all returned 403 to curl with desktop and mobile user agents and via r.jina.ai. **amazon.com search pages returned 200 with `--compressed`**, so supply counts below are Amazon result counts (P), with the query and the department filter stated. Amazon counts are "over N" buckets, not exact, and the two batches used different department filters (noted per figure). Etsy supply is described from Google-indexed /market page snippets (S) and from the fact that Etsy auto-generates a /market page only when a query has enough listings.
- Process note: the global rule to run a skeptic agent in parallel could not be followed inside this subagent (no Agent tool). The parent session should run one against sections 1 and 3 before anything here drives spend.

**What "gullible" means here, operationally.** Chris's words were "the most gullible types/niches of people who throw their money away on dumb crap". Read as a buyer profile, that is: (a) identity-first, the hobby or role is who they are; (b) in a group that sees the merch (club, course, jobsite, show ring, coop tour); (c) with disposable income or a gift-buyer who has it; (d) buying on impulse from a joke or a flag of belonging; (e) buying repeatedly because the hobby has seasons, events and new in-jokes. Every niche below was scored on those five, on spend evidence, on supply saturation, and on whether it can be done inside Printful's Acceptable Content Guidelines, Printify's Terms and IP Policy, and Shopify's AUP (all fetched, P, quoted in section 4).

---

## Executive summary

1. **Pickleball is the best first niche.** 24.3 million US players in 2025 (SFIA, P), median household income reported at $112K (T), a tight in-group vocabulary (dink, kitchen, "it was in", 3.5 rating), club and league play that makes merch visible, and thin supply beyond t-shirts: Amazon shows "over 4,000" results for `pickleball shirt` but only 414 for `pickleball hoodie` and 658 for `pickleball mug` (P). Search interest fell about 10% in 2025 (Axios citing Google, T), so this is a mature, large niche past its fastest growth. Verdict: pursue.
2. **Backyard chicken keepers are the most under-estimated spenders.** 11 million US households keep chickens, up 28% from 2023 (APPA via Pet Age and Good News for Pets, T, S); L.E.K. counts about 17 million (T). Keepers are mostly women 45 to 64 with household incomes over $100K (academic surveys, T). "Chicken lady" merch is saturated on Amazon ("over 60,000"), but `backyard chickens shirt` returns 840 (P), and the humour register (chicken math, henopause, "hold my drink I gotta pet this chicken") is the kind of in-joke that sells. Verdict: pursue, with home goods and mugs ahead of tees.
3. **Linemen and skilled trades are the clearest unserved high-income gap.** Power-line installers earn a median $95,320 (BLS via snippet, S; bls.gov 403s to curl), 127,400 of them, plus 821,000 electricians at a $63,190 median (S). Amazon returns "over 1,000" results for `lineman shirt` against "over 20,000" for `nurse shirt` (P). The sitting proof that this audience buys identity merch is Lineman Probs ("over 50,000 orders and over 500,000 followers", T). The main slogan in the space ("Dirty Hands Clean Money") belongs to Troll Co and must not be used. Verdict: pursue, hoodies and hats, gift-buyer (spouse) angle.
4. **Golf has the richest buyers and the worst saturation.** 48.1 million participants, 29.1 million on-course (NGF, P); regular golfers' household income over $100K (T). But `golf gift` returns "over 300,000" Amazon results and `golf shirt funny` "over 8,000" (P), and the Amazon first page is owned by moisture-wicking printed polos at $22 to $30 from Chinese labels (P). Augusta National and the PGA TOUR enforce hard (T). Verdict: test only with all-over-print polos for a specific sub-group (women golfers, up 46% since 2019, NGF P), never generic.
5. **Birders are the quietest big-spend group.** 96 million Americans birded in 2022 and spent $107.6 billion, $93 billion of it on gear (FWS, P). Average age 49, income above average (FWS, P). Amazon has "over 1,000" `birding shirt` results and the designs are text jokes on blank tees (P). Verdict: test, with posters, mugs and illustrated species designs rather than tees.
6. **Dog owners are a volume play that only works breed by breed.** 71 million dog households, $158 billion industry (APPA, P). `dog mom shirt` returns "over 10,000" (P). Breed names are generic terms and free to use (T). Verdict: test with three or four breeds whose owners are famous for over-identifying (dachshund, golden retriever, corgi, French bulldog) and skip "dog mom".
7. **Avoid**: nurses (over 20,000 Amazon results, P), teachers (over 50,000, P), grandma/grandpa as a standalone (over 50,000 each, P; good as a gift overlay), RV/camping (over 60,000, P), homestead-generic (over 20,000, P), western/cowboycore (Boot Barn at $2.25 billion revenue and 500+ stores means real brands own the look, T; "Yellowstone" is a trademark), gym/powerlifting (brand-dominated, and "CrossFit" is an instant takedown, T), any licensed fandom or team.
8. **Average order value expectation:** Amazon first-page prices cluster at $15 to $25 for tees and $35 to $45 for hoodies and sweatshirts across every niche fetched (P). A Shopify store cannot win at $15. Price tees at $28 to $34, sweatshirts at $45 to $55, mugs at $18 to $22, posters at $25 to $40, and use two-item bundles (shirt plus mug, hoodie plus sticker sheet) to lift AOV to $45 to $60. That is the only way the 20 to 35% net margin table from `01-income-options.md` survives any paid traffic.
9. **Seasonality** is gift-driven in every niche: Mother's Day $34.1 billion, $259.04 per celebrant (NRF, P); Father's Day $27.9 billion in 2026, $226.58 per celebrant (NRF, P); Q4 for everything. Niche-specific peaks: Nurses Week (May 6 to 12), Masters week (April, do not touch the IP), lake season (May to August), hunting season (September to December), chick season (February to April when feed stores sell chicks), pickleball's spring league start.
10. The single most useful design finding across all niches: the Amazon first page is dominated by **text-only jokes on blank tees at $15 to $20 from anonymous labels**. Etsy's indexed pages show the differentiators that command $25 to $35: Comfort Colors garment-dyed blanks, "In My ___ Era" and "Easily Distracted By ___" templates, boho floral and line-art illustration, rhinestone and embroidery looks, and personalization (names, lake names, dog names). The agents should produce illustrated, specific, in-joke designs on premium blanks, never one-line text on a Gildan.

---

## 1. Ranked niche candidates

Scoring: Spend = documented money in the hobby. Identity = how much the hobby is who they are. Visibility = whether the merch gets seen by the in-group. Gap = demand relative to quality of current supply. IP = policy and trademark exposure. All 1 to 5, 5 best (for IP, 5 = safest).

| # | Niche | Spend | Identity | Visibility | Gap | IP | Verdict |
|---|---|---|---|---|---|---|---|
| 1 | Pickleball players (club and league) | 4 | 5 | 5 | 3 | 4 | Pursue |
| 2 | Backyard chicken keepers | 3 | 5 | 3 | 4 | 5 | Pursue |
| 3 | Linemen and skilled trades (plus their spouses) | 4 | 5 | 5 | 4 | 3 | Pursue |
| 4 | Golfers, sub-segmented (women, dad-golf, league night) | 5 | 4 | 5 | 1 | 2 | Test |
| 5 | Birders | 5 | 4 | 2 | 4 | 5 | Test |
| 6 | Dog owners, breed-specific | 5 | 5 | 3 | 2 | 4 | Test |
| 7 | Lake and pontoon boat owners | 4 | 4 | 4 | 3 | 4 | Test |
| 8 | Fly fishing and trout anglers | 4 | 5 | 3 | 3 | 3 | Test (Montana tie-in) |
| 9 | Horse girls and horse owners | 3 | 5 | 4 | 2 | 4 | Test small |
| 10 | Bourbon dads | 3 | 4 | 2 | 3 | 2 | Test small, Father's Day only |
| - | Nurses, teachers, grandparents, RV, homestead-generic, western, gym, hunting-generic, any fandom | | | | | | Avoid as primary (reasons per entry) |

### 1. Pickleball players

- **Who buys:** 24.3 million US players in 2025, up 22.8% on 2024; 7.48 million "core" players (8+ times a year); 57% male, 43% female; strong in 25 to 44 and 65+ (SFIA pickleball report page, P, https://sfia.org/research/u-s-pickleball-participation/). The APP's broader count is 48.3 million adults who played at least once, "more than 70% of avid pickleball players are between the ages of 18 and 44" (APP, P, https://www.theapp.global/news/nearly-50-million-adult-americans-have-played-pickleball). Median household income $112K, with 50% at $100K+ (brandedpickleball.com aggregating SFIA/Pickleheads, T, https://brandedpickleball.com/stats/pickleball/demographics). Income disparity score improved from 2.83 (2019) to 1.90 (2022), meaning higher-income players still play about twice as often (Pickleball Union citing SFIA/Pickleheads report, T, https://pickleballunion.com/income-disparity-pickleball/).
- **Why they buy merch:** in-group humour (the vocabulary is the joke: dink, kitchen, "it was in", "0-0-2", Erne, ratings 3.0/3.5/4.0), club identity (round-robins, leagues, Facebook groups per court complex), gifting (spouses and adult children buying for the parent who "won't shut up about pickleball"), and gear habit: Amazon paddle sales rose 55% to roughly $44 million in 2025 with buyers "choosing higher-priced paddles more often" (The Dink, P, https://www.thedinkpickleball.com/amazon-pickleball-paddle-sales-up-55-in-2025-surge-to-44-million/). Apparel sales at tournaments up 47% since 2021 and a US apparel market of about $187 million in 2024 (market-research vendors, T, low confidence).
- **Supply:** Amazon `pickleball shirt` (fashion dept) "over 4,000"; `pickleball t-shirt funny` "over 1,000"; `pickleball hoodie` (all depts) 414; `pickleball mug` 658; `pickleball gift` (fashion dept) "over 60,000" (P, all fetched 2026-10-05). Etsy has auto-generated /market pages for `funny_pickleball_shirt`, `rhinestone_pickleball_shirts`, `pickleball_apparel`, `pickleball_shirts_neon`, `custom_pickleball_t` (S), which means each has enough listings to index; the snippets show cartoon geese, "it's a good day to play PICKLEBALL" in rainbow text, "Playing Pickleball Improves Memory", "002" and "IT WAS IN" designs, prices $21.99 to $30 (S).
- **Gap:** tees are crowded with generic puns; hoodies, mugs, posters and club-specific or rating-specific humour are thin. Nobody on the first Amazon page is doing illustrated, premium-blank designs.
- **IP risk:** "pickleball" is a generic sport name. Do not use USA Pickleball, PPA Tour, MLP, APP, Selkirk, JOOLA, Franklin, or paddle shapes with brand logos. Low otherwise.
- **Seasonality:** spring league season, Christmas (the gift buyer), and summer tournaments; search interest fell about 10% in 2025, with "pickleball set" (-25%) and "pickleball lessons" (-15%) down; court construction in the 100 largest cities grew 4% in 2026 versus 13% in 2025 (Axios, T, https://www.axios.com/2026/05/26/pickleball-courts-building-decline; page 403s to curl, snippet only). Participation still grew 22.8% in 2025 (SFIA, P). Treat as mature.
- **AOV:** $30 to $45 single item; $55 to $70 with a mug or hat bundle. Buyers in this income band will pay $32 for a shirt that is specifically about their rating or their court.
- **Verdict: pursue.**

### 2. Backyard chicken keepers

- **Who buys:** "11 million U.S. households own backyard chickens (a 28% increase from 2023)" (APPA 2025 report via Good News for Pets, P fetch of the secondary, https://goodnewsforpets.com/appa-2025-report-152b-industry-shows-continued-growth-cats-gaining-on-dogs-gen-z-stats-more/); L.E.K. puts it at "approximately 17 million U.S. households raise backyard chickens, representing 13% of all pet owners" and reports Amazon seeing about 13% year-over-year growth in backyard-animal categories versus 9% for pet overall (L.E.K., P, https://www.lek.com/insights/pet/beyond-dogs-and-cats-exploring-growth-other-backyard-animals-and-wildlife). Chicken ownership is most popular among millennials (22%) then Gen Z (19%) (APPA 2021-22 via L.E.K., P). Keeper surveys: "most backyard bird-keepers have been found to be highly educated women with household incomes of over $100,000 USD a year" (academic survey summaries, T); UK survey 86.9% women, 60%+ aged 45 to 64 (University of Winchester, T). Interest driven by egg prices and the suburban/rural migration (L.E.K., P; "2 million people relocated to less-densely populated areas" 2020 to 2023).
- **Why they buy merch:** identity ("chicken mama", "queen of the coop"), self-deprecating in-group humour about the hobby taking over ("chicken math", "henopause", "I was crazy before the chickens"), gifting within families who find the hobby funny, and a strong home-goods pull (signs, mugs, egg-basket adjacent decor) because the hobby lives at home.
- **Supply:** Amazon `chicken lady shirt` "over 60,000"; `chicken gift` "over 30,000"; but `backyard chickens shirt` 840 (P). Etsy /market pages exist for `chicken_lady_shirt`, `chicken_mama_t_shirt`, `funny_chicken_shirts`, `crazy_chicken_lady_sign` (S); snippet designs: "Backyard Coop Club Ladies Only Est. 1975", "Welcome to Chicken Math Club", forest-green tee with fluffy chickens and "Chicken Mama" script (S). Amazon first page: "Crazy Chicken Lady Shirt Let's Be Honest I was Crazy Before", "Queen of The Coop", "Chicken Bandana Girl", mostly $12 to $21 (P).
- **Gap:** the saturated part is the "crazy chicken lady" phrase. The under-served part is breed-specific (Silkie, Orpington, Polish, Brahma owners are as breed-proud as dog people), coop-and-flock personalization (flock name, est. year), and home goods: mugs, posters, tea towels, doormats, framed "coop rules". Searches for `backyard chickens` style phrasing return under 1,000 results.
- **IP risk:** none inherent. Avoid Tractor Supply, Purina, Hoover's Hatchery names. Low.
- **Seasonality:** chick season (February to April, when feed stores sell chicks), Mother's Day, Christmas. Egg-price news cycles drive spikes.
- **AOV:** $25 to $35 tees; mugs $18 to $22; two-item home-goods bundles $45 to $55.
- **Verdict: pursue.**

### 3. Linemen and skilled trades

- **Who buys:** Electrical power-line installers and repairers: median wage $95,320 (2025), 127,400 employed (2024), growth much faster than average (BLS Occupational Outlook via snippet, S; bls.gov returns 403 to curl, https://www.bls.gov/ooh/installation-maintenance-and-repair/line-installers-and-repairers.htm). Electricians: median $63,190, 821,000 jobs, 9% growth (BLS via snippet, S, https://www.bls.gov/ooh/construction-and-extraction/electricians.htm). Trade wages "rising 5-7% annually in high-demand trades like linemen, welders, and elevator techs" (recruiter blogs, T). The buyers are two people: the tradesman himself (hoodies, hats, stickers for the hard hat and truck) and the spouse or girlfriend ("Lineman Wife", "Lineman Mom" products are a visible sub-category on Lineman Probs and Etsy).
- **Why they buy merch:** occupational pride as identity, in-group humour ("Support Your Local Pole Dancer" is the dominant joke on Amazon's first page, P), flag and patriotism motifs, storm-work and "trenches" mythology, and hard-hat sticker culture (stickers are a real product line here).
- **Supply:** Amazon `lineman shirt` "over 1,000"; `lineman gift` "over 3,000"; `electrician shirt` "over 2,000"; `welder shirt` "over 2,000" (P). Compare `nurse shirt` "over 20,000" (P). Etsy /market pages exist for `lineman_clothing`, `funny_lineman_shirt`, `blue_collar_lineman_shirts`, `clean_money_lineman` (S), with "Lineman Definition T-Shirt" at $31 and a flag tee at $25.38 list (S). Proof of a brand-shaped buyer: Lineman Probs sells a "LINEMAN MOM" hoodie at $45, a logo tee at $34, and gloves; site copy reads "Tag us on Instagram @linemanissues" (P, https://linemanprobs.com/); the claim of "over 50,000 orders and over 500,000 followers" is from a search snippet (T). Troll Co. describes itself as "Bold Tees, Hoodies & Gear for Blue Collar Workers" with an app (P, https://trollcoclothing.com/).
- **Gap:** under 1,000 Amazon results on a $95K-median occupation. Current designs are one-liner text and clip-art bucket trucks. Nobody on the first page is doing illustrated regional or storm-specific designs (Hurricane season restoration crews, "mutual aid" culture), sub-trades (substation, transmission, tree trimmer, meter tech), apprentice milestone gifts (topping out, journeyman card), or spouse gifting done well.
- **IP risk:** medium. "Dirty Hands Clean Money" is Troll Co's slogan (T); do not use it or anything close. IBEW and local union numbers are trademarks of the IBEW; do not use the IBEW logo or name. Utility company names and logos are off limits. Generic trade names are fine.
- **Seasonality:** Christmas and Father's Day (NRF Father's Day record $27.9 billion in 2026, $226.58 per celebrant, P, https://nrf.com/research-insights/holiday-data-and-trends/fathers-day); storm season (August to October) drives "storm chaser" pride content.
- **AOV:** hoodies $45 to $55 and hats $28 to $32 are the native price points (Lineman Probs sells hoodies at $45, P). Expect $45 to $65 per order.
- **Verdict: pursue.**

### 4. Golfers, sub-segmented

- **Who buys:** 48.1 million Americans age 6+ played golf in 2025; 29.1 million on-course; 8 million female on-course golfers (28% of on-course, highest on record, up 46% since 2019); just under 4 million juniors; 3 million+ on-course beginners every year since 2020; 500 million+ rounds (NGF, P, https://www.ngf.org/the-clubhouse/golf-industry-research/). "The average household income of regular golfers exceeds $100,000. Most golfers come from households earning $75,000 or more, with roughly a quarter reporting household incomes above $300,000" (GolfN, T, https://www.golfn.com/insights/golf-consumer-demographics-spending-data-2026; the $300K quarter is not sourced on that page and should be treated as unverified).
- **Why they buy merch:** humour about being bad at it, league and buddies-trip identity, gifting (golf is the default dad gift), and loud-polo culture (the Amazon first page is all-over-print "funny" polos, P).
- **Supply:** Amazon `golf gift` "over 300,000"; `golf shirt funny` "over 8,000"; `golf mug` "over 2,000"; `golf hoodie funny` "over 1,000" (P). First page for `golf shirt funny` is ZITY, BOJIN and similar moisture-wicking printed polos at $21.84 to $29.99 (P). Etsy /market pages for `funny_golf_shirts`, `dirty_funny_golf_polos`, `funny_ladies_golf_shirts`, `funny_golf_shirts_for_couples` (S): flamingo and margarita all-over polos, "Par then Bar", "Fore O'Clock Somewhere", "Catch Me Riding Birdie", "He's Golfing" golf-wife tees, and crude "long shafts and big balls" lines (S).
- **Gap:** generic golf is gone. What is thin: women golfers as a distinct customer (46% growth, NGF P) with designs that are not pink versions of men's jokes; league-night and buddies-trip personalization (trip name, year, course city without the course's trademark); junior golf parents.
- **IP risk:** high at the edges. Augusta National owns MASTERS, AMEN CORNER, GREEN JACKET and the Pantone 342 jacket green, and "has been very strict about protecting their brand" (Front Office Sports and law-firm posts, T). PGA TOUR, USGA, Ryder Cup, course names and logos are all registered. Stay with the activity.
- **Seasonality:** Father's Day, Masters week (April; do not reference it), Christmas, spring opening. Strong.
- **AOV:** all-over-print polos at $45 to $60 (Printful offers AOP polos) move this niche's AOV above tees. $50 to $75 per order is realistic with a hat.
- **Verdict: test** with AOP polos for a sub-segment; do not launch a "golf store".

### 5. Birders

- **Who buys:** "96 million people (or 3 out of 10 Americans) engaged in birding, making up 37% of the population aged 16 and older"; 91 million backyard, 43 million travelled; "birders spent $107.6 billion on their activities, split between $14 billion spent on trip-related costs ... and $93 billion on equipment like birdhouses, binoculars, cameras, and even land purchases"; average age 49, "equally likely to be male or female", income and education above average (FWS, P, https://www.fws.gov/story/2024-12/birdwatching-america). Broader wildlife watching: 148 million participants, $250.2 billion (FWS press release, P, https://www.fws.gov/press-release/2023-10/americans-spent-394b-hunting-fishing-and-wildlife-associated-activities-22).
- **Why they buy merch:** identity (life list, "bird nerd"), self-aware humour ("Sorry I'm Late I Saw A Bird", "The Birds aren't Going to Watch Themselves", "We Bird At Dawn", all on Amazon's first page, P), species obsession (owls, hummingbirds, corvids, warblers), regional pride (state birds, flyways), and gifting by family who find the hobby endearing.
- **Supply:** Amazon `birding shirt` "over 1,000"; `bird watching shirt` "over 2,000" (P), prices $9.99 to $21.99, text jokes on blank tees. Etsy has /market pages for `birding_t_shirt`, `birdwatching_shirt`, `birding_apparel`, `gift_for_birdwatcher`, `birdwatcher_gifts` (S); snippet designs "Easily Distracted By Birds", "In My Bird Watching Era", "Just a Girl Who Loves Birds", Comfort Colors blanks at $10 to $26 (S).
- **Gap:** the buyer skews 49, educated, with a $93 billion gear budget, and the merch is teenager-grade text jokes. Illustrated species posters, field-guide-style mugs, regional checklists as wall art, and dry humour on premium blanks are thin. Posters and mugs carry higher net margins than tees (35 to 50% and 30 to 45% per Printful's table in `01-income-options.md`).
- **IP risk:** low. Do not use Audubon, Cornell Lab, Merlin, eBird, Sibley or Peterson names or art. Public-domain Audubon plates are usable but everyone uses them; agents should generate original illustration.
- **Seasonality:** spring migration (April to May), Christmas, Mother's Day; the Great Backyard Bird Count (February) and Global Big Day (May) are event hooks (do not use their logos).
- **AOV:** posters $25 to $40, mugs $18 to $22, tees $28 to $32. Bundle a poster and a mug for $50+.
- **Verdict: test.** The weakness is visibility: birders do not wear merch in front of other birders the way pickleball players do. Posters and mugs sidestep that.

### 6. Dog owners, breed-specific

- **Who buys:** 53% of US households (71 million) own a dog; pet industry $158 billion in 2025, projected $165 billion 2026; "22% of pet owners spending less on their pets in 2025" (APPA, P, https://americanpetproducts.org/2026-state-of-the-industry and Pet Age, P, https://www.petage.com/appa-report-pet-industry-consumer-spending/). AKC 2025 ranking: French Bulldog first for the fourth year, then Labrador Retriever, Golden Retriever, German Shepherd, Dachshund entering the top five and pushing Poodle out (AKC, P, https://www.akc.org/expert-advice/dog-breeds/most-popular-dog-breeds-2025/).
- **Why they buy merch:** the dog is the identity; breed owners form tribes (dachshund owners especially); gifting ("dog mom" is a gift category); personalization with the dog's name is the strongest lever (Printful: "Personalized gifts sell" and "buyers form an emotional connection to something made specifically for them", P, https://www.printful.com/blog/print-on-demand-statistics).
- **Supply:** Amazon `dog mom shirt` "over 10,000" and `cat mom shirt` "over 9,000" (fashion dept, P); `dachshund shirt` "over 5,000" (all depts, P). Etsy /market pages for every "dog mom" variant including plus size (S). Amazon first page for dachshund: "Bad Decisions Make Better Stories", "Less Meanies, More Weenies", a hipster dachshund with iced coffee, a Gen Z smoking dachshund (P), so breed humour is already in play.
- **Gap:** only at the breed-plus-angle level (breed plus hobby, breed plus region, breed plus owner age cohort), and in personalization. "Dog mom" itself is closed.
- **IP risk:** "Dog breed names are considered facts and are descriptive, making them not subject to trademark protection" (legal Q&A summaries, T). Avoid AKC, Westminster, brand names (Purina, Chewy, BarkBox).
- **Seasonality:** Christmas, Mother's Day, National Dog Day (August 26), gotcha-day personalization year-round.
- **AOV:** sweatshirts $40 to $48 (Etsy snippets show dog-mom sweatshirts at $21.49 sale, S, which is the price floor to avoid); personalized items command $35+.
- **Verdict: test** with three or four breeds; measure which breed converts before adding more.

### 7. Lake and pontoon boat owners

- **Who buys:** 12 million registered boats; $56.7 billion annual sales; "61% of boat owners have an annual household income of $75,000 or less"; 95% of boats under 26 feet (NMMA, P, https://www.nmma.org/advocacy/economic-impact/recreational-boating). New powerboat sales down 8 to 10% in 2025 (NMMA via snippet, S). So this is a large, middle-income group whose spend goes to the boat.
- **Why they buy merch:** place identity (the lake), family-trip identity (matching crew shirts), "boat dad / lake chauffeur" humour, personalization with the lake or boat name.
- **Supply:** Amazon `lake life shirt` "over 2,000"; `boat shirt funny` "over 4,000" (fashion); `pontoon shirt` 985 (P). Etsy /market pages `lake_life_apparel`, `personalized_lake_life_shirt`, `custom_lake_life_tee`, `lake_lover_gifts` (S) with "Lake Chauffeur", "Boat Dad", "Wake Surf Dad", custom lake-name sweatshirts in cursive, custom lake-map apparel up to $40.99 (S).
- **Gap:** pontoon-specific humour (under 1,000 results), named-lake personalization for lakes outside the famous few (Lake George and the Adirondacks are already covered on Etsy, S), and Montana and Pacific Northwest lakes specifically, where Chris has local knowledge from NSL and Glacier Shrink Wrap clients.
- **IP risk:** low. Avoid boat brand names (Bennington, MasterCraft, Sea-Doo) and Coast Guard imagery.
- **Seasonality:** sharp. May to August, plus Father's Day. Dead in winter.
- **AOV:** family crew orders (4 to 6 shirts) push AOV to $100+. Personalization is the whole play.
- **Verdict: test** as a summer collection, personalized by lake.

### 8. Fly fishing and trout anglers

- **Who buys:** 57 million Americans fished in 2025 (18%), first year-over-year decrease since 2021 with a record 19 million lapsed; fly fishing 7.9 million, "nearly 2 million more fly anglers vs. a decade ago", outings up from 10 to 11 a year; 31% of angler households earned $100K+ (ASA/RBFF 2026 Special Report press release, P, https://asafishing.org/press-release/2026-special-report-on-fishing/, and the report PDF, P). Fly anglers specifically: 48% over $75K household income in the 2024 report (T via snippet).
- **Why they buy merch:** craft identity (fly fishing is a self-image), species art (trout, steelhead), river and region pride, and dry humour. The dominant brands (Simms, Orvis, Patagonia, Fishpond) sell identity apparel at $35 to $60.
- **Supply:** Amazon `fly fishing shirt` "over 2,000", but the first page is entirely UPF performance fishing shirts from 33,000ft, Palmyth, BASSDASH and Columbia at $24 to $60 (P), with no graphic tees on it. `bass fishing shirt` "over 2,000" (P). Etsy /market pages `fly_fishing_t_shirts`, `trout_fishing_shirt`, `funny_fly_fishing_t_shirt`, `fly_fishing_sweatshirt` (S) with vintage lure graphics, abstract boho trout, "Born To Fly", $8.99 to $32 (S).
- **Gap:** illustrated species and river art on premium blanks and posters; regional (Montana rivers: Flathead, Blackfoot, Madison, Gallatin, Missouri) with no brand trademarks. Amazon's first page has zero graphic tees, which means the graphic-tee demand is going to Etsy and to the big brands.
- **IP risk:** medium. Do not use Simms, Orvis, Patagonia's trout logo, Yeti, or Trout Unlimited. River names are free; a state's tourism logo is not.
- **Seasonality:** March to October; Christmas; Father's Day.
- **AOV:** $30 to $40 tees, posters $30 to $45. Buyers here pay $45 for a hoodie from a brand they trust.
- **Verdict: test**, with a Montana and Northern Rockies angle Chris can speak to from the ground.

### 9. Horse girls and horse owners

- **Who buys:** 2023 equine industry value added $177 billion (up from $122 billion in 2017), 6.6 million horses (down from 7.2 million), 2.2 million jobs, "62% of horse owners own or lease property"; recreation sector $36.7 billion (AHC, P, https://horsecouncil.org/economic-impact-study/ and https://horsecouncil.org/project/results-from-the-2023-national-equine-economic-impact-study-released/). Owner income distribution ("46 percent ... $25,000 to $75,000; 9 percent earn $150,000 or more") appeared in a snippet attributed to AHC but could not be tied to the 2023 study and may be from the 2005 study (S, unverified). US equestrian apparel market estimated at $1.9 billion 2025 (market-research vendor, T, low confidence).
- **Why they buy merch:** the horse is the identity, often from age 8; "horse girl" is now a self-applied, meme-aware label ("In My Horse Girl Era", S); parents and grandparents are the gift buyers; show and barn culture makes merch visible.
- **Supply:** Amazon `horse girl shirt` "over 5,000"; `horse gift` "over 50,000" (P). Etsy /market pages `horsegirl_shirt`, `equestrian_inspired_clothing`, `horse_riding_shirt_girls`, `womens_horse_shirt` (S) with boho horse-head florals, Comfort Colors, personalized birthday shirts (S).
- **Gap:** adult amateur riders (the money) are poorly served; everything is aimed at girls. Discipline-specific (barrel racing, dressage, hunter/jumper, trail) and breed-specific (Quarter Horse, Arabian, Thoroughbred OTTB) humour is thin. But the money per household goes to the horse first.
- **IP risk:** low to medium. AQHA, USEF, breed registries and Western brands (Ariat, Wrangler) are registered; "Yellowstone" is a trademark.
- **Seasonality:** show season (spring to fall), Christmas.
- **AOV:** $28 to $45. Verdict: **test small**, adult-rider angle only.

### 10. Bourbon dads

- **Who buys:** male, 30 to 60, the Father's Day and Christmas gift target; "Millennials and Generation Z consumers now represent over 54% of bourbon purchasers" (market-research vendors, T, low confidence); secondary-market action "in the $50 to $150 range" with Buffalo Trace products near half of flipped bottles (InsideHook/Spirits Business, T).
- **Why they buy merch:** connoisseur identity, bar and home-bar decor, gifting.
- **Supply:** Amazon `bourbon shirt` "over 1,000"; `bourbon gift` "over 10,000" (P). First page: "Bourbon Periodic Table of Elements", "Bourbon Makes It Better" (Grunt Style), "Things I Do in My Spare Time Drink Bourbon" at $15 to $33 (P). Etsy /market pages `bourbon_dad_shirt`, `i_drink_bourbon_and_know_things_shirt`, `bourbon_sayings_tee` (S): "Life Happens, Bourbon Helps", "Call Me Old Fashioned", "I'll Be In The Backyard" with a glass and cigar (S).
- **Gap:** modest; decor (posters, bar signs as framed prints) over apparel.
- **IP risk:** high for brands: Buffalo Trace, Pappy Van Winkle, Blanton's, Maker's Mark trade dress (the wax), Weller are all registered and enforced. Alcohol humour itself is allowed by Printful and Printify (neither policy mentions alcohol, P), but **Meta and Google restrict alcohol-adjacent ad targeting**, which cuts off the paid-ads path if Chris ever funds it (T, not verified this session; see section 5).
- **Seasonality:** Father's Day and Christmas only. Verdict: **test small**, posters and mugs, no brand names.

### Avoid list, with the reason

- **Nurses:** Amazon `nurse shirt` "over 20,000" (P); Printful itself says "Specific roles create stronger products than generic 'nurse life' designs" (P, https://www.printful.com/blog/print-on-demand-niches); Kittl calls generic "Nurse" shirts "Saturated" (P, https://www.kittl.com/blogs/print-on-demand-niches-pod/). Big audience, but the agents would be the 20,001st entrant.
- **Teachers:** "over 50,000" (P), and the buyer has the least disposable income of any group here.
- **Grandma / grandpa:** "over 50,000" each (P). Keep as a gift-overlay (a "Pickleball Grandma" or "Chicken Grandma" SKU inside another niche). The spend is real: nine in ten grandparents spend on grandchildren, $2,654 a year on average, $172 billion in direct financial support (AARP, P, https://www.aarp.org/caregiving/financial-legal/grandparents-report-2026/), and they are the buyer rather than the wearer.
- **RV and camping:** "over 60,000" (P). 8.1 million RV households (RVIA, T) are real, and the supply is already there.
- **Homestead-generic:** "over 20,000" (P). Chickens is the specific, open sub-niche.
- **Western / cowboycore:** Boot Barn revenue $2.25 billion with 500+ stores, Western boot sales up 7% Jan to Aug 2025 while fashion boots fell 5% (Marketplace and WWD, P and T). Real brands and licensed TV properties own the aesthetic; a POD store is the knock-off here.
- **Gym / powerlifting / CrossFit:** Gymshark-level competition; "Never use 'CrossFit' in titles or designs" (POD-tool blogs, T) and Kittl: "Trying to rank for a generic 'Fitness Shirt' puts you in direct competition with massive brands like Nike and Gymshark" (P).
- **Hunting-generic:** 14.4 million hunters, $45.2 billion, $1,896 per hunter per year (FWS, P and T), 90% male, 97% white, peak age 55 to 64 (FWS addendum, T). Supply is moderate (`deer hunting shirt` "over 3,000", `duck hunting shirt` "over 2,000", P), but Mossy Oak and Realtree camo patterns are registered trade dress, and the niche's humour drifts into content Printful's guidelines flag (glorified violence, weapons). Workable only as a sub-line of fly fishing (lodge and outfitter aesthetic).
- **Any licensed fandom, team or brand:** Shopify removes on a trademark notice, "repeat offenders can lose the store entirely, and Shopify's policy extends termination to other stores run by the same operator" (T). Printify: "We prohibit any use of our Service that infringes the IP rights of others, including by producing or selling infringing or counterfeit goods" (P, https://printify.com/intellectual-property-policy/). This also rules out "bootleg" style designs, which a POD-playbook blog reports as the second-largest style on Etsy by volume ("bootleg at 84,119" listings, T, https://theprintondemandplaybook.com/blog/the-ultimate-guide-to-2026-etsy-design-print-on-demand-design-trends; the page fetched but the figures are only in the snippet).

---

## 2. Customer profiles and purchase journeys (top four)

Each step names what the agents produce. The store is one Shopify store with a collection per niche; profiles share the same Klaviyo account with a niche tag.

### 2.1 The pickleball regular

**Demographics.** 45 to 70 (the money) and 25 to 44 (the volume); household income $100K+ for half of players (T); suburban and Sun Belt; plays 2 to 4 times a week at a club, YMCA, HOA court or dedicated facility (16,210 US places to play at the start of 2025, Pickleheads, P). The gift buyer is a spouse or adult child.

**Psychographics.** Evangelist for the sport; competitive about a rating (3.0 to 4.5) and about which court group they belong to; enjoys being teased for the obsession; retired or flexible-hours; buys gear upgrades without guilt (paddle revenue outgrew units on Amazon in 2025, P). Treats the Tuesday round-robin as a social calendar.

**Where they are online.** Facebook groups per court complex and per city; Pickleheads and club apps; YouTube instruction channels; The Dink newsletter; Instagram reels of rallies. Reddit r/Pickleball exists (lead only, not used as voice).

**What they already buy.** Paddles ($100 to $250), court shoes, visors, sweat-wicking tees, lead tape, paddle covers, portable nets, club dues, tournament entries, lessons.

**Trigger moments.** First rating bump; joining a league; club tournament; a friend's birthday; Christmas list ("I don't know what to get Dad, he only talks about pickleball"); summer travel to play in another state.

**Price tolerance.** $30 to $40 for a shirt that is specifically right; $50 to $60 for a hoodie; will not pay $30 for a shirt that says only "Pickleball".

**Objections.** "Is it moisture-wicking?" (offer at least one performance blank); "Will it be cringe at the club?" (the humour has to come from inside the sport); sizing on Comfort Colors oversized fits.

**What they find cringe.** Jokes that explain the sport ("it's like tennis but smaller"), pickle puns with cartoon pickles, "Dink Responsibly" (done to death), anything that looks like a tourist shirt.

**Journey.**
1. *Discovery:* Pinterest and Instagram reels (organic), club Facebook groups (members share funny shirts), Google "pickleball gifts for her/him" in Q4. **Agent output:** weekly short-form posts pairing a design with a one-line in-joke; a Pinterest board per sub-theme (rating humour, kitchen jokes, court-group shirts); an SEO landing page per gift intent ("gifts for pickleball players who have everything").
2. *First touch:* product page. **Agent output:** listing copy that leads with the joke, then the blank (Comfort Colors 1717 or Bella+Canvas 3001), then sizing; mockup on a 50+ model and a 30s model; a "which rating are you" size chart gag in the gallery.
3. *Consideration:* compares to Amazon $18 tees and Etsy $25 tees. **Agent output:** a bundle (shirt + mug) at $52; a free "court etiquette" printable PDF as the email-capture lead magnet; reviews requested by Klaviyo flow 10 days after delivery.
4. *Purchase:* Shopify checkout. **Agent output:** cross-sell block "for your doubles partner" with a matching design.
5. *Post-purchase:* Klaviyo flow: shipping, "tag us at the courts" ask, review request, 30-day "new drops" email. **Agent output:** flow copy per niche; a monthly "new rating-humour drop" campaign.
6. *Repeat and gift occasions:* Christmas, birthday, Father's and Mother's Day, league start (March and September). **Agent output:** a seasonal calendar with send dates; gift-guide blog post refreshed each October.

### 2.2 The backyard flock keeper

**Demographics.** Women 35 to 64 (UK survey: 86.9% women, most 45 to 64, T; US surveys: educated women, household income over $100K, T); suburban-exurban homeowners with a yard; millennial and Gen Z households are the fastest-growing owners (APPA via L.E.K., P). Often also gardens, cans, bakes.

**Psychographics.** The flock is pets with names and a drama; collects breeds the way others collect sneakers; proud of "chicken math" (always more chickens than planned); self-mocking; strongly community-oriented (local poultry swaps, Facebook breed groups, coop tours); values homemade, local, "farm" aesthetics; suspicious of slick marketing.

**Where they are online.** Facebook groups (Backyard Chickens, breed-specific groups, regional swap groups); BackyardChickens.com forum; Instagram and TikTok coop content; Pinterest for coop design; YouTube homestead channels.

**What they already buy.** Chicks ($3 to $8 each, in spring), feed ($20 to $40 a bag, monthly), coops ($300 to $3,000), run netting, nest boxes, heated waterers, treats, egg cartons and stamps, coop signs, boots, garden gear.

**Trigger moments.** Chick season (February to April); first egg; a new breed; a predator loss (a surprisingly strong driver of "coop security" humour); Mother's Day (family buys for "the chicken lady"); Christmas.

**Price tolerance.** $25 to $35 for a tee or a mug set; $40+ for a sweatshirt; $30 to $45 for a framed coop print; does not mind spending on the coop's "decor".

**Objections.** "Is it cotton, I'll be wearing it in the yard?"; "I already have a chicken shirt" (hence breed and flock-name personalization); dislikes anything that reads as mocking the hobby from outside.

**What they find cringe.** "Crazy chicken lady" has become the generic (60,000 Amazon results, P), so it reads as cheap; cartoon chickens from stock libraries; "farm fresh eggs" signs with no specificity.

**Journey.**
1. *Discovery:* Pinterest (coop decor), Facebook group shares, Google "gifts for chicken lovers". **Agent output:** Pinterest-first content: coop sign and mug designs pinned to decor boards; a blog with legitimately useful content (breed guides, coop checklist, "chicken math calculator") that carries the shop; SEO pages per breed ("Silkie owner gifts").
2. *First touch:* a breed-specific or flock-name product. **Agent output:** breed illustration sets (one style, 12 breeds) applied across mug, tee, poster, tea towel; personalization field for flock name and est. year.
3. *Consideration:* compares to Etsy handmade signs. **Agent output:** copy that leans on the illustration being original and the blank being garment-dyed; bundles (mug + print) at $45.
4. *Purchase.* **Agent output:** "add the matching coop sign" cross-sell.
5. *Post-purchase:* Klaviyo: shipping, "show us your flock" UGC ask, review, "chick season is coming" February campaign.
6. *Repeat:* chick season, first-egg milestones, Mother's Day, Christmas; new breed drops quarterly.

### 2.3 The lineman and the person who buys for him

**Demographics.** Lineman: male, 22 to 50, median wage $95,320 (S), often rural or small-city, union or contractor, travels for storm work. Buyer two: spouse or girlfriend, 22 to 45, who manages gifts and buys "Lineman Wife" products for herself. Electricians, welders and other trades share the pattern at lower wages.

**Psychographics.** Pride in danger and skill; dark humour; patriotism; brand loyalty to tools (Klein, Buckingham) and to a handful of trade apparel brands; distrust of anything that looks corporate or "safety department"; hard-hat stickers and truck decals as identity. The spouse side: pride, worry during storms, a community of "line wives".

**Where they are online.** Instagram (@linemanissues-style meme accounts), Facebook lineman groups and storm-work groups, TikTok jobsite content, YouTube climbing and rescue videos.

**What they already buy.** Boots ($250+), gloves, hooks and climbers, Carhartt and Ariat work clothes ($70 to $150 per piece, T), trade-brand hoodies ($45, Lineman Probs, P), hats, stickers, coolers.

**Trigger moments.** Finishing apprenticeship (journeyman); topping out on a big job; storm deployment and return; Father's Day; Christmas; a new truck.

**Price tolerance.** $45 to $55 hoodies and $28 to $32 hats are normal (P). Tees $28 to $34. Sticker packs $8 to $12 sell as add-ons.

**Objections.** "Is it heavyweight?" (specify a heavyweight hoodie blank); "Does it look like a safety-meeting shirt?"; brand-slogan copying (they know Troll Co and will call out a rip-off).

**What they find cringe.** "Support Your Local Pole Dancer" is the Amazon first page (P), so it reads as cheap; stock bucket-truck clip art; wording written by someone who has never been on a crew.

**Journey.**
1. *Discovery:* Instagram meme accounts and Facebook groups, plus Google "lineman gifts" by the spouse in November. **Agent output:** meme-format posts that show the design in a jobsite context; a "gifts for a lineman" SEO page and a "lineman wife" page; sticker giveaways for UGC.
2. *First touch:* hoodie or hat. **Agent output:** illustrated designs (transmission towers, storm skies, regional grid maps, sub-trade icons) with short, specific wording; heavyweight blank specified in copy.
3. *Consideration:* compares to Lineman Probs and Troll Co. **Agent output:** do not compete on slogan; compete on illustration, region and sub-trade specificity; hoodie + sticker pack bundle at $58.
4. *Purchase.* **Agent output:** "for the one at home" cross-sell to the spouse line.
5. *Post-purchase:* Klaviyo: shipping, "tag us from the bucket" UGC, review; storm-season September campaign.
6. *Repeat:* Christmas, Father's Day, storm returns, apprentice milestones (a "journeyman" SKU with year personalization).

### 2.4 The birder

**Demographics.** Average age 49, equally male and female, income and education above average, 75% white, Asian Americans the highest participation rate at 47% (FWS, P); 91 million watch from home, 43 million travel for it (FWS, P).

**Psychographics.** Quietly obsessive (life list, yard list, patch birding); values accuracy (a wrong bird on a shirt is disqualifying); dry humour; environmentally minded; buys quality once (binoculars $300 to $3,000); gifts for each other within birding couples and clubs.

**Where they are online.** eBird and Merlin (Cornell, do not reference by name in designs); Facebook birding groups by state and county; regional Audubon chapters; Instagram bird photography; YouTube.

**What they already buy.** Binoculars, scopes, cameras and lenses, feeders and seed (monthly), field guides, bird-friendly coffee, trips and festivals, club memberships ($93 billion in equipment, P).

**Trigger moments.** Spring migration (April to May), a lifer, a festival, Christmas, Mother's Day, retirement (birding is a common retirement identity).

**Price tolerance.** $25 to $40 for a poster, $18 to $22 mugs, $28 to $34 tees. Will pay more for accurate, original illustration.

**Objections.** Accuracy ("that is not a Cooper's Hawk"); dislike of "cute" cartoon birds; prefers natural colour palettes; wants to know the art is original and not an AI mash-up with wrong wing feathers.

**What they find cringe.** "Bird nerd" and "easily distracted by birds" at this point (both on Amazon's first page, P); stock photos; anything that looks like it came from a gift shop at an airport.

**Journey.**
1. *Discovery:* Pinterest and Instagram for illustrated posters; Google "gifts for birders" and species-name queries ("barred owl art print"). **Agent output:** species illustration series (one consistent style, 24 common North American species, then regional sets); SEO page per species and per region; a monthly "migration calendar" content piece.
2. *First touch:* a poster or mug of their bird. **Agent output:** listing copy that names the species correctly, with a line of natural history; paper and print spec stated.
3. *Consideration:* compares to artist prints on Etsy. **Agent output:** original-illustration positioning, bundle (print + mug) at $50, and an email-capture lead magnet (printable yard-list checklist).
4. *Purchase.* **Agent output:** cross-sell the regional set.
5. *Post-purchase:* Klaviyo: shipping, review, spring migration campaign, Christmas gift guide.
6. *Repeat:* new species drops; the life-list framing makes collecting natural.

---

## 3. Unserved or poorly served: where the money is and the merch is not

Ordered by how much money sits behind the gap, with an honest note on whether the gap is real or just unprofitable.

1. **Linemen and sub-trades.** $95K median wage, 127,400 workers, under 1,000 Amazon `lineman shirt` results (S, P). Real gap. The incumbent brands (Lineman Probs, Troll Co) prove the buyer; the gap is illustration quality, sub-trade and region specificity, and spouse gifting. Why nobody fills it: the audience is small per sub-trade and most POD sellers chase search volume rather than wage. That is the point: a store that does not depend on marketplace search can serve a 127,000-person group with $45 hoodies.
2. **Birders, 49 years old, $93 billion on gear, text-joke tees.** Real gap on product type (posters, mugs, home goods) and on illustration standard. Why nobody fills it: birders are hard to reach with paid social and do not wear the merch in public, so the funnel has to be search and Pinterest, which takes months. This is a gap that is only profitable with patience and organic content, which an agent loop can supply cheaply.
3. **Pickleball beyond the t-shirt.** 414 hoodies and 658 mugs on Amazon against 24.3 million players (P). Real gap on product type and on sub-group humour (rating, court-group, doubles partner). Caveat: search interest is cooling (T), and the tee layer is saturated. Enter with hoodies, mugs, hats and club-group bundles.
4. **Backyard chickens, breed-specific and personalized.** 11 to 17 million households (T), 840 Amazon results for `backyard chickens shirt` against 60,000 for `chicken lady shirt` (P). Real gap in the specific; the generic is closed.
5. **Women golfers.** 8 million on-course, up 46% since 2019, 35% of beginners (NGF, P). Current supply is pink versions of men's jokes and golf-wife tees ("He's Golfing", S). Real gap, but it sits inside the most saturated gift category on Amazon (300,000 results, P), so it only works as an owned-store collection with its own content.
6. **Adult amateur horse riders.** Everything is for girls (Amazon and Etsy first pages, P and S). The money per household goes to the horse, and the AHC income distribution (if the 46% at $25K to $75K figure holds, S) says these owners are not rich. This looks like a gap mostly because the buyer is already spending on hay. Test small or skip.
7. **Lake-name personalization for non-famous lakes.** Real but seasonal and operationally heavier (personalization fields, more support). Worth a summer test using Flathead, Whitefish and Coeur d'Alene as the first set because Chris has local credibility and NSL/Glacier Shrink Wrap audiences nearby.
8. **Fly fishing graphic tees and posters.** Amazon's first page is all performance shirts (P); the graphic demand goes to Etsy and to Simms/Orvis/Patagonia. The gap is real but defended by brands with real loyalty; a POD store wins only on regional river art and humour the big brands will not do.
9. **Gaps that are not gaps.** Nurses, teachers, grandma, RV, homestead, western: the Amazon counts show supply has already found the demand. "Bootleg" style designs (84,119 Etsy listings, T) are a large "gap" that only exists because it is infringement; excluded. Bourbon brand-specific humour (Blanton's, Pappy) is a demand pocket that only works by using registered marks; excluded. Hunting humour that leans on weapons imagery and "shoot first" jokes is a demand pocket that risks Printful's "glorify violent acts" clause and Meta's ad rules; excluded as a primary.

---

## 4. Design and product directives for the agents

### 4.1 What the evidence says top sellers look like

- **Amazon first pages (P, fetched 2026-10-05)** across ten niches: one-line text jokes, often in a heavy sans or distressed display font, on black, navy or heather blanks, $12.99 to $21.99; a few "retro" badge layouts (sunset silhouette, "Power to The Line" badge for linemen); AOP polos in golf; UPF performance shirts in fishing; personalized sweatshirts with names in dog and lake niches at $27 to $36. The floor is cheap text. The differentiators that command $25 to $36 on those same pages are personalization and illustration.
- **Etsy indexed pages (S)** show the premium layer: Comfort Colors garment-dyed tees and sweatshirts (named in birding, chicken, horse snippets); "In My ___ Era" and "Easily Distracted By ___" templates; boho floral and single-line illustration; rhinestone and embroidered looks (pickleball); cursive lake and flock names; "Est. 19XX" club badges ("Backyard Coop Club Ladies Only Est. 1975"); cartoon-animal-doing-the-hobby (geese playing pickleball, hipster dachshund with iced coffee).
- **Etsy listing volumes by style** reported by a POD-playbook blog (T): "dopamine decor" 103,448 listings, "bootleg" 84,119, "animal memes" 81,658, "minimalist line art" 60,194 (line art "sells primarily on wall art and posters, then totes"). Bootleg is excluded on IP grounds; the other three map directly onto chickens (animal memes), birders (line art on posters), and pickleball (dopamine colour).
- **Printful's own guidance (P):** "Specific roles create stronger products than generic 'nurse life' designs"; "Personalization adds value through names, roles, dates, inside jokes, and pet names"; "Family sets support bundles"; "Overusing AI art without cleanup: wonky hands, distorted pets, and messy text hurt your reputation"; "Use Google Trends, Etsy autocomplete, Reddit, TikTok comments, and social media groups to compare demand and competition" (https://www.printful.com/blog/print-on-demand-niches). On AI designs, Printful's copyright post (from `01-income-options.md`, P): avoid "copyrighted characters, brand logos, or the recognizable style of living artists" and reverse-image-search finals.

### 4.2 Product mix per niche

| Niche | Lead products | Secondary | Skip |
|---|---|---|---|
| Pickleball | Comfort Colors tee, heavyweight hoodie, 15 oz mug | Dad hat, sticker sheet, poster (court-rules gag) | Performance polos (brands own it), phone cases |
| Chickens | 15 oz mug, poster/framed print, Comfort Colors tee | Tea towel, doormat (if Printful carries it), sweatshirt, sticker sheet | Phone cases, hoodies (yard wear is tees and sweatshirts) |
| Linemen/trades | Heavyweight hoodie, dad hat, sticker pack (hard-hat size) | Tee, long-sleeve, tumbler | Posters, mugs (low fit) |
| Golf (sub-segment) | AOP polo, hat | Towel if available, tee | Mugs, posters |
| Birders | Poster (matte, 12x16 and 18x24), mug | Tee, tote, sticker sheet | Hoodies, phone cases |
| Dog breed | Sweatshirt (personalized name), mug | Tee, tote, pet bandana (family set) | Posters |
| Lake/pontoon | Family crew tee sets (personalized lake), sweatshirt | Hat, tumbler | Posters |
| Fly fishing | Tee, poster, hat | Hoodie, sticker | Mugs |

Phone cases appear nowhere above: nothing in the fetched data showed phone cases ranking in any of these niches, and the buyer ages (45+) skew away from case-swapping.

### 4.3 Design styles that sell, per niche

- **Pickleball:** bright, high-saturation "dopamine" colour on garment-dyed blanks; chunky retro sports type; rating-number badges ("Certified 3.5, Plays Like a 2.5"); animal-doing-the-sport illustrations; doubles-partner pairs. Avoid: pickle characters, "Dink Responsibly", anything explaining the sport.
- **Chickens:** hand-drawn breed illustration in a consistent naturalist-meets-folk style; sage, cream, rust, forest palettes; serif and script type; "Coop Club Est." badges; chicken-math and henopause humour. Avoid: "crazy chicken lady", stock cartoon hens, neon.
- **Linemen/trades:** heavy black, charcoal, olive and safety-orange accents; distressed badge and shield layouts; illustrated transmission towers, storm skies, bucket trucks drawn by hand; sub-trade icons; flag done with restraint. Avoid: Troll Co's slogan, IBEW marks, utility logos, cartoon "pole dancer" jokes.
- **Golf sub-segment:** all-over patterns for polos (women-golf motifs that are not pink flamingos), league-night badges with city and year, dry self-deprecation. Avoid: Masters green, jacket references, tour logos, crude "balls" jokes if the target is women.
- **Birders:** accurate species illustration (verify field marks before publishing; one wrong wing bar kills credibility), muted natural palettes, field-guide typographic layout, regional checklists as posters. Avoid: "bird nerd", cute cartoons, Audubon's name.
- **Dog breed:** breed silhouette and expressive illustration; personalization with dog name; breed-trait humour (dachshund stubbornness, golden retriever energy). Avoid: "dog mom" alone, AKC marks.
- **Lake/pontoon:** cursive lake name over a simple lake-outline map; distressed summer-camp type; "Lake Chauffeur" register. Avoid: boat brand names, Coast Guard.
- **Fly fishing:** trout and river illustration, vintage-fly-tying-catalogue type, river names. Avoid: brand trout logos, Montana tourism marks.

### 4.4 Rules that apply to every design (policy, P)

- Printful Acceptable Content Guidelines: "You need to either own the content you submit to Printful, or have the rights to use, display, and resell it. Content must comply with right of publicity, trademark, and copyright laws." Hateful content "that expresses hatred towards or attacks on any person, group and/or their protected characteristics" is removed; violent events may not be used "to promote, glorify, or trivialize violent acts." (https://www.printful.com/policies/download/content-guidelines)
- Printify Terms: "Hateful Content: You may not post or upload Content that condones or promotes violence against people based on race, ethnicity, color, national origin, religion, age, gender, sexual orientation, disability, medical condition or veteran status"; "Printify at its discretion and at any time may also remove any Content from our Service that we deem obscene, offensive or otherwise inappropriate." (https://printify.com/terms-of-service/) Printify IP Policy: "We prohibit any use of our Service that infringes the IP rights of others, including by producing or selling infringing or counterfeit goods", extended explicitly to "AI-Generated Content" and "prompt inputs". (https://printify.com/intellectual-property-policy/)
- Shopify AUP: "you can't call for, or threaten, violence against specific people or groups"; "most product eligibility or takedown disputes that entrepreneurs may encounter originate from outside Shopify, including from regulators and third-party IP rights holders." (https://www.shopify.com/legal/aup) Shopify Help: "Posting content that constitutes an infringement of others' legal rights violates Shopify's Acceptable Use Policy and the content can be removed at Shopify's discretion." (https://help.shopify.com/en/manual/compliance/intellectual-property)
- Neither Printful's nor Printify's policy mentions alcohol or firearms imagery (P); the limits there come from ad platforms (T) and Chris's own judgement.
- Agent pre-publish checklist: (1) no registered marks, team names, course names, brand slogans or character likenesses; (2) USPTO TESS search on any phrase used as a headline; (3) reverse-image search on the final art (Printful's own advice); (4) species, breed and trade terminology checked against a reference before copy is written; (5) disclose AI assistance in the product description if Printful's guidance is followed; (6) nothing that mocks a protected class, including "jokes" about age or gender aimed at the in-group's spouses.

---

## 5. What could not be verified, and pages that need a manual browser read

**Could not verify this session (treat as unconfirmed):**
1. Pickleball median household income of $112K and the income-bracket split (brandedpickleball.com, T). The underlying SFIA/Pickleheads "State of Pickleball" report is paywalled.
2. The "roughly a quarter of golfers report household incomes above $300,000" line on GolfN (T). NGF's participation page (P) carries no income figures; NGF income data is member-only.
3. The AHC owner-income distribution ("46 percent ... $25,000 to $75,000") appeared in a snippet attributed to AHC but may be from the 2005 study, as the dvm360 article with the $204/$260/$547 per-horse vet figures is dated 2005 (P). Needs the 2023 AHC study PDF ($ purchase).
4. Lineman Probs "over 50,000 orders and over 500,000 followers" (snippet only; the site itself shows products and an Instagram handle, P).
5. Pickleball search interest down about 10% in 2025 and court growth of 4% (Axios, 403 to curl; snippet only).
6. The Etsy style listing counts (dopamine decor 103,448 etc.) on theprintondemandplaybook.com (page fetched, numbers only in the search snippet; may be in an image).
7. Etsy per-query listing counts. Every etsy.com fetch returned 403. Etsy /market page existence is the proxy used.
8. Redbubble, TeePublic, Zazzle and Spreadshirt counts (all 403).
9. Any Semrush keyword volumes (no API units) and any Google Trends curve (429).
10. Meta and Google alcohol-advertising restrictions affecting bourbon merch (not searched before the budget ran out; well known but unverified here).
11. BLS wage figures for linemen and electricians (bls.gov 403s to curl; figures are from the search snippet of the BLS page, S).
12. Backyard chicken keeper income figures ("highly educated women with household incomes of over $100,000") come from snippet summaries of academic surveys (T); the ScienceDirect and PMC papers were not fetched.
13. Market-research vendor figures (pickleball apparel $187M US, equestrian apparel $1.9B US, bourbon buyer demographics) are low confidence by nature.
14. Amazon counts: "over N" buckets, and the second batch used `&i=fashion` (pickleball shirt, pickleball t-shirt funny, dog mom shirt, grandpa shirt, cat mom shirt, boat shirt funny, pickleball gift) while the first used no department filter. Comparable within a batch, roughly comparable across.

**Pages for a manual browser read:**
- https://www.etsy.com/search?q=pickleball%20shirt and the /market pages listed above (for exact "N results")
- https://www.redbubble.com/shop/?query=pickleball (and chicken, lineman, birding)
- https://trends.google.com/trends/explore?q=pickleball%20shirt,chicken%20shirt,lineman%20shirt,birding%20shirt&geo=US (12-month and 5-year)
- https://www.bls.gov/ooh/installation-maintenance-and-repair/line-installers-and-repairers.htm
- https://www.axios.com/2026/05/26/pickleball-courts-building-decline
- https://help.printify.com/hc/en-us/articles/4483625985553-Can-any-image-be-printed (403)
- https://help.printful.com/hc/en-us/articles/360014009020-What-is-Printful-s-print-file-content-policy (403)
- https://horsecouncil.org/economic-impact-study/ (purchase the 2023 study for owner income and per-horse spend)
- https://www.sec.gov/Archives/edgar/data/1370637/000137063726000019/etsy-20251231.htm (fetched, P; worth a read of the category section for GMS shares, which the 10-K lists by name only: "home and living, jewelry and personal accessories, apparel, craft supplies, paper and party supplies, and toys and games")
- Meta Advertising Standards on alcohol, and Google Ads alcohol policy, before any bourbon SKU is funded with ads

---

## Sources (grade, date 2026-10-05)

Primary fetched (P): sfia.org pickleball page; theapp.global participation release; pickleheads.com statistics guide; thedinkpickleball.com Amazon paddle sales and participation posts; fws.gov 2022 survey press release and "Birdwatching in America"; fws.gov hunting expenditure addendum PDF; asafishing.org 2026 Special Report press release and PDF; ngf.org golf industry research; nmma.org recreational boating economic impact; horsecouncil.org 2023 study pages; americanpetproducts.org 2026 state of the industry; petage.com APPA reports; goodnewsforpets.com APPA 2025 summary; lek.com backyard animals insight; akc.org most popular breeds 2025; aarp.org grandparents report 2026; healthandfitness.org 81 million members release; nrf.com Mother's Day and Father's Day pages; marketplace.org Western boot story; linemanprobs.com; trollcoclothing.com; printful.com niches and statistics posts, Acceptable Content Guidelines PDF; printify.com terms of service, intellectual property policy, niches post; shopify.com AUP, Terms, POD niches post; help.shopify.com IP page; kittl.com niches post; merchtitans.com nurse post; golfn.com demographics post; amazon.com search result pages for 50 queries (counts and first-page titles/prices).

Search-snippet (S): BLS Occupational Outlook pages for linemen and electricians; Etsy /market pages for every niche named; AHC owner-income line; Axios pickleball piece; Lineman Probs order count.

Secondary (T): brandedpickleball.com; pickleballunion.com; market-research vendor pages (Technavio, GM Insights, Coherent, Dataintelo); InsideHook and The Spirits Business on bourbon; Front Office Sports and law-firm posts on Augusta National; Avvo and ColoradoBiz on breed-name trademarks; university and journal survey summaries on chicken keepers; POD-tool blogs (Printify knowledge hub, podbase, merchone, prinil, theprintondemandplaybook) on saturation and style volumes; RVIA profile pages.
