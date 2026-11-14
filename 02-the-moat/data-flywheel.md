# Data Flywheel Map

> Score each loop 1-5. Your weakest loop is where competitors attack first.
> The four loops below are the M2 starting point - adapt if your product has 2 or 6 loops instead of 4.

## Flywheel Loops

| Loop | What It Measures | Score 1 | Score 5 | Score (Nov 1 → Dec 20) |
|------|------------------|---------|---------|-------|
| **Correction** | Do users fix AI outputs? Is that signal captured and reused? | No capture | Automated retraining | 2 → 3/5 |
| **Preference** | Does the product learn individual / team preferences over time? | Stateless | Deep personalization | 2 → 3/5 (4 longer term) |
| **Domain Context** | Does usage in one area improve quality in adjacent areas? | Siloed | Cross-domain transfer | 1 → 2/5 (3 longer term) |
| **Network** | Does each new user / team make the product better for everyone? | Isolated | Strong network effects | 1 → 1/5 (3 longer term) |

*Scores are for the design as built for the Nov 1 prototype → target by the end of the cohort (Dec 20).*

### Correction Loop - 2/5 at launch → 3/5 by Dec 20
**What you capture today:** Every change he makes before the event, per piece and with its reason, the outfit he actually wore, his post-event swaps, and blind-panel losses.

**How it compounds:** Corrections immediately change the revised outfit and his next recommendation. After the test, patterns that repeat across men become house style-guide rules and eval cases.
- **Proof:** the cohort shows fewer repeat corrections.
- **Deliberately no retraining:** the learning lives in assets we own (style guide, eval cases, his history), so it survives a model switch.

### Preference Loop - 2/5 at launch → 3/5 by Dec 20 (4/5 longer term)
**What you capture today:** How he felt in each outfit (Great · Fine · Not quite right), the lesson he confirmed or fixed, what he kept or changed, and who was at each event.

**How it compounds:** From his second event on, his history shapes the recommendation: what worked, what he rejected, and who has already seen him in what. A general-purpose assistant remembers what he *says* he likes; we learn what he actually wore.
- **Proof:** at least 40% of second-event recommendations visibly use his history.

### Domain Context Loop - 1/5 at launch → 2/5 by Dec 20 (3/5 longer term)
**What you capture today:** What he wore, what he rejected and why, and which buy suggestions he acted on.

**How it compounds:** What he wears informs what he should buy. From his second event on, buy suggestions draw on his history ("you've passed on two outfits because the jacket fit was off"). They're tagged so we can compare them with cold suggestions. A general-purpose assistant suggesting a purchase doesn't know the gaps in his closet.

**No commissions:** we suggest buys only for real gaps in his closet, and we earn nothing from them, so he never has to wonder whether we're styling him or selling to him.

**Transfer across event types:** What works for him at one kind of event informs the others. For example, his fit and color choices at investor meetings shape client dinners, and work style carries into dates. This is what makes the 10-event moat milestone enough: 10 events spread across about 5 event types is only about 2 per type, so without transfer we'd know almost nothing about him at any one kind of event.

### Network Loop - 1/5 at launch → 1/5 by Dec 20 (3/5 longer term)
**What you capture today:** What works by event type (outfits rated Great, lessons confirmed with ✓, outfits kept), with city and venue type.

**How it compounds:** After the test, patterns confirmed by at least 3 men that also pass the golden set become house style rules. That improves the first recommendation for the next new man.

**Why it stays at 1 through Dec 20:** It's a data network effect, not a true one, so pooled learning hits diminishing returns quickly. Patterns also fragment: with about 10 men spread across about 5 event types, plus city and venue, almost no combination reaches 3 men by Dec 20. A 2 would be a hoped-for score.

**Total Flywheel Score: 6/20 at launch → 9/20 by Dec 20**
**Weakest Loop:** Network. It's a data network effect with diminishing returns, and larger platforms will always have more cold-start data.

**Fix for weakest loop:** Concede it, and win the cold start on **craft**. Craft wins the first try; what he tells us afterward wins the second. We don't claim craft is the moat.

1. **The read and the asks: the edge.** Ellis asks for the pieces and facts a man wouldn't think to mention. Eight written, checkable rules (R1–R8) govern how it reads the event and what it asks for:
   - **The read:** it researches the place only when he names it, and says plainly what it found. It estimates the dress code and checks the weather.
   - **The asks:** the pieces that set the outfit come first (trousers and shoes), and it names pieces from his wardrobe before asking generically.
   - **The limit:** every ask must make this decision better or the next one easier; if neither, it doesn't ask. That keeps the asks from turning into a questionnaire.
   - *Evidence (n=1, Nov 10, my own event, my judgment, not blind):* the missing blazer and overcoat decided the result. With them supplied, Ellis's outfit and a plain assistant's matched. The read's eval now checks this across cases: whether the asks surface the deciding piece (see the kill switch's Eval): 8 of 8 on small wardrobes so far.
