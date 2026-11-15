# My AI Product Strategy

> A living strategy built across 6 sessions. Each module adds one component. By Module 6, this repo IS your strategy — version-controlled, board-ready, portable.

---

## Strategy at a Glance

| Component | Module | Status | Key Artifact |
|-----------|--------|--------|-------------|
| **The Bet** | M1 | [x] | `01-the-bet/` |
| **The Moat** | M2 | [x] | `02-the-moat/` |
| **The Margin** | M3 | [x] | `03-the-margin/` |
| **The Contract** | M4 | [x] | `04-the-contract/` |
| **The Guardrails** | M5 | [x] | `05-the-guardrails/` |
| **The Pitch** | M6 | [ ] | `06-the-pitch/` |

---

## The Bet (M1)

**What we're building, for whom, why now.**

- **Product:** Mercer + Taylor, an AI personal stylist that tells busy professional men (30s–40s, around $250K, in tech, finance and real estate) exactly what to wear from their own closet for the moments that matter.
- **AI Value Archetype:** Copilot, moving toward Orchestrator at Horizon 2.
- **Vulnerability Scores** (today → target; 1 = pain, 5 = strong): Moat 1 → 4 · Data 1 → 3 · Platform 2 → 3
- **Top Risk:** Users don't report back. The product still looks like it works, but nothing compounds.
- **Confidence:** L. No user evidence yet; set by the 10-man test (postponed; no new date yet).
- **Prototype:** built and shipped Nov 8, 2026, redesigned as "Ellis takes charge" after the builder's own n=1 (link pending).
- **Kill Criteria:** Under 40% blind panel picks against a plain assistant · under 50% of events answered "Was it right for the room?" within 48 hours · under 20% unprompted use by men who had another event within 14 days · under 4 of ~10 cohort men making a refundable founding-member payment at $11.99.

→ Details: [`01-the-bet/`](01-the-bet/)

---

## The Moat (M2)

**Why this won't get copied in 6 months.**

- **Data Flywheel Score:** 6/20 at launch → 9/20 by Dec 20 (Correction 3, Preference 3, Domain Context 2, Network 1).
- **Weakest Loop:** Network. It's a data network effect with diminishing returns, and larger platforms will always have more cold-start data. Fix: concede it and win the cold start on craft: the read and the asks (the edge: asking for the pieces he wouldn't think to mention), the follow-up and mirror check, and a house style guide as the floor. His closet is an input, not an edge. Craft wins the first try; what he tells us afterward wins the second.
- **Competitive Position:** Axes: advice that starts from zero ↔ knows what happened last time, × a person or a box you schedule ↔ there when he's getting dressed. ChatGPT and Match.com are on demand but start from zero; Stitch Fix and human stylists know more but need a box or an appointment. We target the empty corner: on demand and knowing what happened. Today we sit next to ChatGPT; we move toward "knows what happened" from his second event, if he reports back.
- **Encroachment Defense:** Win the first try on craft; win the moment of capture (the mirror check records what he wore before anyone asks); show him what we know, so leaving costs something; style him, don't sell to him (buy suggestions only for real gaps, no commissions). Concede pooled fit and purchase data to the larger players.
- **Vendor Portability:** Partial. Ready slipped from Nov 9; it comes when a backup provider passes our full eval, including clothes-only at 100%, and has an equivalent to the read's web search.

→ Details: [`02-the-moat/`](02-the-moat/)

---

## The Margin (M3)

**Will this make money or bleed it?**

- **Gross Margin (current):** Pre-revenue: the prototype is free. An event costs about 25¢ in model calls (measured on one real event, Nov 8, n=1).
- **Gross Margin (AI-adjusted):** About 84% on paying men alone at $11.99, on par with software. About 52% counting the free men they carry (planning case: 5% of men pay, free men use their event every other month), and about 19% in the worst case. The free tier, not the paying men, is the biggest margin risk. Floor: 50%, defended by cost cuts first, then the free tier's allowance, then price.
- **Pricing Model:** Hybrid on a free tier. Free: one event a month, with the full flow. Paid: $11.99 a month, with a fair-use cap around 20 events and a higher tier above it (never stopped before an event). The mirror check, the check-in, "Change something" and his history are never add-ons; outcome-based pricing is ruled out because it would corrupt his check-in answers.
- **Cascading Strategy:** Haiku for intake and, once it passes the eval, later reads with no public place to research; Sonnet for everything that decides the first try; when in doubt, Sonnet. Opus was dropped for now: the recommendation is already ~20 seconds, and Opus is slower. About 28% of calls move to Haiku but only about 10% of cost, because the recommendation never moves down.
- **Break-even at:** About 2% of men paying covers model and hosting costs in the planning case (about 4% in the worst case); about 5% holds the 50% floor. Today's fixed costs (~$30 a month) are covered by about 5 paying men.

