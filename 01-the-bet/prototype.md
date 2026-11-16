# The Prototype Bet

## What I Built
<!-- One sentence: what does this prototype demonstrate? -->
**Built; shipped and checked on my phone Nov 8, 2026.** A single-flow mobile web prototype that tests whether Ellis's flow (asking for the right pieces, one outfit from his own closet, and a clothes-only check at the mirror before he leaves) beats what his own AI assistant would give him, and whether he reports back after the event.

**The first-event flow ("Ellis takes charge"):**
1. He describes the event.
2. **Ellis reads the event.** If it's a named public venue or event, Ellis researches it (at most two web searches) and says what the event calls for. It never researches a person, a private address or a private event.
3. **Ellis asks for specific pieces,** like a stylist going through his closet: three or four asks, essentials first ("Show me your trousers: charcoal or navy wool if you have them"). It names a piece from his wardrobe when one fits, and asks for a photo only of a piece it hasn't seen.
4. **One outfit,** then the try-on and the mirror check (the mirror check is built; "Change something" isn't yet).

A leave-out ("not the brown loafers") appears only when he showed a real mistake, at most one. The pre-built backup outfit is retired.

**Why it changed (n=1, the builder):** For two real events of my own, I asked Claude.ai instead of Ellis. It already knew my closet, I didn't know what to photograph, and photographing took too long. The first version also made a man's first experience a test, with Ellis hidden behind a blind comparison. So the flow was redesigned before any man saw it, and the 10-man test was postponed.

**Prior evidence:** An earlier version, built in Lovable from July to September 2026, showed that turning closet photos into AI outfits works end to end. That proved feasibility only (n=1).

## Tool Used
<!-- v0 / Cursor / Lovable / other -->
**Claude Code**, with TanStack Start, Supabase and the Claude API. Every model call sits behind one interface, so the AI vendor can be swapped.

The earlier feasibility version was built in **Lovable**.

## Prototype Link
<!-- Paste the shareable URL -->
Built and shipped Nov 8, 2026 (checked on my phone). Link pending.

## AI Value Archetype
<!-- Automator / Copilot / Oracle / Creator / Orchestrator -->
**Copilot.** He makes the final call. The AI gives him a confident recommendation with reasons, checks him at the mirror, and rescues him when an outfit doesn't feel right.

**Path:** It moves toward **Orchestrator** at Horizon 2, when it prepares him for events from his calendar without being asked.

## The Bet in One Sentence
<!-- What you're building, for whom, why now -->
An AI personal stylist that tells busy professional men who've never hired a stylist exactly what to wear from their own closet for the moments that matter. Vision models can now see his actual clothes, which brings a stylist's judgment to a fraction of the $100–500 an hour a human charges, without the awkwardness.

## Kill Criteria
<!-- When would you stop? What evidence would kill this bet? -->
All of these were set before any data came in. They're tested in the **10-man prototype test**, postponed from Nov 2–15 to **about Dec 7–20** (decided Nov 15), after the build finishes about Dec 4, with a midpoint review about Dec 13–14. The cohort (~20 men: test men who want to continue, plus referrals) starts on a gate, not a date: Jan 4 at the earliest, Jan 11 if the test turns up problems. Holiday-party season gives real events but skews them to one type, so results are reported by event type.

**How H1 is measured: a blind panel, not a comparison inside his flow.**
- **Pairs:** on each man's first event, a plain assistant's answer is generated, stored, and never shown to him. He only ever sees Ellis.
  - **What the plain assistant gets:** what his own assistant would have had: his event description, his own pick if he named one, and his wardrobe only if his assistant already holds it. It runs at the same effort setting, with web search, like the ChatGPT he'd actually use.
  - **What it doesn't get:** the pieces Ellis asked for. On my own n=1, given the same pieces, both picked the same outfit, so asking for the right pieces is where Ellis's edge is. Handing those pieces over would test only the styling.
  - **Fallback:** if he names no pick and his assistant doesn't hold his wardrobe, the plain assistant would have no pieces at all and would lose too easily. Then it gets the same pieces Ellis collected. That's the cautious case, because it makes Ellis's job harder. Those pairs are reported separately, so an easy win can't inflate the result.
  - **Keeping fallback pairs rare:** few men keep their closet in an assistant, so without a pick most pairs would be fallback pairs, which test only styling, the part the Nov 10 n=1 says is thin. That risks a false "not proven."
    - "Do you know what you want to wear?" is built before the test. For most men, their own pick is the realistic plain-assistant input, so every man who names one gives a standard pair.
    - The wardrobe import is offered only to men who answer yes to a setup question ("Does your AI assistant already know your clothes?"), meaning they already keep their closet in an assistant, never created for the test, and only after it passes messy real pastes (a long memory dump, a paste with names, an instruction buried in the middle).
    - Results report the split, standard vs fallback pairs. If fewer than half of pairs are standard, the headline reads "H1 tested styling only" (threshold set before any data).
    - *Noted:* standard pairs will come mostly from men who already had a plan, so they mainly test refining his pick; undecided men, where the asks matter most, will mostly be fallback pairs.
    - *Status:* decided, not built. The app and the eval still give the plain assistant the pieces Ellis collected.
- **Raters:** men in the target group, never rating their own case. At least 3 raters per pair, about 5 pairs each, in the same plain format.
- **Sample:** about 10 pairs × 3 raters. **A pair goes to whichever answer most of its raters pick,** and the 70% / 40% thresholds apply to pairs. Per-rater picks are reported as support, since picks on one pair aren't independent: about 10 data points, not 30.
- **Behavioral check:** the follow-up call asks, "Did you also ask another assistant for this event? Which did you go with?"
- **Offline:** a separation check on the golden set (built; not yet run, because 11 closet photos are missing). It runs from the event description, like the panel, so it tests the asks as well as the styling.
- **Trade-off accepted:** the panel compares advice, not whole experiences, and a rater doesn't own the closet. H2 (did he wear it) stays the behavioral half.

At this sample size, every result is **directional**: 70% or more means *not falsified*, not *proven*.

1. **It doesn't beat a plain assistant.** The blind panel picks our recommendation over a plain assistant's:
   - *70% or more:* passes (not falsified).
   - *40–70%, not proven yet:* diagnose why, fix the biggest reason, and retest in the cohort. If it's still short of 70%, reposition.
   - *Under 40%:* stop or reposition.
2. **He doesn't report back.** Fewer than 50% of events get an answer to the morning-after "Was it right for the room?" within 48 hours, with at most one reminder (target 70%).
   - *What counts:* only that answer. The mirror's "How do you feel in it?" comes while he's anxious and motivated, so it's reported alongside, never counted. The ✓/Fix on what Ellis learned comes right after it, so it never counts on its own.
   - *Which events:* all of them, including men who declined notifications. Declining is what this rule exists to catch.
   - *Reported by channel:* every message records how it reached him (notification, email, or a text I send by hand when both miss), so a delivery gap isn't read as Ellis failing. The threshold doesn't change.
   - *50–70%:* redesign the capture (for example, ask at his next event) and retest.
3. **He won't pay** (cohort, ~20 men, from Jan 4 at the earliest). The share of cohort men, asked at the end of the cohort, who commit to the paid tier at $11.99 a month (restated Nov 15 as shares, since the bars were first written for about 10 men):
   - *70% or more (about 14 of 20):* passes (not falsified).
   - *40–60% (about 8–12):* not proven.
   - *30% or less (about 6 or fewer):* stop or reposition.
   - **What counts as committing: a founding-member payment.** At the end of the cohort, each man gets a one-time payment link for $11.99, his first paid month, starting when the polished version launches. No auto-renew and no card stored. Full refund on request any time before launch, and a refund takes his commitment off the count. "I'd pay for this" on the call doesn't count; men are polite to the person who built it.
   - **What a pass means:** cohort men likely come from my network and are friendlier than the market, and many are test men who chose to continue, so a 70% pass means "worth building," not "the market will pay."
   - *Price questions at the follow-up call:* "At what monthly price would this feel like a bargain?" and "At what price would you stop considering it?" Ten answers won't set the price, but they show whether $11.99 sits near the floor or the ceiling.
4. **He leaves after one event** (cohort, from Jan 4 at the earliest). Of the men who completed a first event **and had another event to dress for within 14 days**, the share who used Mercer + Taylor for it without being prompted:
   - *40% or more:* passes.
   - *20–40%:* not proven.
   - *Under 20%:* the risk that he leaves after one event is confirmed, and calendar-driven prep moves up the roadmap.

   **Outreach doesn't count (decided Nov 15).** In the cohort, Ellis reaches out first only for the events he listed at recruitment (sub-bet S6). "Comes back" counts only second events he starts himself, outside that list; outreach-started events are reported separately, against outreach's own target. _Why:_ outreach only reaches events Ellis knows about, so an unprompted return is the test of whether Ellis is his default stylist rather than his own assistant; returns that come only after a nudge are fragile; and without the split there's no telling whether outreach added events or only got there first. Directional at about 20 men.

   **Why this base:** a man with nothing to dress for isn't a lost customer, so counting him would mix "didn't need us" with "didn't want us." Whether he had another event is asked at the follow-up call, held 14 days after his first event, so every man gets the full 14 days. If that falls after the cohort ends, he keeps access until the call. The call asks "Did you have anything to dress for in the past two weeks?" before any question about Ellis, so a man who didn't come back has no reason to say he had nothing to dress for. The base still includes men who went quiet or cancelled, as long as they had an event, to avoid survivorship bias.

   **Reported alongside, never deciding:** the same share across every man who completed a first event. That's how often men come back at all, the event frequency that the moat milestone (3.3 events a month) and Module 3 pricing depend on.

   **The bars are looser than they look.** 20% and 40% were first set on every man. On a base of men who all had a reason to come back, the same bars are easier to clear. They're kept, set before any data. At about 20 cohort men in a quiet January, this base may be under 10 men, so the result is directional only.
