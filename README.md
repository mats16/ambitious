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

`ambitious-review` only proposes changes (rules, skills, access, checks); it does not apply them.

## 日本語の概要

記事「How to be more ambitious」の 3 つの方向（Altitude・Depth・Range）を、スキル `ambitious` のサブコマンドにした。サブコマンドを付けなければ 3 つまとめて、付ければその方向だけを見る。ログの振り返りは、スケジュールから呼びやすいよう別のスキル `ambitious-review` にした。

- **altitude** — タスクではなく、その先の結果から考える。繰り返す依頼は、繰り返さない仕組みにする。
- **depth** — 一流の専門家の材料と道具（生データ、DB、統計、シミュレーション）で、大きくではなく深くする。無茶な目標、生データからの裏付け、自分で採点しない外の判定。
- **range** — 名詞を動詞に言い換え、その動詞が得意な分野の役（反対役を含む）に、実際の仕事をさせる。
- **ambitious-review** — 3 つの目でログを定期的に振り返り、仕事が小さく留まったところと、次に大きくするための直しを挙げる。

どれも提案までで、勝手に範囲を広げない。

## License

MIT