→ Details: [`03-the-margin/`](03-the-margin/)

---

## The Contract (M4)

**Why users will trust a probabilistic system.**

- **Reliability Target:** Hard rules and clothes-only at 100% on the eval (one outfit, only his pieces, never his body); any failure blocks the change. Supporting: a 65% hit rate (Great at the mirror and Right for the room), blind panel picks at 70%, the asks finding the deciding piece 90%+ of the time (8 of 8 so far), and under 3 minutes from describing the event to the outfit.
- **Golden Dataset:** 13 rows, 3 adversarial (plus 2 edge cases). About 500 before production; about 300 clothes-only cases to show failures under 1%.
- **Confidence UX:** Tiered, and uncertainty is handled by asking, not hedging. Ellis asks when he can settle it, states its estimate once on the read screen when nobody can, and keeps the outfit screen clean ("The closest you have" is the only heading). At most 5 asks before the outfit, however unsure Ellis is. The 90% / 70% bands (the share of outfits kept with no "Change something") are targets to calibrate.
- **HITL Architecture:** Nothing waits on a human; the eval gates every change instead. During the test I read every outfit within a day; after it, a judge scans every answer within the hour. A zero-tolerance failure pauses only the broken step, he's always told, and his case becomes a golden row before it's unpaused.
- **Failure Mode Coverage:** Zero tolerance for a comment about his body, a piece he didn't send, a venue fact presented as found, a condition flaw the photo doesn't clearly show, or a description of anyone in review photos (rows 9, 12, 13, script and judge). Gaps: no history rows yet, and no rows for his own pick or a wrinkled piece. Red-team lesson: my tests kept measuring what any assistant already does well, so each one moved to the asks.

→ Details: [`04-the-contract/`](04-the-contract/)

---

## The Guardrails (M5)

**What breaks when this scales — and what compounds.**

- **Compounding System:** Three loops. His outcome record is the moat (what he wore, how he felt at the mirror, whether it was right for the room, what Ellis learned); pooled house style compounds only weakly and is conceded at 10 men; his wardrobe compounds but isn't a moat, since it moves both ways. The outcome record broke twice on my own events (no input on Nov 7; nowhere to put it on Nov 14), so the fix catches the record at the moment he cares: the mirror stays open, the check-ins are asked when he knows the answer, and what Ellis learned is shown back. Measured by report-back (70% target; under 50% fires).
- **Governance Posture:** Ellis may prepare; only he may act. Nothing waits on a human; the eval gates every change, five zero-tolerance cases each have their own off switch, and he's always told when something goes wrong. Ellis never changes its own rules. One home per kind of decision across the two chats (strategy here, build in the build repo).
- **Shadow AI Status:** 10 tools found, 10 triaged: 6 govern, 2 keep, 1 retire, 1 not ours. Highest risk: Claude Code holds the production database key today, fixed before the first man.
- **Agent Boundaries:** A fixed workflow, not agents: each step is one model call in a fixed order, and the model never chooses its next step, writes to the database or calls another step. One tool, web search (≤2, named public places only). He approves anything that leaves the app or uses his data beyond his outfit; I approve every prompt, model or tool change, only after the eval and a blind taste check pass.
- **Regulatory Exposure:** US-only study. Candidates to confirm with a lawyer before anything beyond it: state privacy law (California first), biometric rules (no facial features extracted), honest AI claims (Ellis is always disclosed as AI), adults only, and the model provider's training terms. EU AI Act: likely transparency duties only, already met. Switching off texts removed the US text-message rules.

→ Details: [`05-the-guardrails/`](05-the-guardrails/)

---

## The Pitch (M6)

**How you get this funded, shipped, and adopted.**

- **Horizon 1 (Now):**
- **Horizon 2 (Next):**
- **Horizon 3 (Bet):**
- **Board Narrative:** [1-sentence thesis]
- **Key Metric:**

→ Details: [`06-the-pitch/`](06-the-pitch/)
