# Three-Axis Vulnerability Diagnostic

## Product
<!-- Name the product you're diagnosing. Real product at your company — not a hypothetical. -->

**Product:** Mercer + Taylor, an AI personal stylist for men in their 30s–40s earning around $250K a year, mostly in tech, finance and real estate.

**Buying triggers:**
1. **Career inflection.** A promotion, a new leadership role, or fundraising, where founders feel they represent their company in investor rooms.
2. **Re-entering dating,** often after a divorce, sometimes on a matchmaker's referral.
3. **Time scarcity plus boredom.** Short on time, unsure what works, tired of grays and navy.

**Buying channel: partner pressure.** A wife or girlfriend pushes him to go, so the buyer and the user can be different people. *(Reclassified in Module 2: this is how he arrives, not a moment when he needs to dress well.)*

**Your Role:** Solo product lead, building the product myself. I'll hire a team once testing confirms the core assumptions.

---

## Scores

### Contextual Moat — 1/5 today · target 4/5
*Workflow depth × switching cost. Would users leave in a weekend if a competitor showed up?*

**Score rationale:** We're pre-launch with no users, so nobody loses anything by switching today. We earn a 4 by building up a record of what actually happened, which he can't export and can't describe to another tool, because most of it he doesn't consciously know:

1. **Event outcomes.** For each event: what was recommended, what he chose, what he actually wore, what he changed and why, and how it went. This record doesn't exist anywhere else.
2. **Revealed taste vs. stated taste.** He always swaps the loafers for boots, never wears the pink shirt, and follows color advice but not fit advice. This is learned only from the gap between what was recommended and what he wore, so he can't type it into ChatGPT.
3. **Who saw him in what (Horizon 3, roles only).** "You wore the navy suit to the last two meetings with this client." "Her parents have seen the green jacket twice." A good human stylist tracks this. An assistant with no history can't, and it's worth the most at the high-stakes events our audience cares about. Ellis tracks roles, never names (Module 5), and it's built at Horizon 3, since it needs several events of history per man first; until then, the moat rests on hooks 1, 2 and 4 (decided Nov 15).
4. **Combinations proven on him.** Which pieces worked together, at which kinds of events. Re-photographing the closet somewhere else is easy; rebuilding what works isn't.
5. **Fit by brand.** A fit passport with alterations on file. It's moderately annoying to rebuild, and it supports the buying side of the business.

**Milestone (target earned when):** 60% of users still active at 3 months have 10+ events logged with outcomes. The ideal user has about one event a week, and 10 events with outcomes is enough to personalize his stylist. This counts only men still active, and assumes they average at least 3.3 events a month, well above the ~2 of the average paying man in the Module 3 cost model. The January cohort (from Jan 4 at the earliest) checks it.

**Critical assumption:** He reliably reports back what he wore and how it went. Hooks 1–4 all depend on that loop. If capturing it takes effort and he stops, the moat never forms.

**Named attacker (from partner challenge):** Whatever general-purpose LLM he already uses every day (ChatGPT, Claude, Gemini). It's already in his workflow and costs him nothing extra, and its basic style advice may be good enough.

---

### Data Advantage — 1/5 today · target 3/5
*Proprietary signal that compounds with usage. What do you see that OpenAI doesn't?*

**Score rationale:** We have no data today. The target is 3, not higher, because the advantage is narrow (high-stakes events, one audience) and a well-resourced competitor is one feature away from collecting similar data.

**Milestone (target earned when):** About 500 outcome-labeled events across 100+ men. That's the point where pooled data measurably improves a new user's first recommendation: he changes **35% fewer pieces** of his first outfit with pooled data than with a general-LLM baseline that has no pooled data. Pieces changed, not taps: "Change something" edits one piece at a time, so a shoe swap counts 1 and a full redo counts 4–5. The first-event hit rate (Great at the mirror and Right for the room) is reported alongside; it depends on the night as well as the outfit, so it supports the result but doesn't decide it.

**The compounding signal:** Outfits labeled with outcomes for high-stakes events. Each event pairs:
- what was recommended
- what he actually wore, verified by a pre-event mirror photo
- what he swapped, and why
- the event type, season and setting
- how it went: the two check-ins, how he felt at the mirror and whether it was right for the room the morning after

