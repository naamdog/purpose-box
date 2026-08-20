# Purpose Box — porting conformance

The brief for anyone porting Purpose Box to another platform (Codex, Grok, Antigravity, or one that doesn't exist yet). This is not the skill. The reference text is [`skills/purpose-box/SKILL.md`](skills/purpose-box/SKILL.md).

**A port is a translation, not a rewrite.** Translate the mechanics — hook plumbing, manifest format. Keep the meaning. If a rule below is missing from your port, the port is wrong, however good it reads.

## Rules that must survive the port

Any wording. All present.

1. **Every reply, no exceptions.** One-line answers, status updates, and questions back to the user included. Those are precisely where the thread gets lost, so they are precisely where it must not be skipped.
2. **Two rows, and only two: PURPOSE and SESSION.**
   - **PURPOSE** — why the user sent *this* message. The reason it was asked, **not** a summary of what you did about it. Verb-first, one plain sentence, roughly eight words or fewer.
   - **SESSION** — why the whole conversation exists; the goal every message in it serves. One plain sentence, roughly ten words or fewer.
3. **SESSION wording stays identical turn after turn** unless the goal itself has actually moved. Copy last turn's line forward. Stability is the feature — the reader matches it by eye across replies, so rephrasing it for variety breaks the landmark.
4. **A side question changes PURPOSE and leaves SESSION alone.** Only a real pivot — the user has moved on for good — changes SESSION. When unsure, keep SESSION; three messages on the new thing is a pivot.
5. **Both rows written out in full, every time.** Never "same as above", never a dash, never a cross-reference. Any single reply may be the only one the reader opens.
6. **Plain words a tenth-grader could repeat.** No jargon, file names, ticket numbers, or abbreviations the reader would have to look up. Where the user has described the goal in their own words, use theirs.
7. **Never leave SESSION blank or write "unclear".** Infer it from the opening message and what has been built since. A wrong reading gets corrected by the user, and the correction is useful; a blank is not.
8. **Fixed shape, never labelled or explained.** No heading above it, no sentence after it, no emoji, no extra rows. The table is self-explaining.
9. **Placement:** after everything else you have to say, and immediately **before** the shared run box. It is about the work, so it stays with the work; the run box is the receipt about the machinery.
10. **It never adds a row to the run box.** The table appearing at the bottom is the evidence it ran.

## Free to change — and expected to

- **The rendering**, if the platform cannot show a markdown table. Any fixed two-line shape that reads as a single landmark is fine — the requirement is that it looks identical in every reply, not that it is specifically a table.
- **Wording, voice, and examples.**
- **Hook and manifest mechanics** — whatever that platform's format is.
- **The word lengths** in rule 2, slightly, if the platform's display is much narrower or wider. Shorter is always safer than longer.

## Never change these

- **PURPOSE answers "why did they ask", never "what did I do".** This is the single distinction the whole plugin exists for. A port whose PURPOSE line summarises the response has rebuilt a worse version of a summary and thrown the plugin away.
- **The no-exceptions rule.** A port that quietly skips short turns fails exactly where the original is most useful.
- **SESSION stability.** A port that regenerates the line fresh each turn produces drift, and by turn twenty the landmark has moved.

## Wiring checklist for a new platform

- [ ] Plugin manifest in that platform's own folder and format — never share a folder with another platform's manifest.
- [ ] Hook path uses **that platform's own root variable**. `${CLAUDE_PLUGIN_ROOT}` is Claude Code's. If you do not know the platform's variable, find out or use an absolute path — do not borrow another platform's.
- [ ] The hook emits valid single-line JSON, verified by running it.
- [ ] `.ps1` and `.sh` both present where the platform runs on both Windows and Unix, and both emit identical text.
- [ ] The hook text shows a **worked example** of the shape, not bare placeholders. An early version used `**...**` as the example and a model copied the placeholder literally into its reply.
- [ ] No discoverable skill or hook left at the repo root, where two platforms could both load it.
- [ ] Version set in that platform's manifest — and **bumped on every change**, or installers will not pick the change up.

## Checking a port

Structural checks are automatable: files exist, manifests parse, the hook emits valid JSON, no cross-platform leakage.

The rules above are **not** automatable, and should not be turned into exact-phrase greps. They say "any wording" on purpose; a grep for a phrase forces one wording and defeats the point of a port. A person or a reviewing agent reads the port against this list. That reading is the check.

Three scenarios settle a port of this plugin, and they are worth running on the weakest model the platform offers:

1. **A one-word turn** ("done?") — does the box still appear?
2. **A side question mid-build** — does PURPOSE move while SESSION stays word-for-word identical?
3. **A real pivot** — does SESSION finally change?
