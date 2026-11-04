# Kill Switch Audit

## Vendor Dependency Assessment

| Dimension | Current State | Risk Level | 48-Hour Action |
|-----------|--------------|------------|---------------|
| **Provider** | Anthropic only (Sonnet 5.5 + Haiku 5.5); never run on another provider | H today → M after the build | Pause new first events, re-run stored cases on OpenAI and Google, resume on the best one that passes |
| **Abstraction** | One provider-neutral interface (Vercel AI SDK); prompts as data; model per task in config | M today → L after the build | Change one setting (provider and model per task); add a provider version of any prompt the stored cases show underperforming |
| **Routing** | Model per task (Haiku 5.5: intake, event intelligence; Sonnet 5.5: recommendation, vision, mirror check); nothing automatic, so a failure shows an error | H today → L at the mirror, M overall after the build | In the moment, not 48 hours. Mirror: saved checklist shown at once; live check from Sonnet ~12s → Haiku ~8s → top-ranked backup provider; photo always saved. Rescue: pre-generated backup outfit. Recommendation: retry once, then ask him to retry |
| **Eval** | Zero cases today; I'm the grader, by eye. Planned: 10 cases by Nov 3, about 30 by Nov 15 | H today → M by Nov 15 → L at 50+ cases and a second taste grader | Run the full set in about an hour: a script for hard rules, a judge model (never the one tested) for dress code and clothes-only, me blind for taste. New first events stay paused until it passes |

### Provider
**Current state:** Anthropic only.
- **Claude Sonnet 5.5:** the recommendation, vision and the mirror check.
- **Claude Haiku 5.5:** intake and event intelligence.

Never run on another provider.

**Risk: H today → M after the build.** Vision is a commodity. What's untested is whether another model keeps one confident pick in our house style.

**Prep to move H → M (during the Nov 2–15 test):** Run the 5 stored cases once on OpenAI and Google against the five checks below, and record which backup ranks first. Until that's done, risk stays H, and the 48-hour action starts with step 2, because there's no ranking yet.

**48-hour action:**
1. Pause new first events, and switch to the backup that ranked first in an earlier one-time comparison (OpenAI and Google, on 5 stored test cases).
2. Re-run the stored cases on both backups in parallel against five checks:
   - one outfit;
   - only his pieces;
   - a reason-backed "no";
   - the right dress code;
   - clothes-only at the mirror.
3. Resume on the best one that passes, with its results tagged and reported separately. Hold only if neither passes.

### Abstraction
**Current state:** One provider-neutral interface (Vercel AI SDK). Prompts are stored as data, and the model for each task is set in config.

The earlier Lovable build called Anthropic directly, with prompts and the model hard-coded in six functions.

**Risk: M today → L after the build,** if all of these hold:
- no direct provider calls;
- prompts stored as data, with an optional version per provider, kept separate from a provider-neutral house style guide;
- responses read through a validated schema;
- photos sent in one normalized format;
- no Anthropic-only features in the core flow (prompt caching, if used, sits in one place and is optional).

**Prep to move M → L (during the Nov 2–15 test):** Run the backup comparison from the Provider row through our own app, by changing the provider setting, not by pasting prompts into ChatGPT or Gemini. If the 5 stored cases run cleanly, every condition above is verified, and the backups' quality is tested at the same time.

**48-hour action:** Change one setting: the provider and model for each task. No code changes. If the stored test cases show a prompt underperforms on the new model, add a provider version of that prompt (about five prompts; data edits, not code).

This works only if the backups are ready ahead of time. Both backup providers' packages are installed, their API keys are set, and their accounts are funded with rate limits high enough for live traffic. That's set up during the test, when the comparison needs the keys anyway, and kept ready afterward.

### Routing
**Current state:** A model per task:
- **Claude Haiku 5.5:** intake and event intelligence.
- **Claude Sonnet 5.5:** the recommendation, vision and the mirror check.

Nothing is automatic: a slow or failed call shows an error.

**Risk: H today → after the build, L at the mirror and M overall.**

**In the moment** (this row works in seconds, not 48 hours):
- **Mirror check:** he sees the mirror checklist saved with his recommendation ("Tuck the shirt; no watch with the navy suit") right away, as the loading screen, so he never stares at a spinner. The live check replaces it when it arrives:
  1. about 12 seconds on Sonnet;
  2. then about 8 on Haiku, but only if Haiku passed the clothes-only test cases. Haiku covers a slow or overloaded Sonnet, not an Anthropic outage, because it goes down with Anthropic;
  3. then the top-ranked backup provider, once it passes the clothes-only check in the backup comparison. This covers an Anthropic outage.

  If none of them reply, the checklist stays. His photo is saved either way, so we never lose what he wore.
- **Rescue ("This isn't me"):** falls back to a backup outfit generated along with the original recommendation.
- **Recommendation:** retries once, then asks him to try again. A right answer late beats a worse one the night before, and a backup's outfit would spoil the side-by-side with the plain assistant.
  - *Exception:* if the event starts within two hours, a backup answer is allowed. It's tagged and excluded from the side-by-side.

### Eval
**Current state:** Zero cases today, and the grader would be me, by eye.

**Planned:**
- **By Nov 3:** 5 stored cases from my own closet and 5 clothes-only cases.
- **By Nov 15:** about 30 cases: each man's real event plus 2 cases from his pieces, and every rejection at the mirror.

