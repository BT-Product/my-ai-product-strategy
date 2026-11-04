# Three-Axis Vulnerability Diagnostic

## Product
<!-- Name the product you're diagnosing. Real product at your company — not a hypothetical. -->

**Product:** Mercer + Taylor, an AI personal stylist for men in their 30s–40s earning around $250K a year, mostly in tech, finance and real estate.

**Buying triggers:**
1. **Career inflection.** A promotion, a new leadership role, or fundraising, where founders feel they represent their company in investor rooms.
2. **Re-entering dating,** often after a divorce, sometimes on a matchmaker's referral.
3. **Time scarcity plus boredom.** Short on time, unsure what works, tired of grays and navy.

**Buying channel: partner pressure.** A wife or girlfriend pushes him to go, so the buyer and the user can be different people. *(Reclassified in Module 2: this is how he arrives, not a moment when he needs to dress well.)*

**Your Role:** Solo founder, building the product myself. I'll hire a team once testing confirms the core assumptions.

---

## Scores

### Contextual Moat — 1/5 today · target 4/5
*Workflow depth × switching cost. Would users leave in a weekend if a competitor showed up?*

**Score rationale:** We're pre-launch with no users, so nobody loses anything by switching today. We earn a 4 by building up a record of what actually happened, which he can't export and can't describe to another tool, because most of it he doesn't consciously know:

1. **Event outcomes.** For each event: what was recommended, what he chose, what he actually wore, what he changed and why, and how it went. This record doesn't exist anywhere else.
2. **Revealed taste vs. stated taste.** He always swaps the loafers for boots, never wears the pink shirt, and follows color advice but not fit advice. This is learned only from the gap between what was recommended and what he wore, so he can't type it into ChatGPT.
3. **Who saw him in what.** "You wore the navy suit to the last two meetings with this client." "She's seen the green jacket twice." A good human stylist tracks this. An assistant with no history can't, and it's worth the most at the high-stakes events our audience cares about.
4. **Combinations proven on him.** Which pieces worked together, at which kinds of events. Re-photographing the closet somewhere else is easy; rebuilding what works isn't.
5. **Fit by brand.** A fit passport with alterations on file. It's moderately annoying to rebuild, and it supports the buying side of the business.

**Milestone (target earned when):** 60% of users still active at 3 months have 10+ events logged with outcomes. The ideal user has about one event a week, and 10 events with outcomes is enough to personalize his stylist. This counts only men still active, and assumes they average at least 3.3 events a month, well above the ~2 of the average paying man in the Module 3 cost model. The Nov 30–Dec 20 cohort checks it.

**Critical assumption:** He reliably reports back what he wore and how it went. Hooks 1–4 all depend on that loop. If capturing it takes effort and he stops, the moat never forms.

**Named attacker (from partner challenge):** Whatever general-purpose LLM he already uses every day (ChatGPT, Claude, Gemini). It's already in his workflow and costs him nothing extra, and its basic style advice may be good enough.

---

### Data Advantage — 1/5 today · target 3/5
*Proprietary signal that compounds with usage. What do you see that OpenAI doesn't?*

**Score rationale:** We have no data today. The target is 3, not higher, because the advantage is narrow (high-stakes events, one audience) and a well-resourced competitor is one feature away from collecting similar data.

**Milestone (target earned when):** About 500 outcome-labeled events across 100+ men. That's the point where pooled data measurably improves a new user's first recommendation: it gets "This isn't me" **35% less often** with pooled data than with a general-LLM baseline that has no pooled data.

**The compounding signal:** Outfits labeled with outcomes for high-stakes events. Each event pairs:
- what was recommended
- what he actually wore, verified by a pre-event mirror photo
- what he swapped, and why
- the event type, season and setting
- how it went: a one-tap check-in after the event, at a time he picks at the mirror (that evening or the next morning)

