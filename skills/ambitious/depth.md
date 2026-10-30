# Depth: work like a top expert

The core ask: **"I want a deeper version of this task, not a bigger one."** Depth is not more pages or more items. It is the expert's material, methods, targets, and checks. A deeper result is often shorter.

Talking like an expert is not depth. Using the expert's instruments is: a query against the database instead of a markdown table of guesses, a statistical model instead of an adjective, a profiler trace instead of "it seems slow".

## Questions

Work through these against the real task and material. Run the instruments you name where available and authorized; a proposal-only request does not authorize the proposed experiments. Distinguish inspected material, planned checks, and checks actually run.

1. **Who is the best in the world at this, and what would they do differently** from what is planned now?
2. **Raw material.** What would they start from? Primary data, raw logs, source code, the original documents, the database — not summaries, dashboards, or what someone said in a meeting.
3. **Instruments.** What methods and tools would they use (SQL, statistics, profiling, simulation, controlled experiments, formal checks)? Which can you run here within the authorized scope? Use those, and name the access or approval needed for the rest.
4. **Stretch target with constraints.** Name a target well past a competent default, and ask what would have to be true to reach it. An order-of-magnitude improvement can be useful (a 200 ms load where 5 s was accepted), but is not a quota for every task. Use an observed baseline; if it is unknown, measuring it is the first probe. Do not invent precision for qualitative work: define an observable pass/fail criterion instead. Mark the target as stretch, name what it must preserve (correctness, privacy, compatibility, or the user's deadline), and set an effort/budget boundary at which to report results and ask for a decision rather than silently lowering the target or trying indefinitely.
5. **Re-derive an assumption.** List what the current answer rests on. Pick the most load-bearing one and reproduce it from raw data ("try to reproduce that from the raw data"). Say whether it held.
6. **New knowledge.** What could be learned here that nobody knows yet? An earlier signal of churn than the one in use; a simulation that reproduces the last year from the logs and can then test changes before they ship.
7. **Validation and independent critique.** Define them before doing the work, not after:
   - **Validation:** evidence that can establish the claim — tests on real machines, held-out data, a reproduction, a measured metric, or observed behavior of real users/readers. State the pass/fail criterion and distinguish a planned check from an observed result. For qualitative work, name the audience and what their understanding or behavior would show. If only a proxy is available, say what it cannot establish and leave that part unverified.
   - **Independent critique:** a separate reviewer (a subagent without your conclusions, a different model, or a human expert) can expose blind spots and challenge reasoning. Keep this where useful, but another model's agreement alone does not establish factual accuracy, performance, or user impact. A reviewer who runs a check contributes its evidence, not just a verdict.

## Output

```markdown
### Depth: <task>
Expert: <who> would <do what differently>
Raw material: <…>  Instruments: <…> (planned: <…>; ran: <which and result, or not run>)
Stretch target: <observable target> vs baseline <measured value, or unknown> — what must be true: <…>
Must preserve: <constraints that cannot be traded for the target>
Assumption to re-derive: <assumption> → <held / did not hold with evidence, or not yet tested>
New knowledge to produce: <…>
Validation: <evidence and pass/fail criterion; planned or observed; proxy limits>
Independent critique: <review if useful; what it can and cannot establish>
First probe: <riskiest assumption → smallest test → continue/reconsider result>
Extra effort/cost and user review burden: <estimate or unknown>
Stop or return for a decision when: <budget, constraint, or evidence boundary>
```

## Pitfalls

- **Depth is not length.** Cut anything that is more of the same.
- **Name the instrument, then use it.** During authorized execution, listing SQL but never running a query when the data is reachable is still vocabulary. In a proposal, make the intended query and check concrete without claiming they ran.
- **Agreement is not validation.** Neither "I checked and it looks right" nor another model agreeing proves the claim. Preserve useful critique, but report actual evidence separately.
- **A stretch target is not a blank check.** Stop at the agreed boundary and report an honest miss, the evidence, and the options. Do not weaken a test, sacrifice a constraint, or quietly extend the budget to hit the target.
- **Use the short output for small tasks** as described in `SKILL.md`; do not fill this template just to make the work look deeper.
- **Ask before reaching for data you don't have access to,** or that costs money or touches production.
