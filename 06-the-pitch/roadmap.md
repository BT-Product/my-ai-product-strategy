# Three-Horizon Roadmap & Board Pitch

## Roadmap

### Horizon 1 — Now (0-3 months)
*Quick wins. Ship with existing capabilities.*

| Initiative | Metric | Confidence |
|-----------|--------|-----------|
| **Finish the build the test needs** (Nov 16–about Dec 4): the pick question, the two check-ins with ✓ / Fix, the timing fix, the plain assistant's new inputs, the off switches, the service key out of local development | One full event on my phone, start to check-in, every record written; the eval passing on every new step; under 3 minutes from describing the event to the outfit (not yet measured end to end) | H on the build · M on speed |
| **Run the 10-man test** (about Dec 7–20, midpoint review about Dec 13–14) | Panel picks ≥70% of pairs (standard pairs reported separately; "styling only" if fewer than half are standard); report-back ≥70% of events with the room answer within 48 hours (under 50%, the kill rule fires); hit rate 65%, supporting | L–M on panel picks (one loss, one win, both mine, not blind) · M on report-back |
| **Run the cohort with the price offer** (~20 men: the test men who want to continue, plus referrals; from Jan 4 at the earliest, for three weeks) | 70% take the paid first month (about 14 of 20); 40% bring a second event unprompted within 14 days; a blind panel prefers later outfits made with his history over the same outfit without it on 60%+ of pairs | L (willingness to pay is the weakest link) |

**Dates (decided Nov 15):**
- **Build:** Nov 16 to about Dec 4.
- **The 10-man test:** about Dec 7–20, in holiday-party season (real events, skewed to one type, so results are reported by event type), with a midpoint review about Dec 13–14. Bugs and screens are fixed as they show up; only the prompts are frozen.
- **The cohort starts on a gate, not a date:** the test's fixes built, the new prompt version passing the eval and the blind taste check, and the readiness bar holding. That's Jan 4 at the earliest, Jan 11 if the test turns up problems, for three weeks; the readout lands in late January or early February. _Why a gate:_ the team is off Dec 25–Jan 1, so about four working days separate the test from Jan 4, and late check-ins run to about Jan 3.

**Problems are sorted before any data:**
- **Bugs and screens** are fixed during the test.
- **Prompt and taste problems** go into one new prompt version for the cohort (the "diagnose, make one fix, retest" path for panel picks between 50% and 70%).
- **Panel picks of 40–49%** mean Ellis lost: a redesign, not one fix, and the cohort runs as a retest without the $11.99 offer until picks reach 50% (added Nov 16).
- **A kill rule firing** (panel picks under 40%, report-back under 50%) means the cohort doesn't run as planned until the bet is redesigned or rethought.

The capstone versions of Nov 16 and about Nov 23 contain no test data, and say so.

### Horizon 2 — Next (3-9 months)
*Bets. Requires new capabilities or integrations.*

