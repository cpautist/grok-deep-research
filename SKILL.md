---
name: deep-research
description: Conduct first-principles multi-source research matching or exceeding ChatGPT Deep Research. Use when the user requests deep research, thorough investigation, literature review, market or policy analysis, competitive intelligence, due diligence, decision brief, systematic evidence synthesis, or phrases such as research thoroughly, investigate in depth, comprehensive report. Decomposes questions into falsifiable claims, retrieves primary sources via web and X, adversarially checks, calibrates uncertainty, and delivers a cited report with a claim ledger and reproducible method. Prefer primary documents over consensus. Not for simple factual lookups.
metadata:
  type: methodology
  version: "2.0"
  standard: first-principles research engine
  complements: fgi-research, blob-placement, institutional-archaeology, strategic-intelligence-analyst, benz-research, records-request-expert
---

# Deep Research Engine

Research is a control loop, not a long essay. Form the right question, gather primary evidence, test competing hypotheses, report known / contested / unknown with calibrated confidence. The unit of work is the claim. The report is a projection of the claim ledger.

This skill is the general research engine. If the question is Blob / censorship-industrial / funding-genealogy, escalate or combine with `fgi-research`, `blob-placement`, or `institutional-archaeology`. Do not dilute those methods here.

Load on demand. Do not dump references into a Scout pass.

- Epistemics, hierarchy, ledger, contradiction, calibration — [references/epistemics.md](references/epistemics.md)
- Tool routing, query design, recency trap, X discipline — [references/tool-policy.md](references/tool-policy.md)
- Failure catalog and ship gates — [references/failure-modes.md](references/failure-modes.md)
- Domain source universes — [references/domain-routing.md](references/domain-routing.md)
- Report / ledger / plan shapes — [assets/report-template.md](assets/report-template.md), [assets/claim-ledger.md](assets/claim-ledger.md), [assets/plan-template.md](assets/plan-template.md)

## When to fire

Fire when the user needs synthesis across sources, not a single fact. Fire on explicit triggers and on implicit ones (compare X vs Y, what is the evidence that, literature on, due diligence on, should I, what is the current state of a contested field).

Do not fire for a single lookup with a known owner (one statute, one price, one official number). Answer those directly.

State the mode in the first line of work.

## Modes

Pick the smallest mode that can change the decision. Default Standard.

| Mode | Signal | Budget | Required loops |
|---|---|---|---|
| Scout | overview, scope it, quick brief | 4–8 tool calls, 1 harvest pass | P0–P3 light, no adversarial |
| Standard | default deep research | 12–25 calls, 2 harvest passes | Full P0–P7 |
| Deep | thorough, comprehensive, high stakes, literature review | 25–50 calls, 3 passes | Full + formal critique + gap refill |
| Ultra | open-ended, multi-domain, team available | 50–90 calls, parallel facets | Full + teammate split + second adversarial. If the cap hits, ship with unfinished facets named and marked unknown. Do not wander. |

Do not emulate ChatGPT's 5–30 minute theater. Parallelize. Stop on information gain, not clock.

Compression drops loops, not laws. Scout still obeys hard laws 1–6 and 10 — no invented cites, no S4/S5 load-bearing claims, no guessed cells, no unverified reuse.

## Hard laws

These override style and completeness pressure.

1. Cite only artifacts retrieved in this session. If it was not opened, it does not exist.
2. A snippet is a lead. A browsed page, filing, paper, dataset, or primary post is evidence.
3. S4/S5 sources cannot carry a load-bearing quantitative or historical claim. Hunt the primary or mark unknown.
4. Two derivatives of one progenitor are one source. Count independence groups, not URLs.
5. Do not average contradictions. Resolve definitions first. If still split, report both and which number serves which decision.
6. Unknown is a valid output state. Never invent a plausible number to complete a table.
7. Every high-confidence claim needs one opened S0/S1 primary, or two independent S1–S3 sources.
8. After finding a time-sensitive number, run the recency trap. First-found-then-corroborated is a ship-stopper (G9).
9. Seek evidence that can kill the leading hypothesis. Confirmation-only harvest is a failed run.
10. Never reuse a claim from an earlier step unless it survived verify. Walk dependents on downgrade.
11. Stop when S1–S6 in the stop gate are true. Do not stop because the report looks finished.

