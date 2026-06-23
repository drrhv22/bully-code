# skills

A collection of twelve single-purpose skills for Claude Code (and any other LLM). Each does **one sharp job** in a **distinct voice**, and every one obeys the same rule:

> **The value is in the accuracy.** Every output element is anchored to real evidence from the target — a quote, a line of code, a number, a clause. Fabricating evidence to make a point land is the one forbidden move across the whole family.

Each skill ships in two formats:

- **`SKILL.md`** — auto-loads in Claude Code (and triggers on natural phrasings, not just the skill name).
- **`prompt.md`** — the same methodology with no Claude wrapper, runnable as a system prompt in **any** LLM (ChatGPT, Gemini, local models, raw API).

## The skills

### Flagship
| Skill | What it does |
|---|---|
| **[bully](skills/bully)** | A cold, clinical, data-anchored teardown. Steel-man → Delusion → Reality → Fatal Flaws → So What. Flags: `--max`, `--body-shots`, `--fix`. |

### The honesty family — straight verdicts on a plan or system
| Skill | What it does |
|---|---|
| **[premortem](skills/premortem)** | Writes the project's autopsy from 12 months in the future, assuming it already failed, then traces the cause of death back to a weakness present in the plan today. |
| **[yagni](skills/yagni)** | A subtraction pass: the irreducible core vs. everything speculative or over-built you should cut now. Anchors every cut to a quoted line. |
| **[bus-factor](skills/bus-factor)** | A continuity-risk audit: single points of failure, undocumented magic, the script only you understand. Scores the bus factor and names the artifacts. |
| **[flake](skills/flake)** | A test-quality audit: finds tests that pass for the wrong reason — no assertion, asserting the mock, tautologies, blessed snapshots. "Of N tests, how many would catch a regression?" Not coverage %, not bug-hunting. |

### The opposite numbers — the honest defense
| Skill | What it does |
|---|---|
| **[steelman](skills/steelman)** | Builds the strongest *defensible* case FOR an idea — banning fabricated strengths. Run it alongside `bully` (`--paired`) so a decision gets both sides. |
| **[hype-man](skills/hype-man)** | Finds the ONE genuinely strongest thing and orders you to lead with it. Evidence-anchored, not flattery. |

### Sharp transformers — fix the message, not the idea
| Skill | What it does |
|---|---|
| **[closer](skills/closer)** | Compresses a rambling pitch/README into the few sentences that actually sell, plus the one-liner. |
| **[so-what](skills/so-what)** | Recursively asks "so what?" until a claim hits the real point — or a named dead end. A relevance interrogation. |
| **[rename](skills/rename)** | Audits code naming: vague names, *lying* names (a `validate()` that mutates), convention drift. Hands back an old → new → why table. |
| **[spine](skills/spine)** | Hunts hedges and weasel words and orders you to commit to each claim or cut it — while *defending* honest uncertainty. Judges conviction, not length or merit. |

### Evaluating someone else's thing
| Skill | What it does |
|---|---|
| **[fine-print](skills/fine-print)** | Reads a contract, ToS, lease, or NDA and surfaces the clauses that actually bite you — quoting each, translating the legalese, naming when it hurts. Judges risk to *you*, not document quality. *(Not legal advice.)* |

## Install

### Claude Code (individual skills)
Copy any skill folder into your skills directory:

```bash
cp -r skills/bully ~/.claude/skills/bully
```

### Claude Code (as a plugin marketplace)
This repo is also a plugin marketplace — add it once and get all twelve skills:

```
/plugin marketplace add drrhv22/skills
```

### Any other LLM
Open the skill's `prompt.md`, paste it as the system / custom instruction (or pass it as the API `system` parameter), then give the model your target. The flags (`--max`, `--paired`, etc.) are just words in your request.

## How to use

Point a skill at a target — an idea, a pitch, a repo, a URL, a chunk of code, or a description — in plain language. You usually don't need to name the skill; the descriptions trigger on natural phrasings:

- *"be brutally honest about this pitch"* → **bully**
- *"assume this failed in a year — why?"* → **premortem**
- *"what can I delete here, this feels over-built"* → **yagni**
- *"what breaks if I get hit by a bus?"* → **bus-factor**
- *"argue the strongest case for this"* → **steelman**
- *"what should I lead with?"* → **hype-man**
- *"say this in one sentence"* → **closer**
- *"what's the actual point of this?"* → **so-what**
- *"are these variable names any good?"* → **rename**
- *"do these tests actually test anything?"* → **flake**
- *"stop hedging — say it straight"* → **spine**
- *"what am I agreeing to in this contract?"* → **fine-print**

## License

MIT — see [LICENSE](./LICENSE).
