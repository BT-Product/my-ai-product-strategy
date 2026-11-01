# The Prototype Bet

## What I Built
<!-- One sentence: what does this prototype demonstrate? -->
**Not built yet; live by Sun Nov 1, 2026.** A single-flow mobile web prototype that tests three things: whether one opinionated outfit from a man's own closet, plus a clothes-only check at the mirror before he leaves, beats a plain AI assistant, and whether he reports back after the event.

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
All of these were set before any data came in. They're tested in the **Nov 2–15 prototype test** with about 10 men.

**Sample design:** Each man does the blind side-by-side on **three scenarios**, for about 30 comparisons instead of 10:
- **His real event.** This is the primary signal, because he goes on to follow that pick.
- **Two golden cases** built from his own photographed pieces, as supporting signal.

Each pick is reported both per comparison and per man. If the real-event picks and the golden-case picks disagree, the real-event picks win. At this sample size, every result is **directional**: 70% or more means *not falsified*, not *proven*.

1. **It doesn't beat a plain assistant.** Men choose our recommendation over a plain assistant's in the blind side-by-side:
   - *70% or more:* passes (not falsified).
   - *40–70%, not proven yet:* diagnose why, fix the biggest reason, and retest in the cohort. If it's still short of 70%, reposition.
   - *Under 40%:* stop or reposition.
2. **He doesn't report back.** Fewer than 50% of events get the post-event "Wear again?" tap within 48 hours, with at most one reminder.
   - *50–70%:* redesign the capture (for example, ask at his next event) and retest.
3. **He won't pay** (cohort, Nov 30–Dec 20). Fewer men commit to the paid tier at a real price than the threshold set in Module 3.
4. **He leaves after one event** (cohort, Nov 30–Dec 20). This is the share of men who complete a first event, have another event coming up within the cohort window, and use Mercer + Taylor for it without being prompted:
   - *40% or more:* passes.
   - *20–40%:* not proven.
   - *Under 20%:* the risk that he leaves after one event is confirmed, and calendar-driven prep moves up the roadmap.

   The base is every man who completed a first event, not only those still active, to avoid survivorship bias. The 20% is a placeholder until the first test shows how many men have a second event at all.
