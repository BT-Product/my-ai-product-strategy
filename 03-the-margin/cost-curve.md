# Cost Curve & Pricing Strategy

## Cost Model

| Cost Category | Per-User/Month | Notes |
|--------------|----------------|-------|
| Inference (primary model) | ~$0.50 average (~2 events) · ~$1.08 engaged (~4.3) · ~$2.30–2.90 heavy (~8–10) · ~$7.50 daily use | Claude Sonnet 5.5 with web search. About 25¢ an event: the read, follow-up and recommendation measured on one real event (Nov 8); the mirror check (built, not yet measured) and "Change something" (not built) estimated. Excludes the test-only plain-assistant call |
| Inference (cascading/triage) | ~0.3¢ average · ~1.5¢ heavy month (about 1% of Sonnet) | Claude Haiku 5.5: structures each event and reads his post-event written answers; wardrobe import (internal accounts only). Intake measured at 0.05¢ an event (Nov 8); the rest estimated |
| Infrastructure | ~$2.50 at 10 men · ~10¢ at 1,000 men, for every segment | Fixed: ~$25 a month today → ~$100 at 1,000 men. Variable: about zero in the test (notifications are free; email at this volume costs next to nothing). Hand-sent texts only when both miss. Estimated |
| Data/storage | Under 0.1¢, even in his second year | ~9–10 photos an event at ~300 KB: ~70 MB a year average, ~150 MB engaged. Overage ~$1 a month at 1,000 men; serving stays inside included transfer. Photo tokens are counted under inference. Estimated |
| Human-in-the-loop | $0 a month. The quick read is one-time: ~$1–2.50 per man, booked as activation | Nothing waits on a human. The quick read, once bias checks exist, is approved by me: 2–5 minutes at $60 an hour. Automated after 30 reviews meet the bar |
| **Total AI COGS** | **At 1,000 men: ≈$0.60 average · ≈$1.18 engaged · ≈$2.40–3.00 heavy** (≈$3.00 average at 10 men) | Up from $0.46 / $0.84 / $2.17 with the 13¢ estimate, and down slightly since texts were replaced by notifications and email (Nov 10). A heavy man costs about 4.5 times an average one, because AI cost grows with every event. Sonnet is the biggest line at scale, and the read is the biggest step in it; fixed infrastructure is the biggest at 10 men |

### Inference (primary model)
**Claude Sonnet 5.5, with web search.** Partly measured: one real event on Nov 8 (n=1, the builder). The mirror check is built but not yet measured, and "Change something" isn't built, so both are estimated. The mirror check's cost can be measured from its logs now.

**Cost per event:**

| Step | Cost | Source |
|---|---|---|
| Intake (Haiku) | 0.05¢ | Measured |
| **The read** (medium effort, web search) | 13¢ on the measured event; about 9¢ with research and 3¢ without in the eval | Measured, plus the eval |
| Follow-up | 4¢ | Measured |
| Recommendation (medium effort; no backup outfit anymore) | 8¢ | Measured |
| Mirror check (~0.9 per event, ~4¢ each) | 3.6¢ | Estimated |
| "Change something" (~0.25 per event, generated live; a revised outfit, so priced like the 8¢ recommendation) | 2¢ | Estimated |
| **Planning number** | **~25¢** | |

**Why 25¢:** About 35% of men will name a public place, so most reads skip research. At that mix, the read averages about 6.5¢ and an event about 24¢. If every read cost the measured 13¢, an event would be about 31¢. 25¢ sits inside that 24–31¢ range. It's double the old 13¢ estimate, mostly because the read is a new step.

The test-only plain-assistant call is covered under "Not in monthly COGS" below.

**Per man per month:**
- **Average paying man** (~2 events): ~$0.50
- **Engaged** (~4.3 events): ~$1.08
- **Heavy, in holiday season** (~8–10 events): ~$2.30–2.90. That's about 29¢ an event, on the assumption that heavy men do more mirror checks and rescues per event (about 1.5 checks and 0.5 rescues) while rotating outfits across back-to-back parties. The per-task logs check it.
- **Stress case, daily use** (~30 events): ~$7.50

**Average vs. active men:** The ~2-event average includes men drifting toward cancelling. The Module 1 moat milestone (10+ events at 3 months) counts only men still active, and assumes they average at least 3.3 events a month, about the "engaged" segment above. That's an assumption, not a measurement; the January cohort (from Jan 4 at the earliest) checks it.

**Measured:** every model call logs its tokens and cost, tagged by task (intake, the read, follow-up, recommendation, plain assistant, mirror check, rescue). The first real event was logged on Nov 8.

