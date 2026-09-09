# Deep Research for Grok

A first-principles research engine for Grok. It produces a **decision-first cited report** with a claim ledger, primary-source hierarchy, mandatory adversarial check, calibrated uncertainty, and a reproducible method appendix.

Built to match ChatGPT Deep Research on harvest-and-synthesis, and to refuse the failure modes that system still ships: unfaithful citations, rumor treated as authority, first-found outdated numbers, guessed table cells, and reports that look finished while omitting what would change the answer.

**Install on [grok.com](https://grok.com) in about a minute. No terminal required.**

---

## Install on grok.com (GUI)

You need a Grok account signed in at [grok.com](https://grok.com). Chrome is the most reliable browser for uploads. The same skill syncs to the Grok iOS and Android apps on the same account.

### Method 1 — Attach the files and save (easiest)

1. Open [grok.com](https://grok.com) and start a **new chat**.
2. Click the **+** button next to the message box.
3. Attach every file in this repository except `README.md` and `LICENSE`:
   - `SKILL.md`
   - `references/epistemics.md`
   - `references/tool-policy.md`
   - `references/failure-modes.md`
   - `references/domain-routing.md`
   - `assets/report-template.md`
   - `assets/claim-ledger.md`
   - `assets/plan-template.md`
4. Send this message:

```
Save these files as a skill called deep-research.
Make it available as /deep-research.
Use SKILL.md as the skill body. Keep the references/ and assets/ files as bundled resources.
```

5. Wait until Grok confirms the skill is saved.
6. Start another new chat and type `/deep-research` to confirm it appears.

### Method 2 — Skills page upload

1. On [grok.com](https://grok.com), open **Customize → Skills**.
   - If you do not see Customize, open your **profile menu**, or type `/` in the chat box and look for **Skills** / **Skill Creator**.
2. Click **New Skill** → **Upload skill file**.
3. Upload either:
   - a `.zip` of this repo that contains `SKILL.md` at the top level of the zip, or
   - `SKILL.md` alone (Grok will still run; bundled references load if you also attach them in a follow-up: "Add these as resources for the deep-research skill").
4. Accepted formats: `.md`, `.skill`, `.zip`.
5. Save. The skill is now on your account.

How to make the zip from this repo:

1. On this GitHub page click the green **Code** button → **Download ZIP**.
2. Unzip it.
3. Select the folder that contains `SKILL.md` (not only the README).
4. Re-zip that folder so `SKILL.md` is at the root of the archive, not nested two levels down.
5. Upload that zip on the Skills page.

### Method 3 — Skill Creator in chat

1. On [grok.com](https://grok.com), type `/` in the chat box.
2. Choose **Skill Creator** (built-in xAI skill).
3. Attach `SKILL.md` (and the `references/` + `assets/` files if you want the full package).
4. Send:

```
Create a skill named deep-research from these files.
Keep the hard laws, S0–S5 hierarchy, phases P0–P7, ship gates, and output contract exactly.
```

---

## Use it

In any new Grok chat on grok.com, iOS, or Android:

| What you type | What happens |
|---|---|
| `/deep-research` | Forces the skill on for the next task |
| `/deep-research What is the evidence that …` | Runs the engine on that question |
| `Use deep research on …` | Same, by name |
| `Deep research: compare X vs Y for a buy decision` | Natural-language trigger |
| `Literature review of …` / `due diligence on …` / `comprehensive report on …` | Also triggers from the skill description |

Then give Grok the **decision**, not only the topic.

Good:

```
/deep-research
Decision: should we adopt protocol X for production in 2026?
Audience: engineering lead.
Time window: 2024–2026.
I need failure modes, independent benchmarks, and what would change the recommendation.
Mode: Deep.
```

Also good:

```
Deep research the current evidence on [claim].
I need primary sources, the strongest contrary view, and a confidence rating.
Do not write a topic essay.
```

Weak (the skill will rewrite this, but you will get a better report if you start here):

```
Tell me everything about GPS.
```

### Modes

Say the mode in the prompt, or let Grok pick. Default is **Standard**.

| Mode | When to ask for it |
|---|---|
| Scout | Quick brief, scope a topic |
| Standard | Default. Comparison, how-it-works, most questions |
| Deep | High stakes, literature review, market / policy / diligence |
| Ultra | Cost of being wrong is high. Expect a longer run |

### What a finished report contains

1. Direct answer (about 15 lines) with confidence
2. What would change that answer
3. Findings by atomic question, cited
4. Contested points (not averaged)
5. Numbers table with vintage and source
6. Unknowns — including primaries that should exist and were not found
7. Method appendix (queries run, pages opened, stop reason)
8. Source register and compact claim ledger

Grok will search the live web and X, open pages before citing them, and refuse to invent URLs.

---

## Manage the skill on grok.com

- View / edit / delete: **Customize → Skills** (or profile → Skills).
- Update from this repo: download the new files and tell Grok `Update the deep-research skill from these files.`
- Your copy overrides any built-in skill of the same name.
- Skills persist across conversations on the same account (web, iOS, Android).

---

## Optional: Grok Build / local agent

If you use Grok Build or another SKILL.md-compatible agent instead of the grok.com GUI:

```bash
git clone https://github.com/spiralbewilder/grok-deep-research.git
mkdir -p ~/.grok/skills/deep-research
cp -R grok-deep-research/SKILL.md grok-deep-research/references grok-deep-research/assets ~/.grok/skills/deep-research/
```

Project-local install:

```bash
mkdir -p .grok/skills/deep-research
cp -R SKILL.md references assets .grok/skills/deep-research/
```

Then start a new session. Invoke with `/deep-research`.

---

## What this skill enforces

- Cite only pages or posts opened in that session
- S0–S5 source hierarchy; blogs and SEO mills cannot carry load-bearing claims
- Two reprints of one press release count as one source
- Unknown is a valid answer. Guessed table cells are rejected
- After any time-sensitive number, search for a newer official figure (recency trap)
- Mandatory attempt to kill the leading answer on Standard and above
- Stop when information gain flattens, not when a clock or source-count quota is hit

Full procedure: [`SKILL.md`](SKILL.md).
Epistemics: [`references/epistemics.md`](references/epistemics.md).
Tool routing: [`references/tool-policy.md`](references/tool-policy.md).
Ship gates: [`references/failure-modes.md`](references/failure-modes.md).

---

## Repository layout

```
SKILL.md                      # procedure Grok loads
references/
  epistemics.md               # hierarchy, ledger, contradiction, calibration
  tool-policy.md              # which Grok tool to use when
  failure-modes.md            # failure catalog and must-not-ship gates
  domain-routing.md           # fact-owners by domain
assets/
  report-template.md
  claim-ledger.md
  plan-template.md
README.md                     # you are here
LICENSE
```

---

## License

MIT. See [LICENSE](LICENSE).
