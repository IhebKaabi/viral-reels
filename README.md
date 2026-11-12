# viral-reels

A skill that makes Claude (or any agent that reads skills) plan short-form videos the way outlier videos are built: as a chain of three psychological beats.

**Stop the scroll → hold attention → pay off.**

Give it a topic, a reel that went viral, or a script that flopped. It returns a plan you can film: a hook described as what is seen, read and heard, a timed beat sheet, a caption, and an honest list of what could still go wrong.

Works for Instagram Reels, TikTok and YouTube Shorts. No dependencies, no API keys; it is Markdown only.

## What it does

| Mode | You bring | You get |
|---|---|---|
| **Create** | A topic, product or offer | A shoot-ready reel plan with three alternative hooks to test |
| **Breakdown** | A reel that outperformed | Why it worked, beat by beat, and versions for your niche |
| **Fix** | A script or reel that flopped | A diagnosis by beat and a full re-cut |
| **Research** | A niche and no ideas | A method for finding outlier videos worth modelling |
| **Batch** | A need for a week of content | Plans that vary triggers and formats on purpose |

## The idea

Videos that travel far beyond their creator's audience tend to use one deliberate trigger per beat. Videos that flop usually miss a beat: nothing to stop for, nothing holding the middle, or an ending that does not answer the opening.

| Beat | Job | Examples of triggers |
|---|---|---|
| 1. Stop | Earn the first 1 to 3 seconds | Danger, pattern interrupt, broken reality, witness hook, curiosity |
| 2. Hold | Keep a question open | Prediction trap, open loop, tension before the payoff, escalation |
| 3. Pay off | Answer it in a way that drives the goal | Unexpected twist, misdirection, product as punchline, missing payoff |

The skill carries a library of 26 triggers (why each works, how to stage it, how it fails), 15 reel formats with timing skeletons, a pre-publish checklist and a case library of real outliers.

## Example

Request: *"I run an online chess coaching business for adult beginners. I need a reel that gets people to book the free trial lesson. I can film myself at a real board and screen-record chess.com."*

From the plan it returned:

> **Chain:** Stop: pattern interrupt → Hold: open loop → Pay off: product as punchline
>
> **See:** a real board mid-game. One knight wears a bright sticky-note flag that says FREE. A hand comes in with a bishop and takes it.
> **Read:** What your opponent sees
> **Hear:** the clack of the capture, then "This is what your opponent sees."
>
> ...the tag the viewer has been watching ends up stuck on the laptop running Zoom: the only thing that should be free is the first lesson.

Full outputs are in [`examples/`](examples/):

- [Create: chess coach, free trial lesson](examples/create-chess-coach-free-trial.md)
- [Breakdown: a bakery reel, adapted for a dental clinic](examples/breakdown-bakery-reel-for-dental-clinic.md)
- [Fix: a flopped skincare script](examples/fix-flopped-skincare-reel.md)

## Install

### Setup prompt

Paste into Claude Code, Codex or any agent with shell access:

```text
Set up https://github.com/IhebKaabi/viral-reels for me.

Read install.md first, register the skill with whichever agent you're running under, then ask me the brand profile questions and save my answers. After that, tell me it's ready.
```

### Claude Code plugin

```bash
claude plugin marketplace add IhebKaabi/viral-reels
claude plugin install viral-reels@viral-reels
```

### skills CLI

```bash
npx skills add IhebKaabi/viral-reels
```

### By hand

```bash
git clone https://github.com/IhebKaabi/viral-reels ~/Developer/viral-reels
ln -sfn ~/Developer/viral-reels/skills/viral-reels ~/.claude/skills/viral-reels   # Claude Code
# ln -sfn ~/Developer/viral-reels/skills/viral-reels ~/.codex/skills/viral-reels  # Codex
```

### Claude app

Download `viral-reels.skill` from the [latest release](https://github.com/IhebKaabi/viral-reels/releases/latest) and add it under Settings → Capabilities → Skills.

## Use it

Ask in your own words. The skill picks the mode.

> give me a reel for my pilates studio, I want more trial bookings

> this reel got 3M views on an account with 4k followers, why? [describe or link it]

> my last reel flopped, here's the script, fix it

> plan five reels for next week for my coffee roastery

> how do I find viral formats in the personal finance niche?

## Make it yours

The skill ships niche-neutral. Fill in [`skills/viral-reels/references/brand-profile.md`](skills/viral-reels/references/brand-profile.md) with your niche, audience, voice, what you can film and what has already worked for you, and it stops asking and starts writing for your account. The setup prompt above does this by interview.

## What's inside

```
skills/viral-reels/
├── SKILL.md                      the workflow and the five modes
├── references/
│   ├── triggers.md               trigger library by beat
│   ├── formats.md                15 formats with timing skeletons
│   ├── checklist.md              pre-publish check
│   ├── outlier-research.md       finding videos worth modelling
│   ├── case-library.md           worked breakdowns of real outliers
│   └── brand-profile.md          your niche, voice and constraints
├── assets/
│   └── reel-plan-template.md     the fixed output structure
└── evals/                        the test cases used below
```

## Does it help?

Tested on three requests (create, breakdown, fix), each run once with the skill and once without, then graded against 26 written checks.

| | With the skill | Without |
|---|---|---|
| Checks passed | 26 of 26 | 22 of 26 |
| Average time per reply | about 5 min | about 1.5 min |
| Average tokens per reply | about 110K | about 69K |

Read this as a sanity check, not proof of better videos:

- The checks are structural (a named trigger for each beat, a timed beat sheet, a diagnosis organised by beat). Whether the resulting reel performs is something only posting it can tell you.
- On the breakdown test both versions passed every check.
- The visible difference is in the hooks. With the skill, openings are things you see (a price tag on a chess piece, a dirty cotton pad after washing); without it, openings are mostly spoken lines.
- It is three cases and one run each. Two small changes were made to the skill after this test and have not been re-run.

The test cases are in [`skills/viral-reels/evals/`](skills/viral-reels/evals/) if you want to run them yourself.

## What it will not do

- Promise views. No method can. This one removes the avoidable reasons a reel fails.
- Fake safety or health warnings, invent numbers, or copy another creator's video. Some viral examples do these things; the skill keeps the trigger and drops the deception.
- Make the video. It ends at a plan you can film or hand to a video tool.

## Where the method comes from

The library was built by studying outlier videos: short-form videos that travelled far beyond their creator's usual reach, across niches including real estate, food, cars, fashion, hospitality and coaching. Each one was broken down into what stopped the scroll, what held attention and how it paid off. The triggers that kept recurring became the library, and the worked cases are in [`case-library.md`](skills/viral-reels/references/case-library.md).

## Contributing

The most useful contribution is a new case: an outlier video broken down into its three beats, added to `references/case-library.md`, plus any trigger it reveals that the library does not have yet.

## License

[MIT](LICENSE)