**Capture design:** Data is captured at the moments when he wants help, so logging isn't a chore.
- **"Check me":** he snaps what he has on and gets a reply about the clothes only ("You're good. Tuck the shirt.").
- **"Change something":** he can tap it any time before the event and edit the outfit piece by piece, each edit with an optional one-tap reason (Fit's off · Too formal · Too loud · Not comfortable · Just not me · You read the event wrong). Ellis revises the outfit live from pieces he's already photographed. He can also snap what he ends up wearing, so the record shows what actually went out the door.
- **Two check-ins, each asked when he knows the answer** (adopted Nov 14 from my client showing, n=1; not built yet):
  - **At the mirror: "How do you feel in it?"** Great · Fine · Not quite right, asked when he snaps the photo and before Ellis replies, so Ellis can't sway it. One skippable tap, and Ellis's reply starts at the same moment, so answering never adds wait. Recorded as its own signal.
  - **The morning after: "Was it right for the room?"** Right · Too dressed · Too casual, what only the event can tell him, plus the feeling question if he skipped the mirror. It brings back the half the feeling question can't answer (he can feel great and be underdressed), and it grades the read's dress-code estimate directly: a read of smart casual, then "Too dressed," is a measured miss on the edge.
  - Then Ellis shows what it learned, including the event ("Got it: the charcoal suit works for investor pitches"), with ✓ / Fix.
  - **His record (what Ellis reuses):** Great and Right leads next time at that kind of event. Great but Too dressed or Too casual is an event lesson ("same outfit, but that room wants a jacket"), not a winner. Fine stays in rotation but never leads. Not quite right is avoided at that kind of event.
  - **The scorecard (how Ellis is judged):** Ellis is designed to make men feel Great in an outfit that's right, so **a hit is Great at the mirror and Right for the room.** The target is **65% of events with both answers**. Everything else is a miss on the scorecard without being taken out of his closet. Two rules keep the number honest:
    - If he skipped the mirror and answers the feeling question the morning after, Great + Right still counts as a hit; otherwise men who skip the mirror could never score one. Each hit records which moment the feeling came from, and the two are reported separately, because a morning-after feeling is colored by how the night went.
    - Events where his closet falls short ("the closest you have") are left out of the 65% and shown as their own count, with their own hit rate. They rarely reach a hit, so the 65% is judged on events his closet could meet.
    - The hit rate is always shown next to the response rate, because men who felt off are more likely to skip a question.

    It's a target, not a kill rule. At 10 men it's directional; the cohort is the first real read.
  - **Across men:** lessons he confirms with ✓ feed the pooled house style, under the existing rule: adopted only when 3+ men show the same pattern.

**Named attacker (from partner challenge):** Stitch Fix. They already have millions of men using the service, plus their sizes and purchases. Asking "What did you wear this to, and how did it go?" is a feature they could add.

---

### Platform Exposure — 2/5 today · target 3/5
*Encroachment risk × pivot speed. If Apple/Google/OpenAI ships your hero feature native — then what?*

*Scale (instructor): 1 = pain · 5 = strong.*

**Hero feature:** Tell it about a high-stakes moment and snap the pieces you're considering, and it gives you one opinionated outfit from your own closet: what to wear, why it works, and what not to wear.

**Hook vs. moat:** The hero feature is the hook, and it's deliberately the part that can be copied. It only has to win the first try. Defensibility comes from the history it starts. The metric that matters is **time-to-moat**: we aim for his second recommendation to visibly use his history.

**Score rationale:** A generic version of the hero feature already works in ChatGPT today, so we're not at 1 only because a platform is unlikely to build for this niche specifically, and a solo product lead can pivot within a week. We reach 3 when the history, not the hook, is what men pick us for.

**Milestone (target earned when):** Both of these hold:
- A blind panel of men picks our recommendation over a plain assistant's at least 70% of the time.
- At least 40% of second and later events get a recommendation that visibly uses his history: what he changed before the event, what was Great and Right for the room, and lessons he confirmed with ✓. Who saw him in what joins once it's built (Horizon 3).

**Named attacker (from partner challenge):** OpenAI (ChatGPT). It already has vision, memory and shopping features, and it's an app he opens every day. Runner-up: Google, which owns his calendar and photos.

**The week it ships:**
1. **Day 1:** Run the offline separation check on our golden set against the new release to measure how much of a gap is left. A blind panel follows within the week, since raters take days to recruit.
2. **If men pick us 70% of the time or more:** Lead with what they can't copy: the pre-event check and "Change something" at the mirror, his record of what he wore and changed, who saw him in what (Horizon 3), and his lookbook.
3. **If men pick us but don't come back to our app,** because habit pulls them to ChatGPT: the free tier moves inside ChatGPT as a front door, never the record. Everything that builds his history stays in our own app (trigger and threshold revised in Module 2's 90-day plan).
4. **If men pick us under 40% of the time:** reposition or stop, as the kill criteria say. Moving the same advice into ChatGPT wouldn't fix advice that isn't better.
5. **Either way:** Show every current user what we already know about him ("6 events, 2 changes before the event, your best look"), so the cost of leaving is visible before anyone tries the alternative.

**If men pick us between 40% and 70% of the time:** Treat it as "not proven yet," not as a pass or a fail. Spend the week finding out why men chose the plain assistant, fix the biggest reason, and test again with the same cohort.

**Ongoing:** Run the offline separation check monthly on the golden set, so the gap is already known on the day a platform ships.

---

## Top Vulnerability
<!-- One line: what's the single biggest strategic risk? -->
**Users don't report back.** Every part of the Contextual Moat, all of the Data Advantage, and our only defense against platform encroachment are built from what he tells us after each recommendation. If reporting back is a chore, the product still looks like it works, but nothing compounds.

**Mitigation:** Reporting back is designed as the reward, not a form: the pre-event "Check me," the instant revision when he taps "Change something," and the record caught when he cares (how he feels at the mirror, whether it was right for the room), with what Ellis learned shown back to him.

**Kill rule:** Fewer than 50% of events get a check-in within 48 hours, counting every event, including men who declined notifications. Only the answer to the morning-after "Was it right for the room?" counts as a check-in; the ✓/Fix after it never counts on its own. The mirror's "How do you feel in it?", "Check me" and "Change something" happen while he's anxious and motivated, so they would flatter the number; the mirror's answer is reported alongside, never counted. The outcome tap is the hardest to get and the one the Data Advantage depends on.

## Confidence Level
<!-- H / M / L — how confident are you in this bet after the diagnostic? -->
**L.** Every axis scores 1–2 today, and there's no user evidence yet. The 10-man test (about Dec 7–20) raises it if a blind panel picks our advice over a plain assistant's **and** men report back, both at 70% or higher. It ends or repositions the bet if panel picks fall below 40% or report-back falls below 50%. Thresholds and sample design are in [prototype.md](prototype.md).
