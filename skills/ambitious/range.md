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
3. **Assemble a crew of 3–5 roles,** including at least one adversary whose job is to find why this fails. For each role, write the concrete actions they would perform on this work and the artifact each action produces.
4. **Run the crew.** Do the actions, don't imitate the voice. The journalist writes the headline and the first paragraph; the editor cuts a third and says what was lost; the short seller writes the bear case; the forensic accountant ties every number back to its source. For large work, give each role to its own subagent in parallel, with the same model as yours, briefed with the role's actions and the raw work — not your opinion of it.
5. **Merge.** For each role: what changed because of it. Surface conflicts between roles to the user rather than averaging them away.

## Output

```markdown
### Range: <task>
Verbs: <one sentence>
| Role | Field | What they do to this work | Artifact | What changed |
|---|---|---|---|---|
| … | … | … | … | … |
Conflicts for the user: <…>
First step: <…>
```

## Pitfalls

- **Role-play is not range.** "As a journalist, I think this is compelling" adds nothing. If a role produced no artifact and changed nothing, drop it.
- **Pick roles from the verbs, not from a stock list.** A crew that would fit any task is a sign step 1 was skipped.
- **Keep the adversary honest.** The red team gets the same raw material, and its strongest objection goes in front of the user even if it is inconvenient.
