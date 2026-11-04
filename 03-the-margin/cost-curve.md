# Cost Curve & Pricing Strategy

## Cost Model

| Cost Category | Per-User/Month | Notes |
|--------------|----------------|-------|
| Inference (primary model) | ~$0.30 average (~2 events) · ~$0.60 engaged (~4.3) · ~$1.50–2.00 heavy (~8–10) · ~$3–4 daily use | Claude Sonnet 5.5. About 13¢ an event. Estimated; measured from Nov 3. Excludes the test-only plain-assistant call |
| Inference (cascading/triage) | ~0.3¢ average · ~1.5¢ heavy month (about 1% of Sonnet) | Claude Haiku 5.5: structures each event and reads his post-event written answers. About 0.1–0.15¢ an event. Estimated; measured from Nov 3 |
| Infrastructure | ~$3.06 at 10 men · ~16¢ at 1,000 men (~23¢ engaged, ~40¢ heavy) | Fixed: ~$30 a month today → ~$100 at 1,000 men. Variable: texts, ~3¢ an event. Estimated |
| Data/storage | Under 0.1¢, even in his second year | ~9–10 photos an event at ~300 KB: ~70 MB a year average, ~150 MB engaged. Overage ~$1 a month at 1,000 men; serving stays inside included transfer. Photo tokens are counted under inference. Estimated |
| Human-in-the-loop | $0 a month. The quick read is one-time: ~$1–2.50 per man, booked as activation | Nothing waits on a human. The quick read, from the cohort on, is approved by me: 2–5 minutes at $60 an hour. Automated after 30 reviews meet the bar |
| **Total AI COGS** | **At 1,000 men: ≈$0.46 average · ≈$0.84 engaged · ≈$2.17 heavy** (≈$3.36 average at 10 men) | A heavy man costs about 4.7 times an average one, because AI cost grows with every event. Sonnet is the biggest line at scale; fixed infrastructure is the biggest at 10 men |

### Inference (primary model)
**Claude Sonnet 5.5.** Estimated; replaced by measured numbers from Nov 3.

**Sonnet calls per event:**
- one recommendation call, which also returns the mirror checklist and a backup outfit;
- about 0.9 mirror checks;
- about 0.25 rescues.

That's about 2.2 Sonnet calls, or roughly **13¢ an event**. Photos are about two-thirds of the input, and thinking tokens are the biggest unknown.

The test-only plain-assistant call is covered under "Not in monthly COGS" below.

**Per man per month:**
- **Average paying man** (~2 events): ~$0.30
- **Engaged** (~4.3 events): ~$0.60
- **Heavy, in holiday season** (~8–10 events): ~$1.50–2.00. That's about 15–25¢ an event, above the usual 13¢, on the assumption that heavy men do more mirror checks and rescues per event (about 1.5 checks and 0.5 rescues, or about 18¢) while rotating outfits across back-to-back parties. The top of the range leaves room for thinking tokens, the biggest unknown. The per-task logs check it.
- **Stress case, daily use:** ~$3–4

**Average vs. active men:** The ~2-event average includes men drifting toward cancelling. The Module 1 moat milestone (10+ events at 3 months) counts only men still active, and assumes they average at least 3.3 events a month, about the "engaged" segment above. That's an assumption, not a measurement; the Nov 30–Dec 20 cohort checks it.

**Measured from Nov 3:** every model call logs its tokens and cost, tagged by task (recommendation, plain assistant, mirror check, rescue, intake).

### Inference (cascading/triage)
**Claude Haiku 5.5.** Estimated; measured from Nov 3.

**What it does: it parses.** At each event's intake, it structures the event (type, setting, time, who'll be there). After the event, it reads his written answers. Intake runs every event, not once.

**Roles, never names:** before anything reaches Haiku, the app swaps names for roles ("Person A, investor, has seen you before"). Real names stay in our database, so "who saw him in what" still works, because our system tracks who's who, not the model.

**Cost:** about 0.1–0.15¢ per event, so roughly **0.3¢ per man per month on average and 1.5¢ in a heavy month**, about 1% of the Sonnet cost.

### Infrastructure
Estimated.

**Fixed:**
- **Today:** about $30 a month: Supabase Pro ($25) and texting registration (~$3 a month after ~$20 one-time). Hosting is free during the test.
- **At ~1,000 men:** about $100 a month: database compute, hosting and standard texting registration.

**Variable: texts.** About 2.4 texts per event (the pre-event mirror prompt, the post-event question, and a reminder when needed) at ~1.2–1.3¢ each: **about 3¢ per event**, 20–30 times the cheap model's cost.

**Per man per month:**
- **At 10 men:** ~$3.06
- **At 1,000 men:** ~16¢ on average, ~23¢ engaged, ~40¢ heavy

At scale, the texts cost about as much as the servers. They stay, because the post-event text is the critical path for reporting back.

**Push is a later saving, tested first.** On a mobile web app, push works on iPhone only if he adds the app to his home screen, so texts will carry nearly every post-event question through the test and cohort. Push replaces texts only after a comparison shows it holds the report-back rate. Saving about 2¢ an event isn't worth triggering our own report-back kill rule.

### Data/storage
Estimated.

**What he uploads:** He photographs the pieces he's considering at each event; there's no closet setup. That's about 9–10 photos per event, resized on the phone to ~300 KB: **~70 MB a year for an average man, ~150 MB engaged.**

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

**The one planned human step is the quick read.** He sends an optional photo of himself, and Ellis drafts which colors and cuts suit him. Because that judges his appearance, a person approves each read before he sees it, until the trust and guardrail rules exist. It's out of the 10-man test (whether men would share the photo is asked in the follow-up call instead) and arrives with the cohort.

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
- sending the event-day texts by hand until texting registration is approved;
- the optional follow-up call.

### Not in monthly COGS
- **The plain-assistant comparison is a test cost.** Each man's first event gets one plain-assistant call for the blind side-by-side (about 5–6¢, taking that event to about 18¢). It runs during the prototype test, and in the cohort if H1 needs a retest, and is removed once H1 is proven.
- **The optional quick read is the only one-time cost in the product,** booked as activation: a few cents of model cost plus my review time (~$1–2.50 per man; see Human-in-the-loop). My time is the real cost until it's automated.
- **The monthly gap check is a small fixed cost, not a per-man one:** our model vs. a plain assistant on stored cases, run offline. So are eval runs and the judge.

## Cascading Strategy
<!-- Cheap model → frontier model routing logic -->

**Triage model:**
**Frontier model:**
**Routing rule:**
**Expected cascade ratio:**

## Pricing Model

**Current pricing:**
**Proposed AI pricing:**
**Model:** seat-based / usage-based / outcome-based / hybrid

## Stress Tests

| Scenario | Impact on Margin | Response |
|----------|-----------------|----------|
| Inference costs 3x | | |
| Heaviest segment doubles | | |
| Model provider raises prices 50% | | |

## Board One-Pager
<!-- Before/After: Old SaaS revenue vs. AI usage revenue for your product -->

**Before (traditional SaaS):**
**After (AI-enabled):**
**Net margin shift:**
