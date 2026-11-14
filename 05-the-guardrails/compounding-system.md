# Compounding System Design

## Feedback Loops

| Loop | Input | Output | Compounds? | Status |
|------|-------|--------|-----------|--------|
| His outcome record (after each event) | What he actually wore, from his mirror photo; what he changed before the event, per piece and why ("Change something"); his morning-after "How did you feel in it?" and the lesson he confirms or fixes | His next recommendation reads it as "His history": it repeats what worked, steers around what he rejected, and says what it used ("Last time you swapped the loafers for boots, so boots again"; "You felt great in the charcoal suit at the last pitch, so it leads") | Y. Each report makes the next pick more his own, and a pick he felt great in gives him a reason to report next time | missing |
| Pooled house style (across men) | Outcome records from many men, grouped by event type: what was worn, rejected and worn again | House-style rules, adopted only when 3+ men show the same pattern, that sharpen a new man's first try | Y, weakly. Returns diminish, and larger platforms will always have more pooled data. This is the Network loop, scored 1/5 and conceded in Module 2; we win the first try on craft, and pooling only sharpens it | missing |
| His wardrobe (each event) | The pieces he photographs for an event, plus any he brings in from his own assistant, plus names he corrects | Next event, Ellis asks for pieces by name from what he owns ("use your charcoal wool trousers"), asks for a photo only of a piece it hasn't seen, and builds from what's already there | Y. Each event leaves fewer pieces to photograph and gives Ellis more to choose from, so the next event takes less effort (S1). It compounds, but it isn't a moat: his assistant already has this loop, and import goes both ways. It gets us level on effort; row 1 is what wins | active for one internal account (mine); no men yet |

**Broken loop identified by partner:**
**Fix plan:**

## Context Connectivity
<!-- How does knowledge flow across teams and domains? Where does it silo? -->

## Governance Policy

**Scope:** Every AI step that produces something he reads, or that changes what we store about him, and the data those steps touch.
- **What men see:** Ellis's read of the event (including its web research), the questions it asks, the asks for pieces, the outfit, the try-on check, the mirror check and the revised outfit ("Change something"). The last two aren't built yet.
- **Behind the scenes:** reading his event description (and removing names before anything is stored), naming his wardrobe pieces, reading a wardrobe list he pastes in from his own assistant, and the plain-assistant answer made for the blind comparison (never shown to him).
- **How we check it:** the judge model in the eval, and any house-style rule learned from pooled outcomes.
- **The data:** his event descriptions (names removed), clothing photos, mirror photos (which show his face), his wardrobe, and his outcome record (what he wore, what he changed and why, how he felt in it, and the lessons he confirmed). His phone number is kept only for a text I send by hand, never in a model call, a log or a message body.
- **Who else receives it:**
  - **Anthropic:** every description and photo sent to the model.
  - **The web search provider:** the venue and event details in each search.
  - **Supabase:** storage.
  - **The notification service** (Apple's or Google's): delivers the message text to his phone.
  - **The email sender** (Resend): his email address and the message text.
  - **Panel raters:** other men in the study see his event description (names removed) and clothing photos, never a photo of him. There's no AI involved, but it's his data, so it's covered by his consent.
  - **My build tools** (Claude Code, the build chat, the LinkedIn chat): *to confirm:* in scope if any of them can reach the production database; out of scope only if they never see real user data.

**Out of scope by design** (the product doesn't do these, so any sign of them is a failure, not a gray area): comments on his body, face or skin; a read of his coloring or build (held back until bias checks exist); buying on his behalf, brands or links, commissions, or suggesting a buy that isn't a real gap (a labeled suggestion for a real gap is in scope); storing other people's names; acting without him (no calendar access, nothing sent on his behalf).

**Autonomy boundaries:**
**Escalation triggers:**
**Audit cadence:**
**Regulatory exposure (EU AI Act / other):**

## Agent Topology
<!-- If using agents: what can each agent do? What can't it do? Who approves what? -->

## Shadow AI Audit

| Tool | Owner | Risk Level | Decision |
|------|-------|-----------|----------|
| | | H / M / L | keep / govern / kill |
| | | H / M / L | keep / govern / kill |
| | | H / M / L | keep / govern / kill |

**Total tools found:**
**Tools after triage:**
**Estimated hidden spend:**
