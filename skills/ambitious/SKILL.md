---
name: ambitious
description: Push work further than it was asked, along three lenses from Felix Rieseberg's "How to be more ambitious" — altitude (the outcome behind the task), depth (what a top expert would use and check), and range (skills borrowed from other fields). `/ambitious [altitude|depth|range] <target>`. With no subcommand, runs all three lenses on the work in front of you and returns a brief; with a lens, runs that lens only. Looking back over logs is `ambitious-review`. Use when asked 「深掘りして」「もっと野心的に」「発展させて」「目的から考え直して」「専門家ならどうする」「別の分野ならどうする」「レッドチームして」, or "be more ambitious", "go deeper", "what is this really for", "look at this from other angles".
---

# Ambitious

Models can do far more than most requests ask of them. Of the four ways to ask for more, **speed** (the same work in less time) is what you already get by default. This skill works the other three:

| Lens | Question | File |
|---|---|---|
| Altitude | What outcome is this task for, and what would keep producing it? | `altitude.md` |
| Depth | What would the best expert in the world start from, use, and check? | `depth.md` |
| Range | What verbs does this work need, and which fields do those verbs best? | `range.md` |

## Subcommands

Read the first word of the arguments.

| Arguments | Do |
|---|---|
| `altitude …`, `depth …`, `range …` | Read that lens file and run it alone on the target. Return only that lens's output. |
| anything else, or nothing | Pick from the request: if it clearly asks for one lens (「目的から」→ altitude, 「専門家なら」「裏付けて」→ depth, 「別の分野」「レッドチーム」→ range), run that. If it names both a window and past work to look back on (「直近 7 日の会話」「先週の PR」), use `ambitious-review` instead; a window alone (「来月までの計画」) is still a task. Otherwise run all three below (the target is the given text, or the current task). |

Source: Felix Rieseberg, "How to be more ambitious: a tutorial for humans with models" (https://felixrieseberg.com/how-to-be-more-ambitious-a-tutorial-for-humans-with-models/).

## Ground rules

- **Propose, don't creep.** The task as asked stays the floor and gets done well. Put the bigger versions in front of the user and let them choose; do not silently widen the work. Ask before anything that needs new access, spends money, publishes, or changes the user's setup. When the user asks for a proposal only, describe the probe without running it; accessible tools are not permission to experiment.
- **Specific and hard beats "do your best".** Every proposal names a concrete target and how it will be checked. Hard, specific goals outperform vague ones.
- **Grounded, not generic.** Each idea points to what in the task, the data, or the logs prompted it. If an idea would fit any task ("add tests", "consider stakeholders"), cut it.
- **Permission to fail, not permission to break constraints.** Mark stretch targets as stretch. A miss still teaches; say what it taught. Do not silently lower the target or drop the original requirements. Name what must not be sacrificed (correctness, privacy, compatibility, or the user's deadline). A hard target does not authorize breaking those constraints.
- **Separate validation from critique.** Whenever a proposal claims "better", name the evidence that would demonstrate it and what remains unverified. An independent reviewer can find blind spots; another model's agreement alone does not validate a factual or performance claim (see `depth.md`).
- **Test the recommendation cheaply.** End on the smallest probe of the assumption most likely to sink the recommendation, with an observable result that would support it or make you reconsider it. A first step is not just starting the build.
- **Bound the attempt.** For the recommendation, state the expected extra effort or cost, user review burden, and when to stop or return for a decision. Use known limits; label estimates and unknowns rather than inventing numbers. If no budget is agreed, propose a bounded probe, not an open-ended run. At the boundary, report the evidence, blocker, and options; do not silently lower the target, expand the budget, or proceed through a failed constraint.
- Reply in the user's language.

## All three lenses

Use on the work in front of you: at the start (before building), midway (when it feels done too early), or after (to decide what's next).

1. **Pin the task as asked.** One line: the request, and what "done" means right now.
2. **Run the lenses.** Read each lens file and work through its questions against this task, with the real material (files, data, the conversation), not from memory. For small tasks, run them inline and use the short output below. For large ones, delegate only genuinely independent work whose contribution justifies its cost; a lens does not automatically need a subagent. Use the same model as yours, and brief each with the task and the material, not with your ideas, so their answers are not anchored on yours.
3. **Merge into a brief** (below). Drop overlaps; keep at most 2–3 ideas per lens; put what you considered and dropped in "Not worth it". When all three were requested, consider all three but say briefly if a lens adds nothing; do not invent work to fill it.
4. **Hand back a choice.** Recommend one option with the reason. If the user already said to go ahead (「そのまま進めて」「任せる」), take the recommendation and start with its first step.

## Output size

For a small task, including a single-lens invocation, use a few lines rather than filling every field:

```markdown
Aim: <better outcome or standard, within the original scope>
Method: <what changes; for all three lenses, briefly note any that add nothing>
Check: <evidence and pass/fail criterion; critique or proxy limits if applicable>
First probe: <riskiest assumption → smallest test → continue/reconsider result>
```

Keep material constraints, extra cost/review burden, and the stop/decision boundary in those lines or one additional line. Shorter output must not omit a necessary safeguard. Use the full brief for larger work; single-lens invocations still return only that lens, with the same safeguards.

```markdown
## Ambitious brief: <task>

**As asked:** <request> — done means <…>

### Altitude
- Outcome: <what should happen after this is done> → beyond: <the goal behind that>
- Durable version: <the system or process that keeps producing the outcome>
- Setup it needs: <access, data, environments, permissions to ask for>

### Depth
- Expert's raw material and instruments: <…>
- Stretch target: <observable target vs measured baseline, or baseline still to measure>
- Must preserve: <constraints the target cannot override>
- Assumption to re-derive from raw data: <…>
- New knowledge to produce: <…>
- Validation: <evidence and pass/fail criterion; planned or observed, and any proxy limits>
- Independent critique: <review that could expose blind spots, if useful; not a substitute for validation>

### Range
- Verbs: <the job, as verbs, for whom, under what constraint>
- Crew: <role> → <what they would do to this work and what they would produce>

### Recommendation
<one option>, because <…>.
- Riskiest assumption: <…>
- First probe: <smallest test and the result that supports or challenges the recommendation>
- Extra effort/cost and user review burden: <estimate or unknown; access/approval needed>
- Stop or return for a decision when: <budget, constraint, or evidence boundary>

**Not worth it:** <ideas dropped and why>
```
