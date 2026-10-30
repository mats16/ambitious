# ambitious

Skills that push work further than it was asked. Based on Felix Rieseberg's essay [How to be more ambitious: a tutorial for humans with models](https://felixrieseberg.com/how-to-be-more-ambitious-a-tutorial-for-humans-with-models/).

There are four ways to ask a model for more. **Speed** (the same work in less time) you get by default. This plugin works the other three as lenses: `ambitious` on the work in front of you, and `ambitious-review` over past work.

| Command | Lens | What it does |
|---|---|---|
| `ambitious` | All three | An "ambitious brief" for the work in front of you: the outcome, the deeper version, a crew, a recommendation, and a first step |
| `ambitious altitude` | The outcome, not the task | Ladders from the task to its outcome, to a durable system that keeps producing it, to a redesigned process; lists the setup that needs (access, data, environments) |
| `ambitious depth` | Work like a top expert | "A deeper version of this task, not a bigger one": the expert's raw material and instruments, an unreasonable target, an assumption re-derived from raw data, new knowledge, and an outside judge |
| `ambitious range` | Borrow from other fields | Nouns to verbs, the fields that do each verb best, and a crew (with an adversary) that does real work on the task |
| `ambitious-review` | All three, over logs | A periodic pass over transcripts, run logs, and git history to find where work stayed small and what to change |

## Install

Claude Code (`/ambitious:ambitious`, `/ambitious:ambitious-review`):

```sh
claude plugin marketplace add mats16/ambitious
claude plugin install ambitious@ambitious
```

Codex (reads the same `.claude-plugin/` manifests; skills appear as `ambitious:ambitious` and `ambitious:ambitious-review`):

```sh
codex plugin marketplace add mats16/ambitious
codex plugin add ambitious@ambitious
```

pi (`/skill:ambitious`, `/skill:ambitious-review`; add `-l` to install for the current project only):

```sh
pi install git:github.com/mats16/ambitious
```

With `-l`, pi reads the package only in a trusted project. Save the trust with `/trust` once in interactive pi before running it from a scheduled task (`pi -p` cannot ask).

## Use

On the task in front of you:

```
/ambitious:ambitious この移行計画をもっと野心的に深掘りして
/ambitious:ambitious depth この見積もりを専門家のやり方で裏付けて
/ambitious:ambitious range この提案書をいろんな分野の目で見て
```

Without a subcommand, the skill picks a single lens when the request clearly asks for one, and runs all three otherwise.

As lenses for a periodic log review (for example from a scheduled job):

```
/ambitious:ambitious-review ~/.claude/projects/<project>/ の直近 7 日の会話を振り返り、結果を reviews/ambitious_<YYYYMMDD>.md に書いて
```

`ambitious-review` only proposes changes (rules, skills, access, checks); it does not apply them or run the proposed probes.

## What a recommendation includes

**Aim boldly, experiment concretely, report honestly. Respect authority, but do not mistake today's methods for the limit.**

- **An outcome beyond the request.** The original task is the floor, not the ceiling. Propose the higher outcome or redesigned process; execute within the authority the user has granted.
- **A hard target and a search for the method.** Treat the target as reachable. After a failed method, learn and try a materially different approach rather than quietly lowering the target. Unknown baselines need measurement, not invented numbers or a smaller ambition.
- **Actual boundaries, not inherited assumptions.** Respect permissions, privacy, and explicit user/project limits. The current API, architecture, workflow, or toolset can be challenged; propose changes and obtain approval where required. Do not claim a broken result is complete.
- **Efficient learning toward the bold goal.** Choose the ambition first, then test its key assumption with the smallest informative experiment. Make the learning step small, not the outcome.
- **Checkpoints that advance the attempt.** Show material extra effort/cost and user review burden. Continue authorized work through learning checkpoints; at an explicit limit or need for new authority, return with evidence and the next experiment or investment that could unlock the target.
- **Validation, separate from critique.** Tests, measurements, held-out data, or observed user behavior support a claim. Independent reviewers find blind spots; another model's agreement alone is not proof. Planned checks and proxy limits stay explicit.

Small tasks get a few lines, not a filled-out report. Scale the crew to the outcome, not a fixed roster or only the cheapest methods. These principles also apply when running one lens alone. A missing estimate is not a reason to invent an approval gate; a proposal-only request still stays a proposal.

Behavioral regression cases and an old/new comparison procedure are in [tests/scenarios.md](tests/scenarios.md). They are an evaluation checklist, not a claim that model behavior has been tested.

## 日本語の概要

記事「How to be more ambitious」の 3 つの方向（Altitude・Depth・Range）を、スキル `ambitious` のサブコマンドにした。サブコマンドを付けなければ 3 つまとめて、付ければその方向だけを見る。ログの振り返りは、スケジュールから呼びやすいよう別のスキル `ambitious-review` にした。

- **altitude** — タスクではなく、その先の結果から考える。繰り返す依頼は、繰り返さない仕組みにする。
- **depth** — 一流の専門家の材料と道具（生データ、DB、統計、シミュレーション）で、大きくではなく深くする。無茶な目標、生データからの裏付け、自分で採点しない外の判定。
- **range** — 名詞を動詞に言い換え、その動詞が得意な分野の役（反対役を含む）に、実際の仕事をさせる。
- **ambitious-review** — 3 つの目でログを定期的に振り返り、仕事が小さく留まったところと、次に大きくするための直しを挙げる。

狙いは大胆に、試行は具体的に、結果は正直に。提案は元の成果物を超えてよいが、実行は与えられた権限の範囲で行う。通常の `ambitious` は選択を返し、事前に実行を任されていれば最初の試行に進む。`ambitious-review` は提案までで、試行も実行しない。

権限・プライバシー・明示された上限は守る。一方、今の API や構成、道具を自動的に限界としない。高い目標を先に置き、実現を左右する前提を小さく試す。最初の失敗では目標を下げず、手法を変える。学習の節目では次の実験へ進み、明示された資源の上限や新しい権限が必要な点では、突破に必要な次の一手を返す。検証と批評は区別し、小さい課題は数行で返す。

## License

MIT
