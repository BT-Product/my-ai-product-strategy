# The Prototype Bet

## What I Built
<!-- One sentence: what does this prototype demonstrate? -->
**Built; shipped and checked on my phone Nov 8, 2026.** A single-flow mobile web prototype that tests whether one opinionated outfit from a man's own closet, plus a clothes-only check at the mirror before he leaves, beats a plain AI assistant, and whether he reports back after the event.

**The first-event flow ("Ellis takes charge"):**
1. He describes the event.
2. **Ellis reads the event.** If it's a named public venue or event, Ellis researches it (at most two web searches) and says what the event calls for. It never researches a person, a private address or a private event.
3. **Ellis asks for specific pieces,** like a stylist going through his closet: three or four asks, essentials first ("Show me your trousers: charcoal or navy wool if you have them"). It names a piece from his wardrobe when one fits, and asks for a photo only of a piece it hasn't seen.
4. **One outfit,** then the try-on and the mirror check (the mirror check and "Change something" aren't built yet).

A leave-out ("not the brown loafers") appears only when he showed a real mistake, at most one. The pre-built backup outfit is retired.

**Why it changed (n=1, the builder):** For two real events of my own, I asked Claude.ai instead of Ellis. It already knew my closet, I didn't know what to photograph, and photographing took too long. The first version also made a man's first experience a test, with Ellis hidden behind a blind comparison. So the flow was redesigned before any man saw it, and the 10-man test was postponed.

**Prior evidence:** An earlier version, built in Lovable from July to September 2026, showed that turning closet photos into AI outfits works end to end. That proved feasibility only (n=1).

## Tool Used
<!-- v0 / Cursor / Lovable / other -->
**Claude Code**, with TanStack Start, Supabase and the Claude API. Every model call sits behind one interface, so the AI vendor can be swapped.

The earlier feasibility version was built in **Lovable**.

## Prototype Link
<!-- Paste the shareable URL -->
Pending: live by Sun Nov 1, 2026.

## AI Value Archetype
<!-- Automator / Copilot / Oracle / Creator / Orchestrator -->
**Copilot.** He makes the final call. The AI gives him a confident recommendation with reasons, checks him at the mirror, and rescues him when an outfit doesn't feel right.

**Path:** It moves toward **Orchestrator** at Horizon 2, when it prepares him for events from his calendar without being asked.

## The Bet in One Sentence
<!-- What you're building, for whom, why now -->
An AI personal stylist that tells busy professional men who've never hired a stylist exactly what to wear from their own closet for the moments that matter. Vision models can now see his actual clothes, which brings a stylist's judgment to a fraction of the $100–500 an hour a human charges, without the awkwardness.

## Kill Criteria
<!-- When would you stop? What evidence would kill this bet? -->
All of these were set before any data came in. They're tested in the **10-man prototype test**, postponed from Nov 2–15; no new date yet.

**How H1 is measured: a blind panel, not a comparison inside his flow.**
- **Pairs:** on each man's first event, a plain assistant's answer is generated, stored, and never shown to him. He only ever sees Ellis.
  - **What the plain assistant gets:** what his own assistant would have had: his event description, his own pick if he named one, and his wardrobe only if his assistant already holds it. It runs at the same effort setting, with web search, like the ChatGPT he'd actually use.
  - **What it doesn't get:** the pieces Ellis asked for. On my own n=1, given the same pieces, both picked the same outfit, so asking for the right pieces is where Ellis's edge is. Handing those pieces over would test only the styling.
  - **Fallback:** if he names no pick and his assistant doesn't hold his wardrobe, the plain assistant would have no pieces at all and would lose too easily. Then it gets the same pieces Ellis collected. That's the cautious case, because it makes Ellis's job harder. Those pairs are reported separately, so an easy win can't inflate the result.
- **Raters:** men in the target group, never rating their own case. At least 3 raters per pair, about 5 pairs each, in the same plain format.
- **Sample:** about 10 pairs × 3 raters, about 30 picks, reported per pair and per rater.
- **Behavioral check:** the follow-up call asks, "Did you also ask another assistant for this event? Which did you go with?"
- **Offline:** a separation check on the golden set (built; not yet run, because 11 closet photos are missing).
- **Trade-off accepted:** the panel compares advice, not whole experiences, and a rater doesn't own the closet. H2 (did he wear it) stays the behavioral half.

At this sample size, every result is **directional**: 70% or more means *not falsified*, not *proven*.

1. **It doesn't beat a plain assistant.** The blind panel picks our recommendation over a plain assistant's:
   - *70% or more:* passes (not falsified).
   - *40–70%, not proven yet:* diagnose why, fix the biggest reason, and retest in the cohort. If it's still short of 70%, reposition.
   - *Under 40%:* stop or reposition.
2. **He doesn't report back.** Fewer than 50% of events get an answer to the post-event "How did you feel in it?" within 48 hours, with at most one reminder.
   - *What counts:* only that answer. The ✓/Fix on what Ellis learned comes right after it, so it never counts on its own.
   - *Which events:* all of them, including men who declined notifications. Declining is what this rule exists to catch.
   - *50–70%:* redesign the capture (for example, ask at his next event) and retest.
3. **He won't pay** (cohort, Nov 30–Dec 20). Out of about 10 cohort men asked at the end of the cohort, how many commit to the paid tier at $11.99 a month:
   - *7 or more:* passes (not falsified).
   - *4–6:* not proven.
   - *3 or fewer:* stop or reposition.
   - **What counts as committing: a founding-member payment.** At the end of the cohort, each man gets a one-time payment link for $11.99, his first paid month, starting when the polished version launches. No auto-renew and no card stored. Full refund on request any time before launch, and a refund takes his commitment off the count. "I'd pay for this" on the call doesn't count; men are polite to founders.
   - **What a pass means:** cohort men likely come from my network and are friendlier than the market, so 7 of 10 means "worth building," not "the market will pay."
   - *Price questions at the follow-up call:* "At what monthly price would this feel like a bargain?" and "At what price would you stop considering it?" Ten answers won't set the price, but they show whether $11.99 sits near the floor or the ceiling.
4. **He leaves after one event** (cohort, Nov 30–Dec 20). Of the men who completed a first event **and had another event to dress for within 14 days**, the share who used Mercer + Taylor for it without being prompted:
   - *40% or more:* passes.
   - *20–40%:* not proven.
   - *Under 20%:* the risk that he leaves after one event is confirmed, and calendar-driven prep moves up the roadmap.

   **Why this base:** a man with nothing to dress for isn't a lost customer, so counting him would mix "didn't need us" with "didn't want us." Whether he had another event is asked at the follow-up call, held 14 days after his first event, so every man gets the full 14 days. If that falls after Dec 20, he keeps access until the call. The call asks "Did you have anything to dress for in the past two weeks?" before any question about Ellis, so a man who didn't come back has no reason to say he had nothing to dress for. The base still includes men who went quiet or cancelled, as long as they had an event, to avoid survivorship bias.

   **Reported alongside, never deciding:** the same share across every man who completed a first event. That's how often men come back at all, the event frequency that the moat milestone (3.3 events a month) and Module 3 pricing depend on.

   **The bars are looser than they look.** 20% and 40% were first set on every man. On a base of men who all had a reason to come back, the same bars are easier to clear. They're kept, set before any data. At about 10 men, this base may be 3–6 men, so the result is directional only.
