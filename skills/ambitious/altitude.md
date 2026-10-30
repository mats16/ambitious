# Altitude: the outcome, not the task

A task is one step toward something the user wants to happen. Working at a higher altitude means serving that outcome directly, and, when it recurs, building something that keeps producing it.

Example ladder: "fix this crash" → "keep the apps crash-free" (a loop that watches crash reports, maps versions to commits, fixes, and verifies on real machines). Another: "make the quarterly business review deck with more data" → "tell me what changed this quarter, why, and what we should do about it" → "find the three most urgent decisions, with the best case for and against each" → "design a better way to run the review than a quarterly deck, and test it against the last few quarters".

## Questions

Work through these against the real task and material.

1. **What should happen after this is done?** Then ask it again of the answer. Stop at the first outcome the user owns and can observe (a decision made, a metric moved, a person unblocked). Going higher than that turns vague ("the company does well").
2. **Who uses the output, to do what?** Serve that action, not the artifact. If the output feeds a decision, the decision and its arguments are the product; the document is packaging.
3. **Will this come back?** If the same kind of task recurs, the higher version removes the recurrence: a check, a rule, a job, a tool.
4. **What would make this task unnecessary next time?**
5. **What setup does the higher version need?** Durable work usually means changing the environment, not just the prompt: access to the signals (logs, crash reports, tickets, metrics), the mappings between them (version → commit, customer → account), and a real place to verify (a machine, a staging workspace, a holdout dataset). List these as asks to the user; do not grant them to yourself.

## Output

```markdown
### Altitude: <task>
| Level | Version of the work | Can we verify it here? |
|---|---|---|
| Task (as asked) | … | yes |
| Outcome | … | … |
| Durable system | … | … |
| Process redesign | … | … |

Recommended level: <level>, because <…>
Setup to ask for: <…>
First probe: <riskiest assumption → smallest test → continue/reconsider result>
Extra effort/cost and user review burden: <estimate or unknown>
Must preserve / stop boundary: <constraints and when to return for a decision>
```

## Pitfalls

- **Too high is as bad as too low.** Recommend the highest level you can still verify with what is within reach, or can be within reach after one ask.
- **The task as asked still gets done.** A higher altitude adds to it, or explains why it should be replaced; it never quietly skips it.
- **Don't invent the outcome.** If the outcome is not in the conversation or material, ask the one question that would reveal it.
- **Test before wiring the durable system.** Prefer a bounded replay or other cheap probe that could challenge the recommendation. State what outcome it would demonstrate, not just whether reviewers like it.
- **Use the short output for small tasks** as described in `SKILL.md`; the ladder is a way to think, not a requirement to fill a table every time.