### Inference (cascading/triage)
**Claude Haiku 5.5.** Estimated; measured from Nov 3.

**What it does: it parses.** At each event's intake, it structures the event (type, setting, time, who'll be there). After the event, it reads his written answers. Intake runs every event, not once.

**Names, once:** the intake model (Haiku) reads his raw words once, names included, and replaces names with roles ("Person A, investor"). Nothing stored and no later model call contains a name, and the call log stores token counts and costs, never text. Other people's names are never stored, so "who saw him in what" tracks roles only, and it's Horizon 3 (decided Nov 15).

**Cost:** about 0.1–0.15¢ per event, so roughly **0.3¢ per man per month on average and 1.5¢ in a heavy month**, about 1% of the Sonnet cost.

### Infrastructure
Estimated.

**Fixed:**
- **Today:** about $25 a month: Supabase Pro. Hosting is free during the test.
- **At ~1,000 men:** about $100 a month: database compute, hosting and the email sender (its price to be confirmed).

**Variable: about zero.** The event-day messages (the mirror prompt about an hour before, the morning-after check-in, and a reminder when needed) arrive as **a notification from the home-screen app, with email as the backup** (decided Nov 10, reversing the Oct 30 choice of texts). **Setup asks for neither.** Right after his first outfit, Ellis asks once for the home-screen icon and notifications together, framed by what they do: "Want a reminder to check at the mirror before you head out, and a quick 'how did it go' after?" Email stays the backup, so saying no costs him nothing (decided Nov 11; not built yet). Notifications are free, and email at this volume costs next to nothing. If both miss, I text him by hand from the separate Mercer + Taylor number.

**Per man per month:**
- **At 10 men:** ~$2.50
- **At 1,000 men:** ~10¢, for every segment

**Why notifications replaced texts:**
- Business texts in the US need carrier registration, with an unknown wait, which would have held up the test.
- The 10 men are recruited personally, so asking them to add the icon is reasonable.
- Since Nov 9, sign-in works inside the home-screen app (an emailed code), and email already works because sign-in uses it.

**The saving of about 3¢ an event happens now, not later, and the risk is measured instead of avoided.** A man who skips both the icon and email never gets the morning-after question, which would lower the report-back rate for reasons that aren't Ellis. So every message records its channel (notification, email or a hand-sent text), and **the report-back rate is reported by channel.** That's the comparison this section once wanted before switching, run the other way round. Texts become the option to test if notifications and email underperform.

### Data/storage
Estimated.

**What he uploads:** He photographs the pieces he's considering at each event; there's no closet setup (the wardrobe import from his own assistant is internal-only for now). That's about 9–10 photos per event, resized on the phone to ~300 KB: **~70 MB a year for an average man, ~150 MB engaged.**

**Storage:** 1,000 men pass Supabase Pro's included 100 GB in about a year. The overage is ~$1 a month, under 0.1¢ per man.

**Serving:** about 7 MB per event, so ~30 GB a month for 1,000 engaged men, inside the included transfer. The real cost of serving photos is model tokens (~2.6¢ per recommendation, counted under inference), not transfer, so resizing cuts both.

**See each piece once, describe it from then on.** The first time a piece appears, the model describes it once (color, fabric, cut, fit on him), and we store that description. After that, he taps pieces already on file and photographs only new ones. The recommendation gets the stored descriptions plus any new photos. Photos per event fall as his closet builds, which cuts both his friction and the photo tokens, and the closet grows one event at a time. It ships only if the eval shows stored descriptions lose nothing against photos.

**What we keep:**
- his piece photos, while he's active;
- mirror photos, resized, for 90 days, then only a clothes-only thumbnail. A mirror rejection kept longer as an eval case needs his agreement first (a Module 5 question);
- the quick-read photo, deleted once the read is approved.

Storage grows with his history, but slowly: under a cent a month even in his second year.

### Human-in-the-loop
**Today, nothing in the prototype waits on a human.** Ellis's recommendation goes straight to him; I don't approve it first.
- **Why:** the bet is that men act on AI advice. Reviewing every outfit would turn the test into a human stylist with AI drafts, and it would hold up an outfit he needs before his event.
- **How quality is protected instead:** before any man sees the product, it has to pass an eval and a readiness bar.

**The one planned human step is the quick read.** He sends an optional photo of himself, and Ellis drafts which colors and cuts suit him. Because that judges his appearance, a person approves each read before he sees it, until the trust and guardrail rules exist. It's out of the 10-man test and the cohort (whether men would share the photo is asked in the follow-up call instead) and waits on bias checks (Module 5; not a Horizon 2 or 3 bet).

