# Install Deep Research on grok.com

Checklist for the grok.com web interface. iOS and Android follow the same idea: attach the file, then tell Grok to save it as a skill.

## Before you start

- A grok.com account.
- This file from the repository: [`SKILL.md`](https://github.com/spiralbewilder/grok-deep-research/blob/main/SKILL.md).
- Optional: the `references/` and `assets/` folders if you want the full engine.

## Method 1 — Attach and save (recommended)

1. Open https://grok.com and sign in.
2. Click **New chat**.
3. Attach `SKILL.md` using the paperclip on the message box.
4. Paste this:

```text
Save this uploaded file as a Grok skill named deep-research.
Keep the name deep-research.
Make it available in every conversation from now on.
Trigger it on: deep research, research thoroughly, literature review, due diligence, comprehensive report, investigate in depth.
Confirm when it is saved.
```

5. Wait for confirmation.
6. Open a **new** chat. Skills often load at session start.
7. Test:

```text
Do you have a skill named deep-research? Quote the first hard law.
```

8. Run it:

```text
Use the deep-research skill. Standard mode.
Question: [your question]
```

## Method 2 — Skill Creator

1. On grok.com, click the composer and type `/`.
2. Choose **Skill Creator** (sometimes **New Skill**).
3. Name: `deep-research`.
4. Paste the full contents of `SKILL.md`.
5. Save.
6. Test in a new chat as in Method 1.

## Method 3 — Skills panel import

If your account shows a **Skills** item in the left sidebar or under the profile menu:

1. Open **Skills** or **Manage Skills**.
2. Choose **Import** / **Upload skill file** / **Create skill**.
3. Drop `SKILL.md` or a zip of this repository.
4. Save.
5. Test in a new chat.

Accepted file types observed in the GUI: `.md`, `.skill`, `.zip`.

## Method 4 — Project workspace

If Skills import is missing on your plan:

1. Create a **Project** on grok.com.
2. Upload `SKILL.md` plus every file in `references/` and `assets/`.
3. Add a Project instruction:

```text
For any deep research, literature review, due diligence, or comprehensive investigation request, follow SKILL.md exactly. Load references/ and assets/ as needed. Do not answer those requests as ordinary chat.
```

4. Ask research questions inside that Project.

This binds the skill to the Project rather than to every conversation.

## Full package zip

If you want every supporting file in one upload:

https://github.com/spiralbewilder/grok-deep-research/archive/refs/heads/main.zip

Then say:

```text
Save this package as a Grok skill named deep-research.
Use SKILL.md as the skill body. Keep references/ and assets/ as supporting files.
Make it available in every conversation. Confirm when saved.
```

## How to invoke after install

```text
Deep research: [question]
```

```text
/deep-research
```

```text
Research thoroughly, Deep mode, time window 2023–2026: [question]
```

```text
Scout only: what are the official sources I should read before a full pass on [topic]?
```

## If it does not stick

- Start a **new chat** after saving. Many clients load skills at session start.
- Ask: `List my custom skills.` If `deep-research` is absent, repeat Method 1.
- Do not rename the skill. The directory and slash command expect `deep-research`.
- Uploading only `README.md` will not work. The skill body is `SKILL.md`.

## Grok Build (terminal, optional)

```bash
git clone https://github.com/spiralbewilder/grok-deep-research.git
mkdir -p ~/.grok/skills/deep-research
cp grok-deep-research/SKILL.md ~/.grok/skills/deep-research/
cp -R grok-deep-research/references grok-deep-research/assets ~/.grok/skills/deep-research/
```

Start a new Grok Build session. Invoke with `/deep-research` or a natural-language research request.