**Risk: H today → M by Nov 15 → L** once there are 50+ cases and a second taste grader.

**48-hour action:** Run the full set in about an hour. Three graders, each for what it can judge:
- **A script** checks the hard rules: one outfit, only his pieces, a reason-backed "no."
- **A judge model** checks dress code and the clothes-only rule. It's never the model being tested.
- **I grade taste** blind, side by side against the current version.

Most of the house style is written as checkable rules, so only what's left needs me.

**Checking the judge:** I grade the first 10 cases myself, and the judge grades the same 10. I trust the judge only on checks where it agrees with me on at least 9 of 10. Otherwise I grade that check myself until it does. I re-check whenever the judge model changes.

**Held-out cases:** The golden cases that decide the side-by-side kill criterion never feed into prompt or house-style tuning. Rejections at the mirror and stored cases can shape the house style. If the side-by-side lands at 40–70% and I "fix the biggest reason and retest," the retest uses fresh golden cases, so a pass means the craft improved, not that I memorized the test.

**Pass bar:**
- hard rules and clothes-only: 100%;
- everything else: no worse than today;
- taste: as good or better on at least 80% of cases.

New first events stay paused until it passes.

## Portability Score
<!-- Ready / Partial / Locked -->
**Partial today → Ready by Nov 9.**

The design switches providers with one setting, but nothing is proven yet: no backup has been tested, the eval set doesn't exist, and the prompts have never run on another model.

**The event that moves it:** All four rows wait on the same thing. A backup provider (OpenAI or Google) passes the full eval set, including the clothes-only cases at 100%.
- **If neither passes,** we stay Partial, and we've learned that our judgment depends on one provider.
- **Ready is re-confirmed** on about 30 cases by Nov 15.

**What Ready also requires:**
- **The switch is actually wired up.** Passing the eval proves the backup is good enough, but Ready also needs its keys live, its account funded with rate limits for live traffic, and Routing step 3 connected at the mirror. Otherwise we're Ready on paper and Partial at 11pm.
- **Ready expires.** Models get updated and retired, and our prompts change. Ready is re-confirmed monthly by re-running the backup on the eval set, in the same session as the monthly side-by-side from Module 1. If the backup fails, we drop back to Partial until it passes again.

## If Anthropic doubles pricing tomorrow:
<!-- What's your 48-hour response? -->
**How much it hurts: pennies at our scale.** An event costs roughly 10–25 cents in model calls (estimate; Module 3 measures it), so 10 test men barely notice a doubling.
- **At 1,000 paying men,** at about one event a week (about 4.3 a month), it adds roughly $0.43–1.08 per man per month. At a placeholder paid-tier price of $10–20 a month, that's about 2–11 margin points. Module 3 sets the real price.
- **If the price lands above about $35 a month,** a doubling stays under 3 points, so price alone never triggers a provider switch (see below).
- **Heavy users are the real stress case.**

**Within 48 hours:** Nothing changes mid-test. After that, in this order, and each step only if it passes our eval:
1. **Free wins first:** cache the long style guide, send smaller photos, trim output.
2. **Lower the effort setting** on the same model.
3. **Move the rescue** (and possibly the mirror check) to the smaller model.

**What never gets cheaper:** the first-event recommendation. It's where we win or lose the first try.

**When we switch providers:** only if a backup passes the full eval, including clothes-only at 100%, and saves more than about 3 margin points. Otherwise, the switching cost isn't worth it.

**If no backup passes** (Portability stays Partial): we absorb the increase through the cost-cutting steps above. If margin still drops by more than a threshold set in Module 3, we raise the paid tier's price.

## If Anthropic ships a competing product:
<!-- What's defensible that they can't replicate? -->
**What's defensible is the same as against OpenAI** (see the [data flywheel](data-flywheel.md) and its 90-day plan):
- who has seen him in what;
- the rules learned from his rejections;
- his lookbook;
- owning the moment he reports.

**What's different: the attacker is also our supplier.** A supplier can also:
- change our price, terms and access;
- retire the model our prompts are tuned to;
- ship the capabilities we need in its own product first.

**What's new in our defense:**
- **Portability.** Once a backup passes our eval, price and terms are negotiable, not imposed.
- **The eval set and the provider-neutral style guide.** They're what let us leave safely.
- **Each request gets only what it needs, never names.** The app swaps the names of people at his events for roles before any request ("Person A, investor"). The full record of any man exists only in our system.
- **His face is cropped or blurred before a photo is sent,** if the eval shows no quality loss. Skin tone and hair can matter for color advice, so we test it rather than assume. If the eval shows a loss, we say so and take it to Module 5. The one exception is the optional quick read, which needs his face; he agrees to that first (see Module 3, Human-in-the-loop).

**Do we stay?** Yes, by default, while:
- Claude stays best on our eval;
- the terms hold;
- the API gets the same capabilities as Anthropic's own product.

**We leave if:**
- the terms block our use case;
- a capability we need is withheld from the API;
- the data terms change;
- a price change fails our margin rule;
- a backup beats Claude clearly on the held-out cases: hard rules equal, and taste better on most cases.

We stay because we choose to, not because we're stuck. That's why portability comes first.