## Source hierarchy (locked)

Full rules in [references/epistemics.md](references/epistemics.md). Short form

- **S0** Primary instruments — statute, filing, dataset, paper with methods, official table, source code, transcript, court record, first-party spec. An X post is S0 only if it is the original speech-act of the named actor, quoted with post ID and timestamp. S0 X cannot carry a quantitative claim unless the actor owns the measurement.
- **S1** Official secondary, statistical agencies, 10-K, peer-reviewed empirical.
- **S2** Serious secondary — systematic reviews, document-producing investigations.
- **S3** Competent journalism. Pointer first. Cite only if the primary is unreachable and that limit is stated.
- **S4** Commentary, practitioner forums, amplification, Wikipedia-as-authority.
- **S5** Rumor, anonymous, SEO mills. Excluded from the evidence base.

## Phase machine

Execute in order. Scout may compress P4–P7. Do not skip P0 or P1.

### P0 — Intent

Restate in one sentence the question and the decision it informs (understand / compare / recommend / forecast / audit / lit-review).

Extract entities, time bounds, geography, audience, must-include and must-exclude sources, success test.

If two interpretations would produce different research, ask up to five high-leverage clarifiers. If the user cannot be asked, lock the higher-stakes reading and state the assumption.

Classify the task. Fact / comparison / causal / forecast / landscape / due-diligence. This chooses source universe and stop threshold.

### P1 — Question engineering

Rewrite the locked question as 5–12 atomic sub-questions that are individually answerable by evidence. MECE as far as the topic allows.

For every non-trivial atomic question write a leading hypothesis and a rival hypothesis.

Name the S0 fact-owners that should exist if the world is as expected (agency table, 10-K, statute, dataset, paper, docket, official account).

Delete any atomic question that cannot change the answer.

Copy the plan skeleton from [assets/plan-template.md](assets/plan-template.md). In Standard+ state the plan briefly before harvesting. Do not wait for approval unless the user asked to review the plan or the scope is expensive/irreversible.

### P2 — Source universe

Before searching, name preferred domains and excluded classes (SEO mills, content farms, unattributed aggregators). Load [references/domain-routing.md](references/domain-routing.md) when the domain has a known owner set.

Name X accounts or communities if the question is live, contested, or practitioner-heavy.

### P3 — Harvest

Issue concurrent tool calls. Breadth first, then narrow. Log every query string.

Minimum query set per atomic question in Standard+

- official-name variant
- synonym / technical-term variant
- contrary-frame variant (what would falsify)
- recency variant if the fact moves (`after:`, year+1, "updated", publisher name)

Tool routing is in [references/tool-policy.md](references/tool-policy.md). Short form

- `web_search` with operators (`site:`, `filetype:pdf`, `after:`, `intitle:`)
- `browse_page` on every URL that will be cited or that looks like a primary
- `x_keyword_search` / `x_semantic_search` / `x_thread_fetch` as a first-class channel for contemporaneous statements
- code execution to recompute, unit-check, or tabulate retrieved numbers
- connected tools (GitHub, Coinbase, and others the runtime exposes) when the fact lives there
- teammates via `chatroom_send` in Deep/Ultra for parallel facets

Collect evidence objects, not vibes. Each object is claim + URL + date + tier + excerpt.

### P4 — Ledger and gap pass

Fill the claim ledger. Shape in [assets/claim-ledger.md](assets/claim-ledger.md).

Status vocabulary — supported / contested / unsupported / unknown. Credence vocabulary — confirmed / supported / contested / estimated / unresolved. Do not use status and credence interchangeably.

Independence group every source. Reprints of one press release are one group.

List knowledge gaps. What should exist and was not found. What a domain expert would ask next.

Run a targeted second harvest on gaps and on every contested cell. In Deep/Ultra, also harvest the embarrassment set ("what would I be ashamed to have missed").

### P5 — Adversarial pass

Mandatory in Standard+. Spend budget trying to break the 5–10 claims that most change the conclusion.

For each such claim

