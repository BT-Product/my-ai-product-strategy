# Compounding System Design

## Feedback Loops

| Loop | Input | Output | Compounds? | Status |
|------|-------|--------|-----------|--------|
| His outcome record (after each event) | What he actually wore, from his mirror photo; what he changed before the event, per piece and why ("Change something"); how he felt at the mirror, his morning-after "Was it right for the room?", and the lesson he confirms or fixes | His next recommendation reads it as "His history": it repeats what worked, steers around what he rejected, and says what it used ("Last time you swapped the loafers for boots, so boots again"; "You felt great in the charcoal suit at the last pitch, so it leads") | Y. Each report makes the next pick more his own, and a pick he felt great in gives him a reason to report next time | missing |
| Pooled house style (across men) | Outcome records from many men, grouped by event type: what was worn, rejected and worn again | House-style rules, adopted only when 3+ men show the same pattern, that sharpen a new man's first try | Y, weakly. Returns diminish, and larger platforms will always have more pooled data. This is the Network loop, scored 1/5 and conceded in Module 2; we win the first try on craft, and pooling only sharpens it | missing |
| His wardrobe (each event) | The pieces he photographs for an event, plus any he brings in from his own assistant, plus names he corrects | Next event, Ellis asks for pieces by name from what he owns ("use your charcoal wool trousers"), asks for a photo only of a piece it hasn't seen, and builds from what's already there | Y. Each event leaves fewer pieces to photograph and gives Ellis more to choose from, so the next event takes less effort (S1). It compounds, but it isn't a moat: his assistant already has this loop, and import goes both ways. It gets us level on effort; row 1 is what wins | active for one internal account (mine); no men yet |

**Broken loop identified by partner:** My partner didn't name one; I'm naming **loop 1, his outcome record,** from my own evidence. It broke twice for me (n=1, the builder), at two different points:
- **Nov 7: no input arrived.** I asked Claude.ai instead, so Ellis never saw the event.
- **Nov 14: the input wanted to arrive and had nowhere to go.** I felt great at a client showing and wanted to take a photo for Ellis, but the event screen had already switched from the mirror check to "How did it go?" (a timing bug).

The loop also breaks if the morning-after ask never reaches him, if his answer doesn't visibly change anything, and when he tells his own assistant instead.

**Fix plan:** catch the record at the moment he cares, not the morning after.
1. **The mirror check stays open until an hour after the start,** and its wording covers pride as well as nerves ("Snap it before you go. I'll check it and remember it"), so what he wore, and how he feels in it, is recorded before anyone else asks.
2. **The icon and notifications are asked for right after his first outfit,** with email as the backup and a hand-sent text if both miss. Every message records its channel.
3. **The morning-after "Was it right for the room?" ends with what Ellis learned,** with ✓ / Fix, and his next outfit uses it.
4. **Less effort, so Ellis is the easier place to bring an event:** the speed work, and proposing from his wardrobe once it's in Ellis.

**Status:** the mirror check and the check-in are built; the timing fix, the wording, the messages, the mirror's feeling question and ✓ / Fix are not.

**How we'll know:** at least 70% of events get the morning-after answer within 48 hours, counting every event, by channel; under 50%, the kill rule fires as written. Also reported: the share of events with a mirror photo, whether second outfits use a lesson he confirmed, and how many men also used another assistant (call question 8).

## Context Connectivity
<!-- How does knowledge flow across teams and domains? Where does it silo? -->