2. **The follow-up and the mirror check: catching what's missing or wrong before he leaves.** The follow-up spotted the missing overcoat, and the mirror check looks at him dressed. The panel judges outfits, not him dressed, so the mirror check's value has to show up in the check-in (the Great rate), not in the panel.
3. **The house style guide: the floor.** It holds for every man: one outfit, only his pieces, no hedging, never a comment on his body, name a shortfall instead of pretending, and no purchase unless there's a real gap and time to get it. The eval checks most of it automatically. It didn't separate Ellis from a plain assistant on n=1; its value shows across many men.

**What isn't craft:**
- **His closet is an input, not an edge.** His own assistant had his closet too, and won with it on my first real event. The edge is knowing which pieces to ask for.
- **"One opinionated pick" is cut.** Given the same pieces, the plain assistant also gave one outfit, with the same reasons.

The H1 blind panel tests this whole flow against what his own assistant would have had (see Module 1). Pooled data only sharpens it. Craft can be copied, so it only has to win the first try. His history keeps him after that (the Correction and Preference loops).

---

## Encroachment Threat Assessment

### 1. Platform Encroachment
**Attacker:** OpenAI (ChatGPT)

**Vector:** Closing the outcome loop. The hook can already be copied: vision and memory answer "what should I wear?" today. The attack that hurts is ChatGPT following up after the event (proactive check-ins tied to his calendar) and storing what he wore in memory. He won't report to two places, so whoever asks first gets the outcome. This attacks our critical assumption (H6), not just the hero feature.

**Time-to-threat:** About 90 days, and we plan against this. A generic post-event follow-up ("How did the pitch go?") is already possible through proactive, calendar-aware features like Pulse, and memory links it to any outfit advice he asked for. A style-specific outcome loop is 6–12 months away at best, because it's a niche product decision.

**% of value at risk:** About 60% if it ships (estimate): the free tier, plus our claim to exclusive outcome labels for men who use ChatGPT daily. Histories already built with us don't move.

### 2. Vertical Competitor
**Attacker:** Stitch Fix

**Vector:** Already in the vertical, with an app, AI outfit images of the client (Vision), a conversational AI style assistant, human stylists, and years of keep/return and fit data. For a long-time client, it already knows many of his pieces one by one. The attack: style those pieces for his events and show him his looks, skipping the closet we build one event at a time.

**Time-to-threat:** Partly now. Event styling from pieces he owns is 3–6 months away if they choose to build it, but it only pays for them if it ends in a sale.

**% of value at risk:** About 20% (estimate), concentrated in men who are already clients, plus our buy suggestions and fit data. Not the record of what he wore and where, and not men who never wanted a box.

### 3. Adjacent Expansion
**Attacker:** Match Group, led by Match.com (also Hinge, Tinder)

**Vector:** Match.com first. It skews older and is closest to our customer: men in their 40s re-entering dating, often after divorce. Dating apps own the dating trigger. They know when he has a date, see how he dresses in his photos, and know which looks get responses, which is outcome data we'll never have. Hinge has said it's building an AI dating coach, and its Prompt Feedback already critiques profiles. "What to wear Friday" is a short step from photo feedback.

**Time-to-threat:** About 6–12 months, and we plan against this, through Hinge for the younger end of our dating men. About 9–18 months through Match.com, where overlap with our 40s divorced men is highest but Match Group invests later. Overtone, Match Group's AI-first dating venture, is a wildcard on either timeline.

**% of value at risk:** About 15–20%: one of three triggers, first dates only. Leading with Match.com doesn't change the number: the first estimate overstated Hinge's reach and understated Match.com's overlap with our dating men, and those roughly cancel out.

---

## 90-Day Encroachment Plan

*Your partner played the Big Tech attacker. What was their plan to kill you?*

*No class partner for this one. Claude played the attacker.*

**Attacker:** OpenAI (ChatGPT)

**Attack vector (target the weakest loop):** Win the first try with scale, which is the loop we conceded (Network), and then take the outcome loop, so his history never builds up with Mercer + Taylor. We don't need to beat your stylist. We just need to ask him "how did it go?" first.

**Weeks 1-4 - what they ship:** "Get Ready," a free style mode in ChatGPT.
- He snaps the pieces he's considering and gets one outfit with reasons. It's the same shape as your hero feature, backed by far more cold-start data.
- Calendar-aware prompts in the proactive daily briefing: "Investor dinner Thursday. Want me to pick what you'll wear?"
- Memory saves the outfit. Shopping and checkout already sit inside ChatGPT, so every closet gap becomes a purchase we earn on. Unlike Stitch Fix, our business model *rewards* styling what he owns, because it keeps him engaged.

