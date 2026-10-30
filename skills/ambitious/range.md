# Range: borrow from other fields

Most tasks arrive as nouns: a deck, a report, a dashboard, a fix. Nouns hide the skills the work needs. Verbs reveal them, and point to the fields that are best at each verb. (The nouns-to-verbs move is from Tom Kelley's *The Art of Innovation*.)

Example: a quarterly business review is not "a deck". It is "getting busy people to believe a story about cause and effect, and to decide under uncertainty, in 30 minutes". That sentence calls for an analyst, a journalist, and an editor — and, to attack it, a short seller and a forensic accountant.

## Steps

1. **Nouns to verbs.** Rewrite the deliverable as one sentence of verbs: what it must get done, for whom, under what constraint (time, attention, risk).
2. **Fields per verb.** For each verb, which fields do it best? Some starting points:
   - Persuade fast → journalists (headline, lede), trial lawyers (theory of the case)
   - Decide under uncertainty → forecasters, intelligence analysts, poker players
   - Find what is wrong → short sellers, forensic accountants, safety investigators, security red teams
   - Make it clear → editors, information designers, teachers
   - Make it hold up in use → operators, SREs, support staff who take the calls
3. **Assemble only the crew the work needs,** including an adversarial check for why this fails. Do not fill a fixed roster: for small work, perform the useful actions inline. For each role retained, write the concrete actions they would perform, the artifact each action produces, and what distinct method or hypothesis it brings. Choose the crew for the best outcome, not just the cheapest review.
4. **Run the crew when execution is authorized.** For a proposal-only request, describe the actions and expected artifacts without performing them. When executing, do the actions, don't imitate the voice. The journalist writes the headline and the first paragraph; the editor cuts a third and says what was lost; the short seller writes the bear case; the forensic accountant ties every number back to its source. For large work, use parallel subagents for genuinely independent actions that bring distinct methods or test competing hypotheses. Scale the effort to the outcome; do not require a known payoff before trying an unfamiliar but well-motivated field. Use the same model as yours, briefed with the role's actions and the raw work — not your opinion of it. Agreement among the crew is critique, not proof; validate factual or performance claims with evidence as described in `depth.md`.
5. **Merge.** For each role: what changed because of it. Surface conflicts between roles to the user rather than averaging them away.

## Output

```markdown
### Range: <task>
Verbs: <one sentence>
| Role | Field | What they do to this work | Artifact | What changed |
|---|---|---|---|---|
| … | … | … | … | … |
Conflicts for the user: <…>
First probe: <riskiest assumption → smallest test → continue/reconsider result>
Material effort/cost and user review burden: <estimate or unknown>
Actual boundaries / assumptions to challenge: <explicit limits vs current choices>
Next checkpoint: <what changed, what to try next, and any new authority needed>
```

## Pitfalls

- **Role-play is not range.** "As a journalist, I think this is compelling" adds nothing. If a role produced no artifact and changed nothing, drop it.
- **Pick roles from the verbs, not from a stock list.** A crew that would fit any task is a sign step 1 was skipped.
- **Keep the adversary honest.** The red team gets the same raw material, and its strongest objection goes in front of the user even if it is inconvenient.
- **Use the short output for small tasks** as described in `SKILL.md`; more roles, agents, or review rounds are not evidence of better work.