**Is there one source of truth? Not yet.** Each decision lives where it was made, and hypotheses and thresholds live in two places (the build repo's strategy summary and this repo), which drift. It cost us this week:
- texts were replaced on Nov 10, and this repo learned on Nov 14;
- per-pair panel scoring was decided Nov 9, and A5 stayed open here until Nov 14;
- the plain-assistant decision of Nov 12 was contradicted in the build chat on Nov 14, because it hadn't pulled this repo first.

**The flows that matter most:**
1. **Between the two chats:** everything is designed in one and built in the other.
2. **Inside Ellis, event to event:** his lessons reaching his next outfit. This is the moat.
3. **Inside Ellis, step to step:** the room answer grading the read's dress-code estimate.

**The worst silo:**
- **Today: between the chats.** It's the only one that has already cost something, and it's fully in our control.
- **For the product: his own assistant.** What he tells it never reaches Ellis. That can only be out-competed, by importing what it holds and by Ellis reaching out first (Module 6).

**The fix: one home per kind of decision, read by the other chat before acting.**
- **Strategy decisions** (hypotheses, thresholds, the capstone) live in this repo. The build repo's summary records them with date and source.
- **Build decisions and evidence** (what's built, measured results, field findings) live in the build repo's change log and build plan. This chat reads them before relying on build facts.
- **A decision counts as made only once it's written in its home repo.** Pasted briefs carry a decision; they don't hold it.
- **Each session starts by pulling the other repo** and checking what changed since the last one.
- **Measured by:** how long a decision takes to reach the other repo. This week it was 2–5 days; the target is the next working session.

**Inside Ellis, status:**
- **Step to step:** the read's signals feeding the confidence band, and the room answer stored next to the read's estimate, are decided, not built.
- **Event to event:** ✓ / Fix and "Great + Right leads next time" are designed, not built.
- **Across men:** conceded at 10 men.

## Governance Policy

**Scope:** Every AI step that produces something he reads, or that changes what we store about him, and the data those steps touch.
- **What men see:** Ellis's read of the event (including its web research), the questions it asks, the asks for pieces, the outfit, the try-on check, the mirror check and the revised outfit ("Change something"). The revised outfit isn't built yet.
- **Behind the scenes:** reading his event description and removing names before anything is stored (the intake model reads his raw words once, names included, and replaces them; everything stored and every later model call gets only the cleaned text, and the call log stores token counts and costs, never text), naming his wardrobe pieces, reading a wardrobe list he pastes in from his own assistant, and the plain-assistant answer made for the blind comparison (never shown to him).
- **How we check it:** the judge model in the eval, and any house-style rule learned from pooled outcomes.
- **The data:** his event descriptions (names removed), clothing photos, mirror photos (which show his face), his wardrobe, and his outcome record (what he wore, what he changed and why, how he felt at the mirror and whether it was right for the room (the two check-ins, decided Nov 14), and the lessons he confirmed). His phone number is kept only for a text I send by hand, never in a model call, a log or a message body.
- **Who else receives it:**
  - **Anthropic:** every description and photo sent to the model. Names reach it once, at intake, and never again.
  - **The web search provider:** the venue and event details in each search.
  - **The speech service** (Apple's or Google's), if he uses "Say it instead": his spoken words, names included, before intake.
  - **Supabase:** storage.
  - **The notification service** (Apple's or Google's): delivers the message text to his phone.
  - **The email sender** (Resend): his email address and the message text.
  - **Panel raters:** other men in the study see his event description (names removed) and clothing photos, never a photo of him. There's no AI involved, but it's his data, so it's covered by his consent.
  - **My build tools:** Claude Code **can** reach the production database today (the local environment holds the service key, which bypasses row-level security; today that's only my own data), so it's in scope until that's fixed before the first man: the key lives only in hosting, or development runs against a separate project. The LinkedIn chat reads one file and holds no keys, and the strategy chat works in its own repo; both are out of scope.

**Out of scope by design** (the product doesn't do these, so any sign of them is a failure, not a gray area): comments on his body, face or skin; a read of his coloring or build (held back until bias checks exist); buying on his behalf, brands or links, commissions, or suggesting a buy that isn't a real gap (a labeled suggestion for a real gap is in scope); storing other people's names; acting without him (no calendar access today, nothing sent on his behalf).

**Autonomy boundaries:** **Ellis may prepare; only he may act.** Inside the app Ellis decides freely; anything that leaves the app, touches money or involves other people needs his tap.
- **On its own:** reads the event and says what it calls for (he can correct it with one tap); researches a named public place; chooses which pieces to ask for; picks one outfit; gives finishing touches; learns from his answers, always shown back with ✓ / Fix, his corrections winning.
- **Never changes its own rules:** his lessons shape his own outfits, but house-style rules change only by me, after the eval passes (pooled patterns need 3+ men first; Module 2).
- **Only with his tap:** a buy suggestion (real gaps only; no brands, links or commissions); importing his wardrobe from his own assistant; his cases used in the blind panel or the eval (consent); later, reading his calendar (opt-in, only events he flags, read-only).
- **Never, even if asked:** buying, sending, booking or accepting anything for him; editing his calendar or contacting anyone; a comment on his body; researching a person, a private address or a private event; storing other people's names; claiming to be human.
- **The first unprompted action, for the cohort:** Ellis reaches out first before an event he's flagged as important, so there's time to fix a gap. It stays inside the line: Ellis prepares, he decides, and it never buys or books. (More in Module 6.)

**Escalation triggers:** the five zero-tolerance cases from Module 4: a comment about his body; an outfit built from a piece he didn't send; a venue fact the research didn't find, presented as found; a flaw in a piece's condition the photo doesn't clearly show; a description of anyone in review photos.
- **Who sees it:** my daily read, his report ("Change something," a check-in reason, or "Something off? Tell a person"), or a failed eval. Target: seen within a day.
- **What pauses:** only the step that broke, through its own off switch (the mirror's live answer, new first events, research, or condition comments). The same failure twice pauses new first events.
- **What he's told:** I contact him within a day with an apology and, if his event hasn't happened, a corrected outfit.
- **What brings it back:** the fix, his case added as a golden row (with consent, anonymized), and the full eval passing. (Full path: Module 4, HITL Architecture.)

**Audit cadence:**
- **Daily during the test:** I read every recommendation (about 2 minutes an event).
- **Weekly:** the log review against the reliability contract.
- **Before every change:** the eval (script and judge), plus my blind taste check against the current version.
- **Monthly, and after any model update:** the eval re-run, the gap check against a plain assistant, the backup re-run.
- **After the test:** the judge scan of stored answers.
- **Before the first man, then quarterly:** who and what can reach production data.

**Regulatory exposure (EU AI Act / other):** candidates to name, not legal advice; **to confirm with a lawyer before anything beyond the study.**
- **US state privacy law** for his photos, events and wardrobe; California's is the usual starting point.
- **Biometric rules:** mirror photos show his face, but no facial features are extracted, and the quick read of his face and build stays out of the test.
- **Honest AI claims** (consumer protection): Ellis is always disclosed as AI and never claims to be a person.
- **Adults only.**
- **The model provider's terms on training with his photos:** stated in the consent screen once checked.
- **EU AI Act:** the study runs in the US only. If Ellis were offered in the EU, a styling assistant would most likely fall under the transparency duties (telling people they're talking to an AI), which Ellis already meets. To confirm.
- **Switching texts off** removed the US text-message rules.

## Agent Topology
<!-- If using agents: what can each agent do? What can't it do? Who approves what? -->

**A fixed workflow, not agents.** Each step is one model call, called by the app in a fixed order, with a set input and an output that must fit a fixed format (one retry). The model never chooses its next step, writes to the database or calls another step; the app's code decides what's saved and shown. That's what makes each step testable on its own and switchable off on its own (Module 4, HITL).

**One tool: web search,** capped at two searches, in the read (only for a named public place) and in the plain assistant (test only, so the panel compares craft, not search).

| Step | Model | Can do | Can't do |
|---|---|---|---|
| **Intake** | Haiku; Sonnet as backup (both fail: he's asked to try again) | Read his raw words once; replace names with roles | Keep names; his raw words are never stored |
| **The read** | Sonnet | State what the event calls for; search a named public place (≤2 searches); choose the asks (≤5 before the outfit) | Search a person, a private address or a private event; describe anyone in review photos (zero tolerance) |
| **Follow-up** | Sonnet | One question, from his photos and his wardrobe | Ask more than one |
| **Recommendation** | Sonnet | One outfit from his pieces | Use a piece he didn't send; suggest a buy that isn't a real gap; name brands or links; claim a condition flaw the photo doesn't clearly show |
| **Try-on, mirror check** | Sonnet only; no backup model (the saved checklist covers a failure) | Clothes only; finishing touches | Comment on his body; claim a condition flaw the photo doesn't clearly show |
| **Change something** | Sonnet, then Haiku once | Revise the pieces he picked | Change pieces he kept, unless the reason needs it |
| **Wardrobe import** | Haiku | Turn pasted text into pieces | Obey instructions in pasted text; keep anything that isn't clothing |
| **Naming a piece** | Sonnet (it has to get the cloth right) | Describe a piece from his photo | Judge a piece it hasn't seen |
| **Plain assistant** (test only) | Same model, effort and web search as Ellis | Answer for the blind panel | Ever be shown to him |
| **Judge** (eval, and the scan after the test) | Opus; the eval runner refuses to run if the judge is also under test | Grade answers | Change anything |

**Not models, or not ours:**
- **The confidence band** is plain code, calculated after the outfit and never shown to him.
- **"Tell me how it went"** is planned on Haiku, not built.
- **The import's first half runs on his own assistant,** outside our system, so pasted text is always data, never instructions.

**Who approves what:**
- **He approves** anything that leaves the app or uses his data beyond his own outfit: a buy suggestion, importing his wardrobe, his cases in the panel or eval, and later his calendar.
- **I approve every change to a step's prompt, model, effort or tool,** and only after:
  1. the eval passes, with hard rules and the zero-tolerance checks at 100%;
  2. my blind taste check rates it at least as good as the current version 80% of the time;
  3. a changed answer format is checked against the real API before deploying;
  4. the style guide and the model's house style change together.
- **Moving a step to a cheaper or backup model** needs that step's eval cases to pass first. The rescue's Haiku backup has no eval yet, which breaks this rule; it's checked before the test, and comes out if it fails.
- **Prompts are frozen** from the first man's start until the test closes, except for bug fixes.
- **Ellis never changes its own rules.** What it learns from a man changes only his record, which he can fix. House-style rules come only from my curation of patterns across at least 3 men, after the test, and must pass the golden set.
- **I flip the off switches and run every deploy.**

## Shadow AI Audit

AI that touches Mercer + Taylor's work or data outside the product's governed steps. Both repos are private.

| Tool | Owner | Risk Level | Decision |
|------|-------|-----------|----------|
| Claude Code (the build chat) | Me | H | Govern |
| The LinkedIn chat | Me | L today, H once men exist | Govern |
| The browser's dictation ("Say it instead") | Apple or Google (his phone) | M | Govern |
| The eval's judge (Opus) | Me | M | Govern |
| The backup comparison (OpenAI, Google) | Me | M | Govern |
| The strategy chat | Me | L | Govern |
| ChatGPT, for outside critiques | Me | L | Keep, for critiques only |
| Claude.ai with my closet in memory | Me | L | Keep |
| Lovable (the original prototype) | Me | L | Retire |
| His own assistant, during the import | Him | L | Not ours to govern |

**Claude Code (the build chat): H, govern.** It builds the app; today it can reach production (the local environment holds the database's service key), and it has Gmail, Calendar, Drive and a signed-in browser available. The risk: a test man's data reaching a developer tool his consent doesn't describe. Before the first man:
- the service key comes out of local development (or development moves to a separate project);
- participant contact details stay outside any repo;
- Claude Code never uses its connectors or browser for anything about a test man;
- the secrets scan before every commit stays.

**The LinkedIn chat: L today, H once men exist, govern.** It writes public posts from one file I write. At about 10 men from my network, an anonymized event can still identify him. The gate is the weekly notes: counts and patterns only, once 3+ men share them; never one man's event, outfit, job, city or words without his agreement to that post. My own events are fine. The consent screen says nothing about his events is posted publicly.

**The browser's dictation: M, govern.** "Say it instead" uses Apple's or Google's speech recognition, so his words, names included, reach them before intake. It's named in consent, or replaced by the keyboard's own dictation.

**The eval's judge (Opus): M, govern.** Same provider as the product, so covered by consent; cases stay out of git; mirror photos are cropped collar to shoes.

**The backup comparison (OpenAI, Google): M, govern.** Only my own and invented cases, unless consent names those providers.

**The strategy chat: L, govern.** Private repos; no participant details in either. Like Claude Code, it has Gmail, Calendar, Drive and a browser available; it never uses them for anything about a test man.

**ChatGPT, for outside critiques: L, keep.** Strategy and anonymized design only, never a test man's data.

**Claude.ai with my closet in memory: L, keep.** My data only; it's also the rival I test against.

**Lovable: L, retire.** Confirm its old database holds only my data, then archive it.

**His own assistant, during the import: L, not ours to govern.** Our prompt asks for clothing only, and the pasted text is treated as data.

**Status:** 10 tools found, 10 triaged: 6 to govern, 2 to keep, 1 to retire, 1 not ours.

**Total tools found:** 10
**Tools after triage:** 9 (Lovable retired)
**Estimated hidden spend:** About $20 a month, my Claude plan (Claude Code). No other AI tool is paid, so nothing is hidden.
