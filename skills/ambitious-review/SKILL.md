---
name: ambitious-review
description: Look back over a body of past work through the three lenses of `ambitious` — altitude (the outcome behind the task), depth (what a top expert would use and check), and range (skills borrowed from other fields) — and find where the work stayed small and what change to the setup would make it bigger next time. Reads logs for a window (conversation transcripts, pi sessions, run logs, git and PR history, rule ledgers; default the last 7 days), writes ranked findings with evidence and proposals to the path the caller gives, and follows up on the previous review. Proposes only; never applies changes. Meant for scheduled tasks; also use when asked 「ログを振り返って」「直近 〇 日の会話を見直して」「ambitious の視点でレビューして」.
---

# Ambitious review: look back over logs through the lenses

Follow the ground rules in `../ambitious/SKILL.md`. The lenses are `../ambitious/altitude.md`, `../ambitious/depth.md`, and `../ambitious/range.md`; read them when a signal below needs more than its row.

Use periodically (daily or weekly), or when asked to look back over a body of work. The question is not "was the work correct" but "where did the work stay small, and what change to the setup would make it bigger next time".

1. **Scope the input.** What logs, and what window (default: the last 7 days). Typical sources: Claude Code transcripts (`~/.claude/projects/<project>/*.jsonl`), pi sessions (`~/.pi/agent/sessions`), `git log` and PR or issue history, job and run logs, rule or correction ledgers. If a previous review exists, read it first.
2. **Read for episodes.** An episode is one request and what followed (corrections, retries, the end state). For large logs, give slices to subagents (same model as yours) and ask for episodes with pointers (file and line, session id, commit, URL), not summaries.
3. **Match against the signals** below. One episode can hit more than one lens.
4. **Write findings,** ranked by leverage (how often it happens × how much bigger the work could have been). Each finding:
   - Evidence: the pointers, and a short quote of what was asked and what came out
   - Lens and signal
   - The bigger version: what the work could have been
   - Proposal: the change that makes it likely next time — a rule or instruction, a skill, tool or data access, a check, a recurring job — with its estimated extra cost and user review burden (or what is unknown)
   - First probe: the smallest test of the proposal's riskiest assumption, the result that would support or challenge it, the constraints to preserve, and the stop/decision boundary. Propose the probe; do not run it or make changes from this review.
   - Confidence: verified in the logs, or inferred. Separate evidence that the episode happened from evidence that the proposed improvement would work; reviewer agreement is not validation.
5. **Follow up on the last review.** Which proposals were adopted, which signals came back anyway, which proposals to drop.
6. **Output.** Write where the caller says (a scheduled prompt should give the path); otherwise reply in the chat. Do not apply changes to rules, settings, or code from a review. Propose them; the user decides.

## Signals

| Lens | Signal in the logs | Likely bigger version |
|---|---|---|
| Altitude | The same kind of fix or request repeats across sessions | A durable workflow that removes the repeat (the "keep it crash-free" version of "fix this crash") |
| Altitude | The user had to ask for the obvious next step right after "done" | Ask "what should happen next" before starting |
| Altitude | Work ended at the artifact; nobody checked the outcome it was for | Close the loop on the outcome (was the decision made, did the metric move) |
| Altitude | Manual steps by the user that the model could do with access | Ask for the access or data feed |
| Depth | Estimates or claims made from vocabulary where data was reachable | Query or measure from the raw material |
| Depth | "Looks good" or model agreement treated as proof, without supporting evidence | Define validation before the work; keep independent critique separate |
| Depth | A target accepted as given when an order of magnitude better was plausible | Name an unreasonable target and plan what would have to be true |
| Depth | A correction the user made that an expert in the field would have caught | The expert's check, built in |
| Depth | A load-bearing assumption never re-derived | Reproduce it from raw data |
| Range | The goal stated as a noun ("a deck", "a report") and built to the noun | Restate as verbs; build to the verbs |
| Range | Reviews always come from the same kind of eye | Add a missing crew role, especially an adversary |
| Range | One method used for jobs that need different ones | Borrow the method from the field that owns that verb |
| Self-efficacy | Asks shrunk or hedged up front; "can't" claimed but never tried; stopped after one failed attempt | Try the hard version first; record what blocked it |

The signals table also works as a checklist for other periodic jobs (for example a job that tidies rules from conversation logs): pass it the table and the finding format above.
