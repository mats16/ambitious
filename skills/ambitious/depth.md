# Depth: work like a top expert

The core ask: **"I want a deeper version of this task, not a bigger one."** Depth is not more pages or more items. It is the expert's material, methods, targets, and checks. A deeper result is often shorter.

Talking like an expert is not depth. Using the expert's instruments is: a query against the database instead of a markdown table of guesses, a statistical model instead of an adjective, a profiler trace instead of "it seems slow".

## Questions

Work through these against the real task and material, and actually run the instruments you name where you can.

1. **Who is the best in the world at this, and what would they do differently** from what is planned now?
2. **Raw material.** What would they start from? Primary data, raw logs, source code, the original documents, the database — not summaries, dashboards, or what someone said in a meeting.
3. **Instruments.** What methods and tools would they use (SQL, statistics, profiling, simulation, controlled experiments, formal checks)? Which can you run here? Run them.
4. **Unreasonable target.** Name a target well past the default, roughly an order of magnitude (a 200 ms load where 5 s was accepted). Treat it as reachable: what would have to be true? Mark it as stretch; a miss still shows where the limit is.
5. **Re-derive an assumption.** List what the current answer rests on. Pick the most load-bearing one and reproduce it from raw data ("try to reproduce that from the raw data"). Say whether it held.
6. **New knowledge.** What could be learned here that nobody knows yet? An earlier signal of churn than the one in use; a simulation that reproduces the last year from the logs and can then test changes before they ship.
7. **Outside judge.** What check does not rely on the model's own opinion? Tests on real machines, a holdout set, a metric, a separate reviewer (another subagent without your context, a different model, a human expert). Define it before doing the work, not after.

## Output

```markdown
### Depth: <task>
Expert: <who> would <do what differently>
Raw material: <…>  Instruments: <…> (ran: <which, result>)
Unreasonable target: <number> vs default <number> — what must be true: <…>
Assumption re-derived: <assumption> → <held / did not hold, evidence>
New knowledge to produce: <…>
Outside judge: <check>, defined before the work
First step: <…>
```

## Pitfalls

- **Depth is not length.** Cut anything that is more of the same.
- **Name the instrument, then use it.** A plan that lists SQL but never runs a query when the data is reachable is still vocabulary.
- **Self-review is not a judge.** "I checked and it looks right" does not count as the outside judge.
- **Ask before reaching for data you don't have access to,** or that costs money or touches production.
