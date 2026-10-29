---
name: ambitious
description: Push work further than it was asked, along three lenses from Felix Rieseberg's "How to be more ambitious" — altitude (the outcome behind the task), depth (what a top expert would use and check), and range (skills borrowed from other fields). Two modes. `task`: deep-dive, develop, or reframe the work in front of you, before or midway through doing it. `review`: a periodic pass over logs (conversation transcripts, run logs, git and PR history, rule ledgers) to find where the work stayed small and what to change so it does not next time. Use when asked 「深掘りして」「もっと野心的に」「発展させて」「ambitious に考えて」「視点を広げて」「ログを ambitious の視点で振り返って」, or "be more ambitious", "go deeper", "what would a much better version look like". For one lens only, use `altitude`, `depth`, or `range`.
---

# Ambitious

Models can do far more than most requests ask of them. Of the four ways to ask for more, **speed** (the same work in less time) is what you already get by default. This skill works the other three:

| Lens | Question | Skill |
|---|---|---|
| Altitude | What outcome is this task for, and what would keep producing it? | `../altitude/SKILL.md` |
| Depth | What would the best expert in the world start from, use, and check? | `../depth/SKILL.md` |
| Range | What verbs does this work need, and which fields do those verbs best? | `../range/SKILL.md` |

Source: Felix Rieseberg, "How to be more ambitious: a tutorial for humans with models" (https://felixrieseberg.com/how-to-be-more-ambitious-a-tutorial-for-humans-with-models/).

## Ground rules

- **Propose, don't creep.** The task as asked stays the floor and gets done well. In `task` mode, put the bigger versions in front of the user and let them choose; do not silently widen the work. Ask before anything that needs new access, spends money, publishes, or changes the user's setup.
- **Specific and hard beats "do your best".** Every proposal names a concrete target and how it will be checked. Hard, specific goals outperform vague ones.
- **Grounded, not generic.** Each idea points to what in the task, the data, or the logs prompted it. If an idea would fit any task ("add tests", "consider stakeholders"), cut it.
- **Permission to fail.** Mark stretch targets as stretch. A stretch that misses still teaches; say what it taught. Do not shrink the target to avoid missing it, and do not pad with hedges.
- **Do not grade yourself.** Whenever a proposal claims "better", name the outside judge (see `depth`).
- **End on a first step.** Every proposal ends with the smallest action that tests it within this session.
- Reply in the user's language.

## Mode: task

Use on the work in front of you: at the start (before building), midway (when it feels done too early), or after (to decide what's next).

1. **Pin the task as asked.** One line: the request, and what "done" means right now.
2. **Run the lenses.** Read each lens skill and work through its questions against this task, with the real material (files, data, the conversation), not from memory. For small tasks, run all three inline in a few lines each. For large ones, give each lens to its own subagent in parallel, with the same model as yours; brief each with the task and the material, not with your ideas, so their answers are not anchored on yours.
3. **Merge into a brief** (below). Drop overlaps; keep at most 2–3 ideas per lens; put what you considered and dropped in "Not worth it".
4. **Hand back a choice.** Recommend one option with the reason. If the user already said to go ahead (「そのまま進めて」「任せる」), take the recommendation and start with its first step.

```markdown
## Ambitious brief: <task>

**As asked:** <request> — done means <…>

### Altitude
- Outcome: <what should happen after this is done> → beyond: <the goal behind that>
- Durable version: <the system or process that keeps producing the outcome>
- Setup it needs: <access, data, environments, permissions to ask for>

### Depth
- Expert's raw material and instruments: <…>
- Unreasonable target: <number> (default would be <number>)
- Assumption to re-derive from raw data: <…>
- New knowledge to produce: <…>
- Outside judge: <check that does not rely on the model's own opinion>

### Range
- Verbs: <the job, as verbs, for whom, under what constraint>
- Crew: <role> → <what they would do to this work and what they would produce>

### Recommendation
<one option>, because <…>. First step: <…>. We'll know it worked when <…>.

**Not worth it:** <ideas dropped and why>
```

## Mode: review

Use periodically (daily or weekly), or when asked to look back over a body of work. The question is not "was the work correct" but "where did the work stay small, and what change to the setup would make it bigger next time".

1. **Scope the input.** What logs, and what window (default: the last 7 days). Typical sources: Claude Code transcripts (`~/.claude/projects/<project>/*.jsonl`), pi sessions (`~/.pi/agent/sessions`), `git log` and PR or issue history, job and run logs, rule or correction ledgers. If a previous review exists, read it first.
2. **Read for episodes.** An episode is one request and what followed (corrections, retries, the end state). For large logs, give slices to subagents (same model as yours) and ask for episodes with pointers (file and line, session id, commit, URL), not summaries.
3. **Match against the signals** below. One episode can hit more than one lens.
4. **Write findings,** ranked by leverage (how often it happens × how much bigger the work could have been). Each finding:
   - Evidence: the pointers, and a short quote of what was asked and what came out
   - Lens and signal
   - The bigger version: what the work could have been
   - Proposal: the change that makes it likely next time — a rule or instruction, a skill, tool or data access, a check, a recurring job — with its cost
   - Confidence: verified in the logs, or inferred
5. **Follow up on the last review.** Which proposals were adopted, which signals came back anyway, which proposals to drop.
6. **Output.** Write where the caller says (a scheduled prompt should give the path); otherwise reply in the chat. Do not apply changes to rules, settings, or code from a review. Propose them; the user decides.

### Signals

| Lens | Signal in the logs | Likely bigger version |
|---|---|---|
| Altitude | The same kind of fix or request repeats across sessions | A durable workflow that removes the repeat (the "keep it crash-free" version of "fix this crash") |
| Altitude | The user had to ask for the obvious next step right after "done" | Ask "what should happen next" before starting |
| Altitude | Work ended at the artifact; nobody checked the outcome it was for | Close the loop on the outcome (was the decision made, did the metric move) |
| Altitude | Manual steps by the user that the model could do with access | Ask for the access or data feed |
| Depth | Estimates or claims made from vocabulary where data was reachable | Query or measure from the raw material |
| Depth | "Looks good" with no independent check | An outside judge defined before the work |
| Depth | A target accepted as given when an order of magnitude better was plausible | Name an unreasonable target and plan what would have to be true |
| Depth | A correction the user made that an expert in the field would have caught | The expert's check, built in |
| Depth | A load-bearing assumption never re-derived | Reproduce it from raw data |
| Range | The goal stated as a noun ("a deck", "a report") and built to the noun | Restate as verbs; build to the verbs |
| Range | Reviews always come from the same kind of eye | Add a missing crew role, especially an adversary |
| Range | One method used for jobs that need different ones | Borrow the method from the field that owns that verb |
| Self-efficacy | Asks shrunk or hedged up front; "can't" claimed but never tried; stopped after one failed attempt | Try the hard version first; record what blocked it |

The signals table also works as a checklist for other periodic jobs (for example a job that tidies rules from conversation logs): pass it the table and the finding format above.
