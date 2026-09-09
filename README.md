# Deep Research for Grok

First-principles research engine for Grok. Produces a decision-first cited report with a claim ledger, primary-source hierarchy, mandatory adversarial pass, calibrated uncertainty, and a reproducible method appendix.

This is the public package of the `deep-research` skill. It is designed to match ChatGPT Deep Research where that system is strong, and to refuse the failure modes that system still ships: unfaithful citations, rumor treated as authority, first-found outdated numbers, and reports that look finished while leaving the load-bearing cells unknown.

**Repository:** [github.com/spiralbewilder/grok-deep-research](https://github.com/spiralbewilder/grok-deep-research)

## Install on grok.com (GUI)

Use this path. It does not require a terminal.

### Fastest path — about one minute

1. Open [grok.com](https://grok.com) and sign in.
2. Start a **new chat**.
3. Click the paperclip / attach control on the composer and upload **`SKILL.md`** from this repository.
   - Direct file: [SKILL.md](https://github.com/spiralbewilder/grok-deep-research/blob/main/SKILL.md)
   - Raw download: [SKILL.md (raw)](https://raw.githubusercontent.com/spiralbewilder/grok-deep-research/main/SKILL.md)
4. Send this message, exactly:

```text
Save this uploaded file as a Grok skill named deep-research.
Keep the name deep-research.
Make it available in every conversation from now on.
Trigger it on: deep research, research thoroughly, literature review, due diligence, comprehensive report, investigate in depth.
Confirm when it is saved.
```

5. Wait for Grok to confirm the skill is saved.
6. Open a **second new chat** and type:

```text
Use the deep-research skill. Standard mode.
Question: [your question]
```

That is the whole install.

### If you also want the supporting files

`SKILL.md` is enough to run. The `references/` and `assets/` files make the engine stricter (source hierarchy, recency trap, ship gates, report shape). To install the full package:

1. Download this repository as a zip:
   [https://github.com/spiralbewilder/grok-deep-research/archive/refs/heads/main.zip](https://github.com/spiralbewilder/grok-deep-research/archive/refs/heads/main.zip)
2. On grok.com, start a new chat.
3. Upload the zip (or upload `SKILL.md` plus every file under `references/` and `assets/`).
4. Send:

```text
Save this package as a Grok skill named deep-research.
Use SKILL.md as the skill body. Keep references/ and assets/ as supporting files the skill may load.
Make it available in every conversation. Confirm when saved.
```

### If the upload control is not visible

xAI also ships a built-in **Skill Creator**.

1. On grok.com, click the composer and type `/`.
2. Open **Skill Creator** (sometimes labeled **New Skill** or listed under **Skills**).
3. Name the skill `deep-research`.
4. Paste the full contents of `SKILL.md`.
5. Save.

Some accounts also have **Skills** or **Manage Skills** under the profile menu or the left sidebar. If you see **Import** or **Upload skill file**, use that and drop `SKILL.md` or the repo zip. Accepted types observed in the GUI: `.md`, `.skill`, `.zip`.

### How to tell it worked

In a fresh chat, send:

```text
Do you have a skill named deep-research? Quote the first hard law.
```

A correct install quotes a rule equivalent to: cite only artifacts retrieved in this session.

Then run a real query:

```text
/deep-research
Compare the current evidence on [topic]. I need a decision-grade brief, not a topic essay.
```

or, without the slash:

```text
Deep research, Standard mode: what is the current evidence that [claim], and what would change the answer?
```

## Use it

| You type | What Grok should do |
|---|---|
| `Deep research: …` | Full Standard run |
| `Research thoroughly: …` | Full Standard run |
| `/deep-research` | Invoke the skill by name |
| `Scout only: …` | Short pass, still bound by the hard laws |
| `Deep mode: …` | Longer harvest, gap refill, formal critique |
| `Ultra: …` | Maximum budget, unfinished facets marked unknown |

Good prompts name the **decision**, the **time window**, and any sources to prefer or exclude.

```text
Use deep-research. Deep mode.
Decision: whether to treat X as current consensus.
Time window: 2024–2026.
Prefer primary documents and official statistics.
Exclude SEO explainers.
```

Do not use this skill for a single lookup with one obvious official page. Ask that question normally.

## What a finished report looks like

1. Mode and restated question
2. Executive answer (short, with confidence)
3. What would change this answer
4. Findings by atomic question
5. Contested points and definition mismatches
6. Numbers table with vintage
7. Unknowns, including primaries that should exist and were not found
8. Method appendix (queries run, pages opened, stop reason)
9. Source register and compact claim ledger

Unknown is a valid cell. A complete-looking table with guessed numbers is a failed run.

## Grok Build / local install (optional)

For the terminal agent, not required for grok.com:

```bash
git clone https://github.com/spiralbewilder/grok-deep-research.git
mkdir -p ~/.grok/skills/deep-research
cp SKILL.md ~/.grok/skills/deep-research/
cp -R references assets ~/.grok/skills/deep-research/
```

Project-scoped alternative: copy the same files to `your-repo/.grok/skills/deep-research/`. Start a new Grok Build session.

## Package layout

```
SKILL.md                         # skill body — this is what grok.com needs
references/epistemics.md         # hierarchy, ledger, contradiction, calibration
references/tool-policy.md        # tool routing, query design, recency trap
references/failure-modes.md      # F-catalog and ship gates G1–G13
references/domain-routing.md     # fact-owners by domain
assets/report-template.md
assets/claim-ledger.md
assets/plan-template.md
INSTALL-GROK.md                  # same GUI steps, printed as a checklist
LICENSE
```

## Design in one page

- Unit of work: the claim, not the page.
- Cite only artifacts opened in the current session.
- S0–S5 source hierarchy. S4/S5 cannot carry a load-bearing quantitative or historical claim.
- Two reprints of one progenitor are one source.
- After any time-sensitive number, run an update search (recency trap).
- Adversarial pass is mandatory in Standard and above.
- Stop when information gain flattens, not when a clock or source-count quota is hit.

## License

MIT. See [LICENSE](LICENSE).