**The bridge from Copilot to Orchestrator** (Module 1's path: Ellis moves toward Orchestrator at Horizon 2, "when it prepares him for events from his calendar without being asked") is Ellis preparing him without being asked, so Orchestrator belongs here.

| Initiative | Metric | Confidence |
|-----------|--------|-----------|
| **Ellis prepares him without being asked.** First, outreach a week before events he's flagged; then, only if that works, read-only, opt-in calendar access for flagged events. Ellis prepares the outfit early and flags a gap while there's time to buy, rent or tailor; it never buys or books | At least half of outreach messages lead to a started event, and fewer men also ask their own assistant for those events; gaps found early, supporting. Today: no data (tested by hand in the cohort) | L–M: the edge is outreach plus his wardrobe plus taste, since platforms are moving toward proactive calendar features |
| **Proposing from his wardrobe when it covers the event,** the first step from a workflow toward agency: after the read, one step chooses to propose now, ask questions or ask for pieces, tried first as rules in code | For men whose wardrobe covers the event, time to the outfit roughly halved with no drop in the hit rate; the right path chosen on at least 90% of the routing eval's cases | M (one real case, mine) |
| **A limited paid launch** (about March, ~200 men, only if both January checkpoints pass): recurring $11.99 billing, a small acquisition budget, and a one-event price tested against the subscription | Profit per paying man over his first 90 days above zero; at least 5% of men paying; at least half of paying men still paying after 90 days; acquisition cost measured | L (no man has paid yet) |
| **A backup provider that passes the eval** (Portability: Partial → Ready) | One provider passes every zero-tolerance case at 100% and the hard rules, and is rated at least as good in the blind taste check 80% of the time. Today: no backup tested | M |

**Not in Horizon 2:**
- **Who saw him in what:** it needs several events of history per man first.
- **The quick read:** it waits on the bias checks and on trust with a photo of himself.

**Outreach and "comes back" (decided Nov 15):** "comes back" stays unprompted (40%). In the cohort, outreach covers only the events he listed at recruitment; "comes back" counts only second events he starts himself, outside that list, and outreach-started events are reported separately against outreach's own target (see Module 1, criterion 4).

### Horizon 3 — Bet (9-18 months)
*Moonshots. High uncertainty, high potential.*

H1 proves Ellis wins a first try; H2 makes Ellis the first place he goes; **H3 makes Ellis worth more every season and costly to leave.** What does both is his record, not his wardrobe (which moves between assistants): what worked for him, in which rooms, in front of whom, labeled by him at the mirror and the morning after. His own assistant remembers what he said; Ellis would hold what happened. H3 bets on what that record lets Ellis do that nobody else can.

| Role | Initiative | Metric (today → target) | Confidence |
|------|-----------|--------|-----------|
| **The moat** | **His record becomes his style history:** what he felt great in, what was right for which rooms, what he changed and why, who has seen him in what (by role), and his fit notes for a tailor. Every new outfit is built from it; he can see it and correct it | Today: no men, one record (mine). Target (draft, set before data): for men with 5+ events, the hit rate on later events at least 15 points above their first events, with fewer pieces changed at the mirror; at 6 months, at least half of active men still bring events on their own | M that it improves his outfits; L that it keeps him, since it rests on report-back |
| **The upside** | **Ellis plans his wardrobe, not just his outfits:** a seasonal plan built from his record, his upcoming events and the gaps in his closet: what to buy next, what to stop wearing, and why, from evidence only Ellis has ("your charcoal suit was Great and Right at every client dinner, but you were Too dressed at three tech events, so the next piece is an unstructured navy jacket"). It grows the job from dressing him for Tuesday to being his stylist for the year, the work a human stylist charges $100–500 an hour for, and gives the paid tier something clearly worth paying for. Ellis plans; he buys: no links, no commissions, real gaps only | Today: no plans; buying is tested as single suggestions. Target (draft): of men offered a seasonal plan, at least a quarter buy one or more planned pieces within the season, and planned pieces score a higher hit rate when worn than unplanned buys | L: it needs enough history per man to plan from, and men acting on a plan, not just an outfit |
| **Scale** | **Pooled house style at 100+ men** (the Data Advantage milestone; the Network loop conceded at 10 men): patterns across men by event type, curated, 3+ men each, passing the golden set | Today: 0 outcome-labeled events from men. Target: about 500 outcome-labeled events, and new men change 35% fewer pieces of their first outfit with pooled data than with a general-LLM baseline that has no pooled data (Module 1's Data Advantage milestone) | L |

**The history risk is worked down in H1 and H2, not left for H3:**
- the two check-ins record an outcome even when the morning message never reaches him;
- reaching out first brings more of his events to Ellis;
- proposing from his wardrobe makes each event cheaper to bring;
- the import gives his record a head start.

**Not H3 bets:**
- **The full wardrobe:** table stakes, since import works both ways; a paid-tier candidate, not a moat.
- **The quick read:** copyable and the highest bias risk; a feature once bias checks exist.
- **Add-ons and the higher tier:** pricing decisions from the cohort's data.
- **Purchase handling:** Ellis never buys for him; fit notes live in his record instead.

## Board Pitch

**Thesis (1 sentence):** I believe busy professional men will follow an AI stylist that asks the right questions, learns what works, and improves their wardrobe over time, all for $11.99 a month versus hundreds for a human stylist.

**In full:** I believe busy professional men will follow the advice of an AI stylist that knows what questions to ask, learns what works for them, and gets better with every event he shares. Over time, choosing the right outfit becomes easier, and their wardrobe gets better. All for $11.99 a month, compared to the $100–$500 an hour a human stylist might charge.

**The case:**
1. **Why now: why couldn't this have existed two years ago?** Vision models can now tell charcoal wool from grey flannel in a phone photo, read an event from a sentence, and look up the venue. That's a stylist's eye working from what's already in his closet, not a catalog. It costs about 25¢ an event to produce (mostly measured on one event), against $100–500 an hour for a human stylist.
2. **What's defensible: why won't ChatGPT just do this?** I tested that first. On my own first events, I chose my own assistant over Ellis, because it already knew my closet. Then I found out why it won: given the same pieces, both picked the same outfit, so the outfit was never the edge. I rebuilt Ellis around what was: asking for what he wouldn't think to mention wins the first try, though it can be copied; his record wins the second. His own assistant remembers what he said; Ellis holds what happened, labeled by him at the mirror and the next morning. Pooled data across millions of users I concede to the big platforms; depth on each man is where Ellis competes.
3. **The economics: does it make money?** $11.99 a month. About 84% gross margin on a paying man, about 52% once he carries the free men, against a 50% floor. Break-even at about 2% of men paying. The risk to watch is the free tier: if free men use their event every month instead of every other month, margin falls to about 19%, so the free allowance is the first thing adjusted, never the free outfit's quality.

**The risks:**
1. **Trust: what happens when Ellis is wrong about how a man looks?** A single comment about his body, or a flaw invented from a photo, would end his trust at the moment he's most nervous. Ellis comments on clothes only, never on him. Five mistakes are zero tolerance: a comment about his body, an outfit built from a piece he didn't send, a venue fact the research didn't find, a condition flaw the photo doesn't clearly show, and describing anyone in a review photo. Each is checked before any change ships and has its own off switch. When Ellis is unsure, it asks or says nothing rather than hedging, and when something goes wrong, he's told by me within a day.
2. **Scale: what breaks as this grows?** Report-back, the top risk since Module 1: if men stop telling Ellis how it went, nothing compounds and the moat never forms. So the record is collected when he cares, not only the morning after: how he feels in it at the mirror, then whether it was right for the room, with a kill rule under 50%. Behind that: Ellis may prepare, but only he may act; it's a fixed workflow, so every step can be tested and switched off on its own; and production data access is removed from the build tools before the first man. Today it runs on one model provider, with no backup that has passed the eval yet; that test is on the roadmap.
3. **Competitive: what if ChatGPT does this?** It partly already does. In week one I chose my own assistant over Ellis because it knew my closet, and the platforms are moving toward proactive calendar features. The styling edge is thin. Ellis's edge is asking for what he wouldn't think to mention, and a record of what actually worked for him, which his own assistant doesn't collect. Big platforms also keep features that use personal photos shallow, because the liability grows with every user, so a long-term record of how a man looked in which rooms is data they'd rather not hold. That buys time, not a wall, and only if we handle it better than they would. The blind panel tests the first; the cohort tests whether he comes back on his own.

**The ask:** Mercer + Taylor is the company, and Ellis is its first product. Fund two phases, the second only if the first passes. Every number is a planning estimate, set before any data.

**Phase 1: prove the value (about Dec 1 to mid-February, ~12 weeks), about $150K beyond my own time.**
- **Team:** me as product lead, plus two engineers moved from existing teams for one quarter (not new hires; hiring by December isn't realistic):
  - **a full-stack engineer:** the app, the check-ins, production keys out of the build tools, and consent, retention and deletion for his photos and history;
  - **an AI engineer:** the eval from 13 golden rows toward about 500, the judge model, and the panel's pairs;
  - **a stylist, about 10 hours a week,** as a second taste grader, so the eval doesn't rest on my taste alone.
- **Cost:** about $120K for the two engineers (roughly $20K a month each, fully loaded), about $15K for the stylist, and about $15K for raters' thanks, a privacy review and tools. Model calls are a rounding error: about 25¢ an event.
- **Recruiting:** 10 men with an event between Dec 7 and 20, and about 6 more to rate pairs blind, through the company's network.
- **Checkpoint 1, early January: does Ellis beat a general assistant?** The 10-man test. Panel picks of 70%+ pass; 50–69% get one fix and a retest; 40–49% mean Ellis lost and is redesigned; under 40% stops the bet. Report-back under 50% also stops it.
- **Checkpoint 2, early February: will men pay, and does Ellis get better for them?** The ~20-man cohort: 70% make the $11.99 founding-member payment; 40% bring a second event unprompted; outfits made with his history win 60%+ of blind pairs against the same outfit made without it.

**Phase 2: a limited paid launch (about March to August), only if both checkpoints pass, about $400K.**
- **Team:** three engineers and a part-time designer.
- **The work:** a paid launch to about 200 men, with a small acquisition budget so the cost to bring in a man is measured, not assumed; a one-event price tested against the subscription; outreach before events he's flagged; a backup provider that passes the eval.
- **Checkpoint 3, around June: is each paying man profitable?** Profit per paying man over his first 90 days (revenue minus model, hosting and acquisition costs) above zero; at least 5% of men paying (the planning case); at least half of paying men still paying after 90 days.

**When customers pay the $11.99:**
- **About early February:** founding-member payments at the end of the cohort. Real money, refundable until launch.
- **About March:** the first recurring charges, when the limited launch opens, if both checkpoints pass.

**What the board should expect:** first-year revenue is small. If 5% of 200 men pay, that's about $120 a month. Phase 1 buys evidence, not revenue. For scale: paying for a three-engineer team (about $60K a month) takes roughly 10,000 paying men at the planning case's margin, about 200,000 men if 5% pay.

**Hold me to my rules:** the stop lines were set before any data, so nobody can move them afterward, including me. If a checkpoint fails, the engineers go back to their teams and Phase 2 isn't requested.

## M1 Baseline vs. Now
*Your 3-sentence AI strategy from Module 1 vs. what you'd say now:*

**M1 baseline** (from Module 1 as committed Oct 28): An AI personal stylist that tells busy professional men who've never hired a stylist exactly what to wear from their own closet for the moments that matter. Vision models can now see his actual clothes, which brings a stylist's judgment to a fraction of the $100–500 an hour a human charges, without the awkwardness. The hero feature is the hook, deliberately the part that can be copied; it only has to win the first try, and defensibility comes from the history it starts.

**Now (Nov 15):** Ellis is an AI personal stylist that helps busy professional men dress for important moments using clothes they already own: it asks for the pieces and details they might overlook, recommends one outfit, and checks the final look before they leave. A general assistant remembers what he tells it; Ellis is built to record what actually worked, how he felt in it and whether it was right for the room, and to use that to make each recommendation better, and eventually to help him build a smarter wardrobe and anticipate his needs before he asks. One event a month is free; the paid tier the cohort will test is $11.99 a month, against $100–500 an hour for a human stylist.