**Capture design:** Data is captured at the moments when he wants help, so logging isn't a chore.
- **"Check me":** he snaps what he has on and gets a reply about the clothes only ("You're good. Tuck the shirt.").
- **"This isn't me":** he can tap it any time before the event, with an optional one-tap reason (Fit's off · Too formal · Too loud · Not comfortable · Just not me). He gets an instant rescue: a different outfit built from pieces he's already photographed. He can also snap what he ends up wearing, so the record shows what actually went out the door.
- **Post-event check-in:** "Would you wear this again to this kind of event?" 👍 / 👎. One tap labels the outcome, distinguishing the outfit he picked from the outfit that worked.

**Named attacker (from partner challenge):** Stitch Fix. They already have millions of men using the service, plus their sizes and purchases. Asking "What did you wear this to, and how did it go?" is a feature they could add.

---

### Platform Exposure — 2/5 today · target 3/5
*Encroachment risk × pivot speed. If Apple/Google/OpenAI ships your hero feature native — then what?*

*Scale (instructor): 1 = pain · 5 = strong.*

**Hero feature:** Tell it about a high-stakes moment and snap the pieces you're considering, and it gives you one opinionated outfit from your own closet: what to wear, why it works, and what not to wear.

**Hook vs. moat:** The hero feature is the hook, and it's deliberately the part that can be copied. It only has to win the first try. Defensibility comes from the history it starts. The metric that matters is **time-to-moat**: we aim for his second recommendation to visibly use his history.

**Score rationale:** A generic version of the hero feature already works in ChatGPT today, so we're not at 1 only because a platform is unlikely to build for this niche specifically, and a solo founder can pivot within a week. We reach 3 when the history, not the hook, is what men pick us for.

**Milestone (target earned when):** Both of these hold:
- At least 70% of men choose our recommendation over a plain assistant's in a blind side-by-side test on our golden cases.
- At least 40% of second and later events get a recommendation that visibly uses his history: what he rejected at the mirror, who saw him in what, and what he felt great in.

**Named attacker (from partner challenge):** OpenAI (ChatGPT). It already has vision, memory and shopping features, and it's an app he opens every day. Runner-up: Google, which owns his calendar and photos.

**The week it ships:**
1. **Day 1:** Run the blind side-by-side against the general assistant on our golden cases to measure how much of a gap is left.
2. **If men pick us 70% of the time or more:** Lead with what they can't copy: the pre-event check and "This isn't me" at the mirror, his record of what he wore and rejected, who saw him in what, and his lookbook.
3. **If men pick us 50% of the time or less:** Pivot. The free tier moves inside ChatGPT as a third-party app, with the same style guide and the same record. Our own app becomes the paid stylist that holds his history.
4. **Either way:** Show every current user what we already know about him ("6 events, 2 rejections at the mirror, your best look"), so the cost of leaving is visible before anyone tries the alternative.

**If men pick us between 50% and 70% of the time:** Treat it as "not proven yet," not as a pass or a fail. Spend the week finding out why men chose the plain assistant, fix the biggest reason, and test again with the same cohort.

**Ongoing:** Run the blind side-by-side monthly from the first golden cases, so the gap is already known on the day a platform ships.

---

## Top Vulnerability
<!-- One line: what's the single biggest strategic risk? -->
**Users don't report back.** Every part of the Contextual Moat, all of the Data Advantage, and our only defense against platform encroachment are built from what he tells us after each recommendation. If reporting back is a chore, the product still looks like it works, but nothing compounds.

**Mitigation:** Reporting back is designed as the reward, not a form: the pre-event "Check me" and the instant rescue when he taps "This isn't me."

**Kill rule:** Fewer than 50% of events get a check-in within 48 hours. Only the post-event "Wear again?" tap counts as a check-in. "Check me" and "This isn't me" happen while he's anxious and motivated, so they would flatter the number. The outcome tap is the hardest to get and the one the Data Advantage depends on.

## Confidence Level
<!-- H / M / L — how confident are you in this bet after the diagnostic? -->
**L.** Every axis scores 1–2 today, and there's no user evidence yet. A two-week test raises it if men choose our advice over a plain assistant **and** report back, both at 70% or higher. It ends or repositions the bet if the side-by-side falls below 40% or report-back falls below 50%. Thresholds and sample design are in [prototype.md](prototype.md).
