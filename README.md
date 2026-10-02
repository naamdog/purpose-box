# Purpose Box

A plugin for Claude Code and Grok Build that ends every reply with two bold lines in a box - **why you asked this**, and **why this whole session exists** - so you never lose the thread, however many chats you have open.

## What it does

Ships a skill (`purpose-box`) plus a `UserPromptSubmit` hook that fires on every turn and has the model close each response with the same two-row table:

| **PURPOSE** | **Build the Purpose Box plugin.** |
|---|---|
| **SESSION** | **Give the public plugins one local home to develop in.** |

- **PURPOSE** is why you sent *this* message - what it was for, not what Claude did about it. Verb-first, one plain sentence, under eight words.
- **SESSION** is why the whole conversation exists - the goal every message serves. One plain sentence, under ten words, and the *same wording turn after turn*, so your eye can match it across replies.
- It runs on every reply, no exceptions - long answers, one-liners, status updates, and questions back to you. Short replies are exactly where the thread gets lost.
- A side question changes PURPOSE and leaves SESSION alone. Only a real pivot - you have moved on for good - changes SESSION.
- Both lines are always written out in full. Never "same as above". Any single reply should stand on its own.
- It sits at the very bottom of the answer. If other skills print their shared run box (the fenced receipt that says which skills ran), the Purpose Box goes immediately above it: answer, then Purpose Box, then run box. It does not add a row to the run box - the table itself is the evidence.

## Why it exists

When you are building several things at once, across many sessions, the hardest thing to hold onto is not the detail - it is the point. Open an old chat and the first question is always "what was this one for?" Scroll up and the answer is buried under forty tool calls.

Two lines, in the same place, in the same shape, in every reply, answer that in one glance. The hook removes the remembering: it fires on every prompt, so the box is there whether or not anyone thought to ask for it.

## Install for Grok Build

```powershell
grok plugin marketplace add naamdog/purpose-box
grok plugin install purpose-box --trust
```

Or install it with the other naamdog Grok plugins from one marketplace:

```powershell
grok plugin marketplace add naamdog/grok-plugins
grok plugin install purpose-box --trust
```

Start a new Grok session so the skill and hook load. Manage it with `grok plugin list`, `grok plugin disable purpose-box`, or `grok plugin uninstall purpose-box`.

## Install for Claude Code

In any Claude Code session:

```
/plugin marketplace add naamdog/purpose-box
/plugin install purpose-box@purpose-box
```

Start a new session (or restart Claude Code) so the skill and hook load. Manage it any time with `/plugin list`, `/plugin disable purpose-box`, or `/plugin uninstall purpose-box@purpose-box`.

## macOS / Linux note

Grok sets `GROK_PLUGIN_ROOT` and the `CLAUDE_PLUGIN_ROOT` alias, so the same hook file works on both Grok Build and Claude Code.

The hook ships two versions of the reminder script. Both emit the exact same single-line JSON:

- `hooks/purpose-box-reminder.ps1` - Windows (PowerShell). This is the one wired up in `hooks/hooks.json` by default.
- `hooks/purpose-box-reminder.sh` - macOS/Linux (POSIX `sh`).

The Claude Code hook picks the right script by itself: when Windows PowerShell is available it runs the `.ps1`, otherwise it runs the `.sh` with `sh`. Nothing needs editing on macOS or Linux.

`hooks.json` can't hold comments, which is why this note lives here instead.

## Sits well with

Built in the same shape as [world-class-results](https://github.com/naamdog/world-class-results), [simple-language](https://github.com/naamdog/simple-language) and [cheap-trick](https://github.com/naamdog/cheap-trick). Each one stands alone; together they share the run box, and the Purpose Box sits just above it.

## License

MIT - see [LICENSE](LICENSE).