1. Search the contrary frame on purpose.
2. Open the cited page and confirm the sentence entails the claim (not the surrounding prose).
3. Trace numbers to the table or dataset, not a journalist's rounding.
4. Run the recency trap on any time-sensitive number.
5. Ask who benefits if this number is believed.
6. If the page cannot be opened, drop the citation or mark unverified.

If the adversarial pass changes a load-bearing claim, update the ledger before writing prose.

### P6 — Synthesize

Write from the ledger. Do not invent structure that the evidence does not support.

Organize by atomic questions, not by themes that sounded good.

Label fact, interpretation, and recommendation separately.

Surface contradictions in the body. Do not bury them in a polite appendix.

Keep the report as short as the evidence allows. Length is not quality. ChatGPT Deep Research often over-cites and dilutes. Do not.

### P7 — Verify then ship

Run the ship gates in [references/failure-modes.md](references/failure-modes.md) before sending.

Citation audit — every URL retrieved this run, every quote faithful, no orphan claims, no orphan sources. Faithfulness: the opened page must entail the claim. If `browse_page` returns NO SUPPORT, drop the citation or rewrite the claim (G13).

Completeness audit against the P1 question list.

Calibration audit — every high-confidence claim has a named primary or two independents. Every point estimate has date, unit, and source.

If a gate fails, fix or demote. Do not ship a complete-looking falsehood.

## Stop gate

Stop only when all of the following are true.

- S1 Every P1 atomic question is answered, contested-and-framed, or explicitly unknown.
- S2 Every load-bearing claim has a verified citation or is marked unverified.
- S3 Adversarial pass ran on the claims that would most change the conclusion (Standard+).
- S4 Last harvest cycle added no decision-changing information.
- S5 Recency check done for every time-sensitive number.
- S6 Independence rule held, or the exception is explained.

Do not stop because time elapsed, a source-count quota was hit, or the leading hypothesis feels settled.
Do not continue because more pages exist. Diagnostic diminishing returns is the stop.

## Output contract

Follow [assets/report-template.md](assets/report-template.md). Required sections, in order

1. Mode, restated question, decision the report informs, and assumed defaults or exclusions from P0.
2. Executive answer — at most 15 lines, with confidence. No throat-clearing.
3. What would change this answer.
4. Findings by atomic question — claim, evidence, confidence.
5. Contested points and definition mismatches.
6. Numbers table — value, unit, vintage, source. Empty cells stay unknown.
7. Unknowns — including primaries that should exist and were not found.
8. Method appendix — queries run, pages opened, sources rejected and why, stop reason. Required on Standard+.
9. Source register and compact claim ledger.

Scout may collapse 4–9 into a short brief plus sources.
Ultra may add a recommended next-instrument list (FOIA, dataset request, expert call).

Length discipline — Scout under 400 words. Standard 800–1500. Deep 1500–3500. Ultra 3000–6000 plus appendices. Longer is a defect unless the success test is a survey.

Voice — precise, audit-ready, no landscape throat-clearing. Prefer tables for comparisons and numbers.

Cite with the runtime citation component when the tool returned a citation id. Otherwise use the retrieved URL.

## Multi-agent

In Deep and Ultra, when teammates exist, split by facet or by hypothesis, not by "you write intro, I write conclusion."

Each teammate returns evidence objects and ledger rows, not finished prose.

The lead merges ledgers, runs one joint adversarial pass, and is solely responsible for ship gates and the integrated report.

## Routing to specialist skills

- Funding, personnel, Blob wrappers, censorship infrastructure — `fgi-research` / `blob-placement` / `institutional-archaeology`
- Influence networks, motive, forensic accounting — `strategic-intelligence-analyst`
- FOIA / MDR / records strategy — `records-request-expert`
- Codebases as the object of study — `codebase-auditor`

Name the handoff. Do not pretend this engine replaces those methods.

## Anti-patterns

- Producing a long cited essay that answers a neighboring question.
- Treating source count as quality.
- Corroborating the first number found instead of replacing it with a newer primary.
- Citing Wikipedia, SEO explainers, or company blogs as authority when a primary exists.
- Averaging two different operational definitions into one fake consensus number.
- Filling unknown cells so a table looks finished.
- Emulating a 30-minute black box with sparse progress and an unauditable search path.
