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

- **Aim beyond the request; execute within authority.** The task as asked is the floor, not the ceiling. Propose the outcome or redesigned process worth reaching even when it goes beyond the original artifact. Preserve the user's actual requirements, and make any proposed replacement explicit. Execute within the scope and permissions they have granted; ask before new access, unapproved spending, publication, or changes to their setup. A proposal-only request stays a proposal.
- **Specific and hard beats "do your best".** Every proposal names a concrete target and how it will be checked. Hard, specific goals outperform vague ones.
- **Grounded, not generic.** Each idea points to what in the task, the data, or the logs prompted it. If an idea would fit any task ("add tests", "consider stakeholders"), cut it.
- **Treat the hard target as reachable.** Ask what would have to be true, then look for a way to make it true. A stretch is an honest attempt, not a disclaimer. After a failed method, use what it taught to try a materially different approach; do not lower the target just because the first attempt failed. An honest miss with evidence is useful.
- **Challenge assumptions, respect actual boundaries.** Permissions, privacy, and explicit user limits are boundaries. The current API, architecture, workflow, and available toolset are assumptions to examine, not automatic invariants. If a breakthrough needs one changed, propose the change and obtain any required approval rather than ruling it out. Experiments can fail in an appropriate sandbox; do not hide that by weakening acceptance criteria or claiming a broken result is complete.
- **Separate validation from critique.** Whenever a proposal claims "better", name the evidence that would demonstrate it and what remains unverified. An independent reviewer can find blind spots; another model's agreement alone does not validate a factual or performance claim (see `depth.md`).
- **Set the ambition first; make learning efficient.** Choose the outcome worth reaching before choosing the probe. Test the assumption that most changes its feasibility with the smallest informative experiment, and say how its result changes the next move. Small describes the learning step, not the goal; do not choose a lesser outcome just because it is cheaper to test.
- **Use checkpoints to advance the attempt.** Make material extra effort/cost and user review burden visible, distinguishing estimates from unknowns. Within authorized work, use learning checkpoints to change methods and keep going; missing estimates or an unspecified budget are not reasons to pause for routine approval. At an explicit resource limit or a need for new authority, report the evidence, blocker, and the next experiment or investment that could unlock the target. Do not exceed the limit or quietly shrink the ambition.
- Reply in the user's language.

## All three lenses

Use on the work in front of you: at the start (before building), midway (when it feels done too early), or after (to decide what's next).

1. **Pin the task as asked.** One line: the request, and what "done" means right now.
2. **Run the lenses.** Read each lens file and work through its questions against this task, with the real material (files, data, the conversation), not from memory. For small tasks, run them inline and use the short output below. For large ones, use subagents for genuinely independent work that brings a distinct method or tests a different hypothesis; scale the effort to the outcome, not to a fixed roster. A lens does not automatically need a subagent. Use the same model as yours, and brief each with the task and the material, not with your ideas, so their answers are not anchored on yours.
3. **Merge into a brief** (below). Drop overlaps; keep at most 2–3 ideas per lens; put what you considered and dropped in "Not worth it". When all three were requested, consider all three but say briefly if a lens adds nothing; do not invent work to fill it.
4. **Hand back a choice.** Recommend one option with the reason. If the user already said to go ahead (「そのまま進めて」「任せる」), take the recommendation and start with its first step.

## Output size

For a small task, including a single-lens invocation, use a few lines rather than filling every field:

```markdown
Aim: <bold outcome or standard worth reaching; make any proposed scope change explicit>
Method: <what changes; for all three lenses, briefly note any that add nothing>
Check: <evidence and pass/fail criterion; critique or proxy limits if applicable>
First probe: <riskiest assumption → smallest test → continue/reconsider result>
```

Mention actual boundaries, material extra cost/review burden, and the next decision point in those lines or one additional line when they affect the choice. Do not invent constraints, numerical estimates, or approval gates to fill a format. Use the full brief for larger work; single-lens invocations still return only that lens, with the same ambition and authority boundary.

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
- Actual boundaries / assumptions to challenge: <explicit limits vs current choices worth changing>
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
- First probe: <smallest informative test of the bold target; what each result would teach>
- Material effort/cost and user review burden: <estimate or unknown; new authority needed, if any>
- Next checkpoint: <what to learn, how to adapt, and what further experiment or investment could unlock the target; respect explicit limits>

**Not worth it:** <ideas dropped and why>
```
