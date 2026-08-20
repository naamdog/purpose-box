---
name: purpose-box
description: Use on every reply, in every session, with no exceptions — ends each response with a two-row box stating, in the shortest plain sentence possible, why the user asked this message (PURPOSE) and why the whole session exists (SESSION). For users who run many chats and sessions at once and lose the thread of what any one of them is for. Never skip it for a short turn, a one-line answer, a question back to the user, or a mid-build status update — those are exactly where the thread gets lost.
---

# Purpose Box

*Two lines at the bottom of every reply: why you asked this, and why we are here at all.*

## The one idea

When someone runs many chats, sessions, and threads at once, the hardest thing to keep hold of is not the detail — it is the **point**. What was this message for? What is this whole session for? Every reply ends with both, in the fewest words that are still true. A reader who lands on any single reply cold should be able to say, an hour later, what it was for and what the session is for.

This is not a summary of what you did. It is the *purpose* — the reason the question was asked, and the reason the session exists.

## The shape

Always the same three lines of markdown, always bold, never labelled or explained:

```
| **PURPOSE** | **Build the Purpose Box plugin.** |
|---|---|
| **SESSION** | **Give the public plugins one local home to develop in.** |
```

Which renders as a box:

| **PURPOSE** | **Build the Purpose Box plugin.** |
|---|---|
| **SESSION** | **Give the public plugins one local home to develop in.** |

The shape never changes. It is a landmark — the reader's eye learns where to look, so it must look the same in every reply of every session. Do not add rows, headings, emoji, or a "Purpose Box:" label. The table is self-explaining.

## The two lines

**PURPOSE — why the user sent *this* message.** What it was for, not what you did in response.

- Verb-first. One sentence. Aim for under eight words. A full stop.
- The *why*, not the *what*: "Understand why the deploy failed." beats "Explain the error message." because it says what the answer is for.
- If the user asked three things, pick the one the other two serve.

**SESSION — why this whole conversation exists.** The goal every message in it serves.

- One sentence. Aim for under ten words.
- **Same wording turn after turn.** Stability is the feature. Do not rephrase it for variety — the reader is matching it by eye across replies.
- Infer it from the opening message and what has been built since. If the opening message was vague, write your best reading; the user will correct it, and the correction is useful. Never leave it blank, never write "unclear".

**Both lines, every time, written out in full.** Never "same as above", never "see earlier", never a dash. The reply may be the only one the reader opens.

## Side question or pivot?

This is the one judgement call.

- **A side question** (a quick "what does this flag do?" in the middle of a build): PURPOSE carries the side thing; SESSION stays exactly as it was. The contrast between the two lines is doing its job — it shows the reader they have stepped off the path and where the path is.
- **A real pivot** (the user has moved to a new goal and is not coming back): SESSION changes to the new goal. If you are not sure which it is, treat it as a side question and keep SESSION — three messages in a row on the new thing is a pivot.

## Placement

Last thing in the answer, after everything else you have to say.

If a shared **run box** is present (the fenced code block other skills use to declare that they ran), the Purpose Box goes **immediately before it**: answer, then Purpose Box, then run box. The run box is the receipt about the machinery; the Purpose Box is about the work, so it stays with the work.

The Purpose Box does **not** add a row to the run box. The table appearing at the bottom is the evidence it ran.

## Plain words

Write both lines in words a tenth-grader could repeat. No jargon, no file names, no ticket numbers, no abbreviations the reader would have to look up. "Stop the booking form losing payments." not "Fix the POST handler race in checkout." If the user has said what the thing is for in their own words, use their words.

## Quick reference

| Situation | PURPOSE | SESSION |
|---|---|---|
| First message of a build | Why they asked | Same as PURPOSE, if that is all you know — say it in full |
| Mid-build detail question | The detail, as a why | Unchanged |
| "Done?" / "Is it working?" | "Check the build is finished." | Unchanged |
| User asks something unrelated once | The unrelated thing | Unchanged |
| User has clearly moved on for good | The new thing | The new goal |
| You are asking them a question | Why you need the answer | Unchanged |

## Red flags — you are doing it wrong

| Signal | What it means |
|---|---|
| The PURPOSE line describes what you did | That is a summary. Rewrite as why they asked. |
| PURPOSE runs past one line | Cut until it is one short sentence. |
| SESSION reads differently from last turn but nothing moved | You rephrased for variety. Put the old wording back. |
| You skipped it because the reply was one line | Never skip. Short replies are where the thread gets lost. |
| You wrote "same as above" | Write it out. Every reply stands alone. |
| You added a PURPOSE BOX row to the run box | Remove it. The table is the evidence. |
| The box appears before the answer, or after the run box | Move it: answer → Purpose Box → run box. |

## Common mistakes

- **Answering "what" instead of "why".** "Clone three repos." is what happened. "Give the public plugins one local home." is why it was asked. Always the second.
- **Letting SESSION drift.** Each turn the wording shifts a little, and by turn twenty the landmark has moved. Copy last turn's SESSION line forward unless the goal itself has changed.
- **Treating a detour as a pivot.** One off-topic question does not change the session's purpose. Keep SESSION; let PURPOSE carry the detour.
- **Explaining the box.** No "Here is the purpose box:" and no sentence after it. The table is the last thing before any run box, full stop.
- **Softening it into vagueness.** "Make progress on the project." says nothing. Name the goal: "Get the booking site live."
