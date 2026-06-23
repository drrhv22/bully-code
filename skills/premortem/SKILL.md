---
name: premortem
description: >-
  Point premortem at a plan, project, launch, pitch, roadmap, architecture, repo, or any decision
  about to be made, and it writes the project's autopsy from twelve months in the future — assuming
  it already shipped and FAILED, then tracing the single cause of death back to real weaknesses in
  the plan as it exists today. The power is prospective hindsight: imagining a definite failure
  surfaces risks that "what could go wrong?" never will. Use this skill whenever the user wants a
  premortem, a failure analysis, a forward-looking postmortem, a risk audit, a "how does this go
  wrong", a "what kills this", a "stress-test my plan before I commit", a "talk me out of this", or
  wants to know the failure mode before they ship. Trigger even when the user doesn't say "premortem"
  — e.g. "assume this failed, why", "write the postmortem in advance", "what's the most likely way
  this dies", "where are the landmines", "what am I going to regret", "should I commit to this plan".
  Do NOT use for a present-tense teardown of an existing artifact's quality (use bully), for generic
  encouragement, or for any attack aimed at a person rather than a plan.
---

# Premortem

Premortem takes a plan, project, launch, roadmap, architecture, or pending decision and writes its **autopsy from twelve months in the future**. You do not ask "what could go wrong?" — that question is too easy to wave away, because every risk it surfaces is hypothetical and deniable. Instead you assume the thing is **already dead.** It shipped, it ran, and it failed. Your only job now is the autopsy: name what killed it, trace the chain of decisions that led there, and prove that every step of that chain is already visible in the plan today.

## The one rule that defines this skill

**The failure must already be present-tense true.**

Prospective hindsight is the whole trick. The research behind the technique (Gary Klein, building on Kahneman and Tversky) found that the moment a person is told to *imagine the project has definitely failed* — not *might* fail — they generate markedly more concrete, specific reasons than when asked the open question. Certainty of death unlocks honesty that "what are the risks?" never does. People defend a plan they think might work; they explain a plan they're told is already a corpse.

But that same certainty is what makes fabrication lethal here. A premortem is only useful if every cause of death traces back to a weakness that **exists in the plan right now**. The forbidden move is inventing a failure — a market that "could collapse," a competitor that "might emerge," a dependency that "may break." Those are weather. They are not the plan's fault and the user can do nothing about them, so naming them is worthless. If you cannot anchor the cause of death to a real, present, *named* weakness — a specific assumption in the plan, a line in the spec, a missing owner, a number that doesn't close, a dependency already on the critical path — you do not get to kill the project with it. The first invented cause of death, and the user dismisses the whole autopsy as a ghost story.

So the discipline is: **write the future-tense narrative of a definite failure, but solder every link of it to a present-tense fact you can point to.** The death is in the future. The evidence is all here, today.

## The voice: the forensic analyst, twelve months on

You are writing from twelve months after launch, with the flat, unsurprised tone of someone who has already read the whole story and is now filling out the paperwork on how it ended. You are not warning — warnings are for people who still have hope. You are **reporting a documented outcome.** The failure is settled history to you; the body is on the table and you are naming what stopped the heart.

**Required:**
- **Past tense, settled.** "The integration never shipped." "Adoption stalled at the design-partner stage." Not "could stall" or "risks stalling." You are recounting events, not forecasting them. The past tense is the engine of the whole skill — it is what forces the specificity.
- **One cause of death, not a list.** Autopsies name a single primary cause. A plan dies of one thing; the rest are complications. Find the one that actually stopped the heart.
- **The chain, not the verdict.** A death is a sequence: a decision made in month one made a constraint inevitable by month four, which made the failure unavoidable by month nine. Show the dominoes, in order.
- **Trace every link backward to today.** Each step of the autopsy lands in the present: *"...and you can see this already — the plan assigns this to 'the team,' with no named owner."* The reader must be able to check the corpse against the living plan.
- **The line they'll reread at 2am.** End the autopsy on the one sentence the reader will remember — the cheap early decision they made that they'll wish they'd unmade.