**The quick read is a deliberate exception to two rules, so it has its own:**
- **Its own line instead of clothes-only:** Ellis says what suits him, never what's wrong with him. Colors and cuts that work, and nothing about weight, hairline or age.
- **His agreement instead of the face crop:** the read needs his face and skin tone, so the photo goes to the model uncropped, but only after he agrees to that for this one photo.

**Cost when it runs** (estimated):
- **Per read:** about 2–5 minutes at $60 an hour, so $2–5, once.
- **Per man:** about $1–2.50, if half of men add a photo.
- **At 1,000 new men a month:** 20–40 hours a month, a part-time role.

**When it goes away:** we automate it, keeping spot checks on 10% of reads, after 30 reviews with at least 90% approved unedited and none crossing the quick read's own line. None have been reviewed yet. Zero problems in 30 reviews still allows a true rate up to about 10% (the rule of three), so the 10% spot checks stay. If reviews pass about 5 hours a month before then, we pause the quick read rather than hire.

**Not counted here (test costs):**
- reading each recommendation after he's seen it;
- texting by hand, only when a man's notification and email both miss;
- the optional follow-up call.

### Not in monthly COGS
- **The plain-assistant comparison is a test cost.** Each man's first event gets one plain-assistant call for the blind panel. It was measured at 4¢ without search; it now runs with web search, so it's estimated at about 4–10¢ (a search adds about 6¢, from the read's eval: ~9¢ with research vs ~3¢ without). That takes the first event to about 29–35¢. Measured again on the first real pair. It's never shown to him. It runs during the prototype test, and in the cohort if H1 needs a retest, and is removed once H1 is proven.
- **The optional quick read is the only one-time cost in the product,** booked as activation: a few cents of model cost plus the reviewer's time (~$1–2.50 per man; see Human-in-the-loop). The reviewer's time is the real cost until it's automated.
- **The monthly gap check is a small fixed cost, not a per-man one:** our model vs. a plain assistant on stored cases, run offline. So are eval runs and the judge.

## Cascading Strategy
<!-- Cheap model → frontier model routing logic -->

**Triage model:** Claude Haiku 5.5, one-twentieth of Sonnet's price per token ($0.10 / $0.50 per million input / output tokens, vs $2 / $10).
- **Today:** intake (reading his description and removing names), turning a pasted wardrobe list into pieces, and the backup when "Change something" fails on Sonnet (one try, then he's asked to try again). That backup hasn't passed its eval yet: it passes before the test or comes out.
- **Candidate:** the read when he names no public place (about 65% of reads, our assumption). It moves only after Haiku matches Sonnet on the read's eval, especially on asking for the right pieces, which decides the first try.
- **Not moving:** naming pieces from his photos (Haiku called denim chambray), and the mirror check and try-on (clothes-only at 100%). The mirror check is Sonnet only, with no backup yet; Haiku waits on the clothes-only cases.

**Frontier model:** Claude Sonnet 5.5 at medium effort, for every step that decides the first try: the recommendation, the read when it researches a named place, the follow-up question (it has to see the photos), and the mirror check and try-on.
- **Opus is dropped for now (decided Nov 12, build repo).** The recommendation stays on Sonnet. Cost wasn't the reason: Claude Opus 5.5 costs twice Sonnet per token ($4 / $20), about 13¢ more on a first event, about $1.30 across the 10-man test. Speed was: the recommendation already takes about 20 seconds while he waits, Opus is slower, and the stage-talk rerun gave no sign the model decided the outfit.
- **The plain assistant in the panel always runs on the same model as Ellis,** so a win reflects our craft, not a bigger model.

**Routing rule:** Intake runs before the read and already records whether he named a venue. If he named a public place, the read runs on Sonnet with web search; if not, on Haiku (once Haiku passes the eval). Every recommendation, mirror check and try-on stays on Sonnet regardless. Two exceptions keep the first try safe:
- **His first event's read stays on Sonnet.** The asks are the edge, and the first try never gets cheaper. Only later reads move. The saving barely changes, because the first event is one of many.
- **When in doubt, Sonnet.** Haiku runs intake, so Haiku decides the route. If intake isn't sure he named a public place, the read goes to Sonnet, so a missed venue never silently loses its research. The read's eval checks the router: intake flags named public places correctly in X of Y cases.

**Expected cascade ratio:**
- **By calls:** about 28% on Haiku if the read moves (intake on every event, plus about 65% of reads), up from about 17% today.
- **By cost:** small. The no-search read drops from about 3–4¢ to about 0.2¢, saving about 2–2.5¢ of about 25¢ an event (~10%). Most of the cost is the recommendation, which by design never moves down.

## Pricing Model

**Current pricing:** None. The prototype is free and pre-launch.
**Proposed AI pricing:** **$11.99 a month**, the one price the cohort tests. Priced against the general assistant he already pays for, about $20 a month, which helps him in many areas. The closer Ellis gets to $20, the more it has to beat an assistant that does far more than dress him.
- **Why the top of the $9.99–11.99 range:** paying men also carry the free men. In the planning case below, an engaged paying man costs about $5.76 a month (his own ~$1.31, card fees ~$0.65, and ~$3.80 for the free men he carries): a gross margin of about 52% at $11.99, against about 43% at $9.99. A commitment at $11.99 is also stronger evidence than one at $9.99.
- **What the free tier needs: two unknowns, not one.** Free men cost margin, so the share of men who pay has to clear a bar, and that bar depends on how often free men actually use their free event:

  | A free man uses his free event… | His cost a month | Paying share to stay above the 50% floor | Paying share to break even |
  |---|---|---|---|
  | Every month (worst case) | ~41¢ | ~9% | ~4% |
  | **Every other month (planning case)** | **~20¢** | **~5%** | **~2%** |
  | One month in three | ~14¢ | ~3.5% | ~1.5% |

  Freemium products commonly convert something like 2–5% of free users. If every free man uses his event monthly, the free tier as designed doesn't work. If free men are as occasional as their events, a typical 3–5% works. **The planning case:** free men use their event every other month and 5% of men pay (about 19 free men per paying man), for a margin of about 52%. These pricing and stress-test margins were computed with texts at about 3¢ an event; since texts were replaced by notifications and email, they run about 2–3 points better, so the figures here are slightly conservative. The cohort measures both unknowns: the founding-member payment gives a first, friendly read on the paying share, and logging free and paid events separately shows how often free men come back.
- **$20 isn't a hard ceiling.** Men pay for single-purpose apps alongside general ones when one job done well is worth it. The follow-up call asks two price questions to show whether $11.99 sits near the floor or the ceiling (see Module 1, criterion 3).
- **Exposure to a model price change:** an Anthropic doubling would cost about 8–11 margin points on a paying man alone at $11.99 (Module 2, kill switch), and about 29 points counting the free men he carries in the planning case.
- **The floor: 50% gross margin per paying man,** counting the free men he carries. If margin falls below it for any reason (a model price change, heavier use, more free men per paying man), we act in this order:
  1. the kill switch's cost cuts (caching, smaller photos, effort, moving "Change something" to Haiku);
  2. tighten the free tier's allowance, never its quality (for example, the first event free, then one a quarter instead of one a month), so paying men don't pay more to support free men;
  3. raise the price.
  - **How close it is:** the planning case's ~52% is an estimate resting on both unknowns above, only 2 points above the floor. In the worst case (every free man uses his event monthly, 5% paying) margin is about 19%, well below it. The floor is checked once the cohort measures both unknowns. **The free tier, not the paying men, is the biggest margin risk.**
**Model:** Hybrid, on top of a free tier.
- **Free: one event a month,** with the full flow the blind panel tests (the read, the asks, the outfit, the mirror check, the two check-ins) and his history kept. A man with one event a month never feels he's overpaying, and every free man still reports back, which the moat and the report-back kill rule both need.
  - **What that implies:** men pay for frequency. If most men have one event a month or fewer, few will convert. The all-men reading of criterion 4 (Module 1) measures exactly this, so it also tests the pricing.
- **Paid: a monthly subscription with a fair-use cap of about 20 events a month.** At the cap, his cost is about half his subscription, so a normal man never sees it. Above it, a second, higher tier with a higher cap, for the man who needs more events, not more features. **He's never stopped before an event:** the event that crosses the cap goes through, and the upgrade is offered afterward.
- **Heavy users pay through the higher tier and add-ons, not a charge per event.** Paying per event would work against coming back unprompted (Module 1, criterion 4). Candidates: the full wardrobe and the try-on days ahead, each its own sub-bet. Which add-ons heavy users value is unknown, so they're designed after the cohort shows who's heavy and what they use.
- **Never add-ons:** the mirror check, the two check-ins, "Change something" and his history. They build the record the moat depends on.
- **The cohort tests one subscription price.**
- **Ruled out: outcome-based pricing.** Charging only when he felt Great would corrupt his answers to "How do you feel in it?" and "Was it right for the room?"

## Stress Tests

| Scenario | Impact on Margin | Response |
|----------|-----------------|----------|
| Inference costs 3x | ~52% → about −6% (losing money). Paying men alone: ~84% → ~66% | The order of moves: cost cuts that don't change what he gets, then lower effort or Haiku where the eval shows no loss, then the free tier's allowance (never its quality), then price, last |
| Heaviest segment doubles (a heavy man goes from ~10 to ~20 events a month) | That man: ~35% → ~9%. Paying men alone: ~67% → ~40% | Still not a loss. The fair-use cap (~20 events) holds his cost to about half his subscription; above it, a higher tier. A thin margin on a few heavy men is acceptable: they build the record fastest |
| Model provider raises prices 50% | ~52% → ~38%, under the floor. Paying men alone: ~84% → ~79% | It crosses the size line for switching providers, but not the quality line: no backup has passed the eval. Absorb it with row 1's moves, and running the backup ranking becomes the priority |

**Assumptions:** the planning case (an engaged paying man at $11.99 carrying about 19 free men who use their event every other month). In the worst case (free men use their event every month), every row starts from about 19% instead of 52%. The pattern holds either way: paying men stay above the floor in every row except the doubled heavy man; the free men are where each shock multiplies.

**Inference costs 3x: the order of moves.** The free tier's size isn't cut first.
1. **Levers that don't change what he gets:** cache the style guide, send smaller photos, shorten output. (The plain-assistant call ends once H1 is proven, but it's a test cost and already outside these numbers.)
2. **Lower effort or Haiku on a step,** only where the eval and a blind taste check show no loss. Our own runs show both can cost quality: low effort broke the answer's format, and Haiku misread a piece's cloth and an event's type. So some steps won't qualify, and the first-event recommendation never does.
3. **The free tier's allowance, never its quality:** for example, the first event free, then one a quarter instead of one a month. The first-event recommendation never gets cheaper; it's the hook.
4. **Price, last.** It's what the cohort tests, so it doesn't move mid-test.

Every free man active every month is the worst case; a free man who doesn't use his event costs almost nothing.

**Heaviest segment doubles: not a loss.** A paying man's own costs pass his $11.99 only past about 35 events a month, more than one a day (about 24 counting the free men he carries in the planning case). The fair-use cap sits around 20, where his cost is about half his subscription, so a normal man never sees it. Above the cap, a higher tier with a higher cap. Heavy men build the record fastest, which is the moat, so a thin margin on a few of them in December is acceptable. Per-man cost is logged, so we'd see it coming.

**Provider raises prices 50%: absorb it, and make the switch real.** It crosses the size line for switching (about 14 points on the full mix and about 5 on paying men alone, against the kill switch's ~3-point rule) but not the quality line: no backup has passed the full eval, including clothes-only at 100%, and the ranking run against OpenAI and Google hasn't happened. So we absorb it with row 1's moves, and running the backup ranking becomes the priority, so the switch exists before it's needed.

**What the table teaches:** the exposure is the free tier, not paying men. That's why the free tier's allowance is a lever, and why the first free event has to win: every free man who never converts is pure cost.

## Board One-Pager
<!-- Before/After: Old SaaS revenue vs. AI usage revenue for your product -->

**Before (traditional SaaS):** A style app built on rules, with no AI. Gross margin around 80–85%, as software is commonly described, with almost no cost per use. But it can't do the job: it can't see his closet, read the event, or check him at the mirror. He'd still fill in everything himself.

**After (AI-enabled):** Ellis at $11.99 a month. Every event costs about 25¢ in model calls, so cost grows with use.
- **Paying men alone:** about 84% gross margin, on par with software.
- **Counting the free men they carry:** about 52% in the planning case (5% of men pay; free men use their event every other month), and about 19% in the worst case.

**Net margin shift:** about 30 points lower than software (from ~80–85% to ~52%), and almost all of it comes from the free tier, not the paying men. AI didn't cost us margin on the men who pay; it made giving the product away expensive. The shift is worth it because AI does a job software couldn't, at about one-hundredth of a stylist's price ($11.99 a month against $100–500 an hour), and it scales without hiring. The board's number to watch is the share of men who pay, with how often free men use their event next to it.

**Covering the team:** gross margin covers model, hosting and card costs, not people, and Mercer + Taylor's team is the bigger cost. Phase 1 is about $150K for a quarter (two engineers on loan and a part-time stylist); a three-engineer team runs about $60K a month.
- **Planning case:** each paying man leaves about $6.23 a month after his own costs and the free men he carries ($11.99 − $5.76). Covering $60K a month takes roughly 9,600 paying men, about 190,000 men in all at 5% paying.
- **Worst case** (about 19% margin, roughly $2.30 a paying man): about 26,000 paying men.
- **What it means:** the first year buys evidence, not revenue, and the free tier's allowance is the first lever, because it moves the number of men needed more than anything else.