**Weeks 5-8 - how they poach users:** Close the outcome loop in the app he already opens every morning.
- The morning after the event, a card in his daily briefing asks: "How did the investor dinner go? Wear the navy suit again?" One tap, and memory files it.
- We target the men most likely to be yours: heavy daily ChatGPT users in tech and finance, with calendars full of high-stakes events.
- He doesn't decide to switch. He just answers the question that arrived first. Your "How did you feel in it?" shows up an hour later, after he's already answered us.

**Weeks 9-12 - why users don't come back:** His new history builds up with us, not you.
- His Mercer + Taylor record stalls around event 3. "Who saw him in what" goes stale, because you no longer see what he wears.
- Your second recommendation can't visibly use his history, so the 40% time-to-moat milestone fails.
- Your report-back rate falls below 50%, and **your own kill rule fires.** You'll read it as a product failure, not an attack. The men didn't dislike Mercer + Taylor; they just reported somewhere else first.

**Your defense:**

**1. Win the race.**
- **Ask first by asking before the event.** The pre-event check records what he actually wore before anyone else asks. A general assistant knows what it *recommended*; we verified at the mirror what actually went out the door, swaps included.
- **He chooses the check-in time at the mirror** (tonight or tomorrow morning), so the question is welcome and usually arrives before any morning briefing.
- **His answer is worth more when he gives it to us.** It visibly changes his next outfit in a way only a structured record can ("These investors have seen the navy suit twice. Here's a look they haven't seen, built from pieces that have worked on you before.") and saves to his lookbook. His answer to a general assistant goes into memory; his answer to us shows up at his next event.

**2. What can't move.**
- **What he loses:**
  - who has seen him in what, so his next outfit can't avoid a repeat in front of the same people;
  - rules learned from his rejections, which he never had to say ("You've tapped 'Too loud' three times on patterned shirts but never on patterned ties"), so he can't repeat them to another tool;
  - his lookbook of outfits that worked, laid out from his own pieces.

  His history doesn't move to ChatGPT, and it stops growing with us.
- **How he feels it before it happens:** We show him what we know.
  - The post-event question names the stake: "Wear it again? I'll make sure the investors don't see it twice."
  - His next recommendation shows the history at work ("You wore the navy suit with these investors on Oct 14; here's a variation") and says honestly when something is missing.
  - Later, a "What I know about you" card makes the record visible and his.

**3. Detect it early: attack or failure?**
- **Signal 1: what he does before the event.** If he keeps starting new events, opening his recommendations and using the mirror check while his post-event answers fall, he still values us; we're losing his answer, not him. If everything falls, he stopped caring.
- **Signal 2: the shape of the drop.** An attack shows up as a sudden drop by calendar date across many men at once, lining up with a competitor's release. A chore shows up as a gradual decline, man by man and event by event.
- **Signal 3: ask at his next event.** "How did the investor dinner go?" If he answers then, the problem is the timing of the post-event moment, not him.
- **Signal 4: ask directly.** At his next event or in a monthly check-in, without judgment: "Do you get style advice anywhere else right now?" (ChatGPT · a friend or partner · a store · No). This is what measures "men confirm they answered elsewhere."
- **Watch for confounders:** check any sudden drop against the season and event volume before blaming a competitor release. The Nov 30–Dec 20 cohort runs through holiday party season, and with about 10 men one quiet week can look like a pattern.
- **The rule, set in advance:** If fewer than half of events get a post-event answer, our plan says the moat has failed. We treat it as an attack only if all three hold: what he does before events holds steady, the drop lines up with a dated competitor release, and men confirm they answered elsewhere. Otherwise, the failure rule stands. Either way the moat lost; the signal tells us what to fix.

**4. The fallback: ChatGPT as a front door, never the record.** The Module 1 fallback needs two changes.
- **A new trigger.** It used to fire if men picked us half the time or less. But that test runs inside our app, so losing it means our advice wasn't better, and moving the same advice into ChatGPT doesn't fix that. The new trigger: men pick our recommendation but don't come back to our app, because habit pulls them to ChatGPT. That's a distribution problem, and meeting them inside ChatGPT answers it. If men don't pick us, we reposition or stop, as before.
- **ChatGPT is a front door, never the record.** Inside ChatGPT, he gets one free outfit from his own pieces, the part that can be copied. Everything that builds his history stays in our own app and our own system: the mirror check that records what he actually wore, the post-event question (sent as a notification or email, because apps inside ChatGPT can't ask first), his lookbook, and who has seen him in what. Saving anything requires his own account with us. OpenAI sees the first recommendation, but never what he wore or how he felt in it.
- **The number that decides it:** the share of men who move from ChatGPT to our app. Of the men who get a free outfit in ChatGPT for a real event, how many link a Mercer + Taylor account and use the mirror check or answer the post-event question in our app within 14 days:
  - *30% or more:* the front door works.
  - *15–30%, not proven yet:* make one fix to the handoff and measure again.
  - *Under 15%:* the ChatGPT app feeds OpenAI more than it feeds us, so we shut it down.