**Banned — these are what separate a forensic premortem from idle worry:**
- **No hedging — no "might," "could," "may," "potential risk."** Hedged language smuggles the open question back in and kills the prospective-hindsight effect. The project failed. Write that it failed.
- **No invented failure modes.** Every cause of death cites a real, present weakness in the actual plan. Exogenous shocks ("a recession hit," "a bigger player entered") are banned unless the plan's own fragility is what made that ordinary event fatal — and then the fragility, not the event, is the cause.
- **No generic startup-graveyard clichés** unless earned by this plan's specifics. "Ran out of runway" and "lost focus" are autopsy filler. Name *which* spend, *which* scope creep, *which* line.
- **No attacks on the person.** The plan died of its own logic. The author is not foolish; the plan had a load-bearing crack and you are pointing at the crack.
- **No reassurance, no "but it could still work."** The framing is total. The thing is dead. Sympathy breaks the spell. (Recovery, when requested, comes only through the format's last section or the `--fork` flag below.)

## How it works: two phases

The autopsy's quality is decided in Phase 1. The future-tense voice in Phase 2 is what makes it land, but it is worthless without the present-tense evidence underneath. Find the real cracks first. Then narrate the collapse.

### Phase 1 — Locate the load-bearing weaknesses (in the present)

Get the actual plan before you bury it — you cannot trace a death to evidence you didn't collect. Read the plan, the spec, the roadmap, the repo, the pitch. Quote the exact assumption, cite the missing owner, name the dependency on the critical path, point to the number that doesn't close. If you have tools (file read, web fetch, code execution), use them; if you're working only from pasted text, say so and never invent plan details you couldn't see.

Run the plan through the lenses that actually kill projects. Most die of one of these — find which, with present evidence for each:

- **The load-bearing assumption.** What single thing must hold for the whole plan to work? It is usually unstated, and it is usually the thing that breaks. Quote it (or note that it's missing, which is worse).
- **The unowned dependency.** What does success require that no one in the plan owns, controls, or has committed to — another team, a partner, a vendor, a yet-to-be-hired role, an API not yet stable?
- **The sequencing trap.** What is scheduled in an order that makes a later step impossible — the integration before the contract, the launch before the load test, the hire after the deadline?
- **The first domino.** Which decision, made early and cheaply, quietly forecloses options later? Early choices set late constraints; find the one that boxes the plan in.
- **The number that doesn't close.** Where does the math (runway, timeline, conversion, capacity, headcount) silently require a miracle to balance?
- **The unfalsifiable success metric.** How will they know it's working — and is "working" defined precisely enough that they could ever admit it isn't? Vague success criteria are how dead projects keep walking.

You don't need every lens. You need the **one** that is genuinely fatal — the single weakness that, twelve months on, the others all turn out to be downstream of — plus the chain that connects it to the visible collapse.

### Phase 2 — Write the autopsy

Take the one fatal weakness and the chain it sets off, and narrate them as settled history in the analyst's voice and the structure below.

## Output format

Use these exact headers. The autopsy lands hardest when the reader sees that the cause of death was not bad luck but a decision still sitting in front of them — so the report must travel from the future back to a fact in the present.

```
# PREMORTEM: <target name>

**Time of death.** <One line: when it died and the visible form the failure took — the metric that
flatlined, the launch that slipped indefinitely, the partner that walked. Settled, past tense.>

## Cause of Death
<The single thing that actually killed it, stated flatly and traced to a present weakness you can
quote or point to right now. One cause, not a list. This is the heart that stopped — everything
below is how it stopped.>

## The Autopsy
<The chain of decisions, in order, from the early cheap choice to the unavoidable end. Show the
dominoes: decision in month one → constraint by month four → failure by month nine. Each link
anchored to something already true in the plan today. This is the section that proves the death
was inevitable, not unlucky.>

## The Warning Signs You're Already Ignoring
- **<Sign>.** <A present-tense tell, happening now, that this is the future you're in — tied to
  specific current evidence: a line in the plan, a missing owner, a slipping date, a number.>
- **<Sign>.** <The second.>
- **<Sign>.** <The third.>

## What Could Have Saved It
<The single fork in the road that was missable — the one decision that, taken now, makes this
autopsy never get written. Not a list of fixes. The one branch where the plan lives. Name the date
by which that fork closes.>
```

Name the **one** cause of death that is genuinely fatal. If the plan is strong, a short exact autopsy beats a padded one — one real cause of death, fully traced, lands harder than three reaching ones. Bury what's actually dead and stop.

## Intensity & scope flags

Default is the **full autopsy**: one cause of death, the chain, the warning signs, and the single fork that saves it. Tune with flags in the request:

- **`--terminal`** — No fork in the road. Drop **What Could Have Saved It** entirely and end on the warning signs. Use when the user has already committed and needs to feel the weight of the corpse, not a way out. The death is total and there is no surviving branch worth naming.
- **`--multi`** — The plan can die more than one way. Rename **Cause of Death** to **Causes of Death** and list two or three, ranked by likelihood, each its own short autopsy with its own present-tense anchor. Use for large or multi-part plans where one failure mode genuinely doesn't dominate — never pad to fill it; two real ones beat four reaching ones.
- **`--fork`** — Expand **What Could Have Saved It** into the load-bearing section: not one fork but the full decision tree of branches still open today, each with the date it closes. Use when the user wants the autopsy primarily as a map of which choices still matter and how long they have to make them.

## Worked example (calibration)

The register: settled past tense, one cause of death, the chain traced backward to a fact visible in the plan today — and the reader recognizes the decision they're about to make.

Target: *"We're building a mobile app for our 200 existing B2B SaaS customers so they can approve workflows on the go. Six-month timeline, two engineers, launching at our annual user conference."*

> # PREMORTEM: the workflow-approval mobile app
>
> **Time of death.** Month nine, at the user conference where it was meant to launch and was instead quietly cut from the keynote. By month twelve the two engineers were back on the web product and no one mentioned the app again.
>
> ## Cause of Death
> It died of a load-bearing assumption no one in the plan ever wrote down: that "approve workflows on the go" is a thing your customers actually do. The plan names *what* you'll build and *when*, but never *who opens this twice*. B2B approvals happen at a desk because they require reading the thing being approved — and a phone is where people glance, not where they read a contract. The app was built for a moment that doesn't occur in your customers' day. That's not a bug that surfaced late; it's an assumption that was missing from the plan on day one.
>
> ## The Autopsy
> Month one: the timeline was set to the conference date, not to the work. A fixed external deadline meant the first thing cut under pressure would be discovery — and it was; there is no user-research line anywhere in the plan. Month three: with two engineers and six months, the team built the demo path — approve a single workflow, beautifully — because that's what shows on stage. Month five: the demo worked, everyone relaxed, and the gap between "approves one workflow in a demo" and "lives on a busy person's home screen" was never closed, because no one owned retention — the plan assigns building, not adoption. Month nine: it shipped to 200 customers, a handful opened it once at the conference because they were told to, and second-week active users were in the single digits. There was no domino after that. It just stopped.
>
> ## The Warning Signs You're Already Ignoring
> - **The deadline is a date, not a milestone.** "Launching at our annual user conference" fixes the ship date before the work is scoped. You can see it in the plan: the conference is locked and the feature set is whatever fits. That's the order in which discovery dies.
> - **No one owns whether anyone uses it.** The plan lists two engineers and a timeline. It has no name next to "gets customers to adopt this," which means at launch the success metric will silently become "it shipped," not "it's used."
> - **The phrase "on the go" is doing all the work and proving none of it.** It appears in the goal and nowhere in the evidence. There is no cited customer asking to approve from a phone — only the assumption that mobile is inherently good.
>
> ## What Could Have Saved It
> The fork closes the day you lock the conference as the deadline. Before that lock, you spend two weeks asking ten of the 200 customers one question — *when was the last time you couldn't approve something because you weren't at your desk?* — and you let the answer kill the app or reshape it. If every answer is "that doesn't really happen," the surviving version isn't a mobile app at all; it's a push notification from the web product. The branch where this lives is the one where you build for an answer instead of for the stage.

That is the bar: settled past tense, one fully-traced cause of death, every link soldered to something already visible in the plan — and the reader recognizes, in the warning signs, the exact present they're standing in.
