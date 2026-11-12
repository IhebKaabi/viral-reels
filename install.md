---
name: viral-reels-install
description: Install the viral-reels skill into the current agent (Claude Code, Codex or another agent that reads skills) and fill in the user's brand profile so plans are written for their account.
---

# viral-reels install

Use this file only for first-time install. For daily use, read `skills/viral-reels/SKILL.md`.

## What you are setting up

A Markdown-only skill for planning short-form videos. There is nothing to compile and no API key. Two things must be true when you finish:

1. The current agent can discover `skills/viral-reels/SKILL.md`.
2. `skills/viral-reels/references/brand-profile.md` describes the user's account, unless they choose to skip that.

## Install contract

- Do everything yourself. Ask the user only for what you cannot know: their answers to the brand profile questions.
- Clone to a stable path such as `~/Developer/viral-reels`, not a temporary or downloads folder.
- Keep `SKILL.md`, `references/` and `assets/` together. The skill refers to them by relative path.

## Steps

### 1. Clone to a stable path

```bash
test -d ~/Developer/viral-reels || git clone https://github.com/IhebKaabi/viral-reels ~/Developer/viral-reels
```

If it is already there, run `git -C ~/Developer/viral-reels pull --ff-only` and continue. If the brand profile was filled in earlier, a pull may conflict with it; keep the user's version.

### 2. Register the skill

Link the skill folder into the skills directory of the agent you are running under.

```bash
# Claude Code
mkdir -p ~/.claude/skills && ln -sfn ~/Developer/viral-reels/skills/viral-reels ~/.claude/skills/viral-reels

# Codex
mkdir -p ~/.codex/skills && ln -sfn ~/Developer/viral-reels/skills/viral-reels ~/.codex/skills/viral-reels
```

For another agent, use its documented skills directory, or import `skills/viral-reels/SKILL.md` from its project instructions file.

### 3. Fill in the brand profile

Open `skills/viral-reels/references/brand-profile.md`. Ask the user its questions in one or two short messages, not one at a time. The ones that matter most:

1. What do you sell or teach, and to whom?
2. Which platforms, and in which language?
3. What can you film: yourself, a product, a place, a screen, a second person holding the camera?
4. What is the main goal of your reels: reach, follows, comments, or leads and sales?
5. What is your call to action or offer?
6. Which of your own videos did best, and what happened in their first three seconds?
7. Anything you will not do or say?

Write the answers into the file and change its status line to `STATUS: filled in`. Leave unknown fields blank. If the user wants to skip this, leave the file as it is; the skill will ask what it needs per request.

### 4. Verify

Confirm the link resolves and the skill file is readable:

```bash
test -f ~/.claude/skills/viral-reels/SKILL.md && echo "viral-reels is registered"
```

Then tell the user it is ready and give them one example request to try, such as "give me a reel for [their offer]". Do not start writing reels until they ask.
