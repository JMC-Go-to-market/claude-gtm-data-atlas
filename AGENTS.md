<!-- jmc-shared:start (synced from JMC-Go-to-market/.github agents/shared.md; edit there, not here) -->
## How we work at JMC (every repo, every agent, every person)

This block is the same in every JMC-Go-to-market repo. It applies to Claude Code, Codex and any other harness, on any machine. Repo-specific rules follow below it.

**The queue is GitHub issues** on the org board **JMC Work** (https://github.com/orgs/JMC-Go-to-market/projects/1). Work lives there, not in handoff files, local notes or chat. Open issues with `gh issue create --project "JMC Work"`; only five repos add new issues to the board automatically. `--project` needs the `project` scope on your gh token (`gh auth refresh -s project`, once per machine).
1. Before starting, find or open the issue for the outcome. Comment `Claimed: <harness> / <session> / <machine>, branch <name>`. If someone else claimed it in the last 48 hours, pick other work or ask on the issue.
2. Every PR body names its issue and its author. The `issue-ref` check reads both:
   - `Closes #N` (same repo) or `Refs JMC-Go-to-market/<repo>#N` (another repo)
   - `Agent: <harness> / <session> / <machine>` (a person writes `Agent: human / <name>`)
3. Progress, findings and handoffs go as comments on the issue. Never write a new handoff, resume or prompt file.
4. A decision that needs Jay (scope, money, public words he owns, anything irreversible) is an issue in `JMC-Go-to-market/jmc-architecture` labelled `jay-decision`. It holds one question, the options, what each answer triggers, and links. Sessions ask Jay one decision at a time in chat. Write his answer back on the issue and close it.
5. Found something out of scope? Open an issue for it and keep going.

**Shipping**
- Start from a fresh worktree off `origin/main`. Remove it once the PR merges.
- Push branches to the org repo itself. Never fork into a personal account (tgd-ai or anyone's): personal accounts own no repos.
- Several sessions share machines and repos. Never `git add -A`, never reset or stash work you did not make, and never touch another session's checkout.
- Open every PR as a draft (`gh pr create --draft`) and run the repo's tests locally while you work. Mark it ready (`gh pr ready`) once, when it is done: the long test suites and CodeQL skip drafts, and every push to a ready PR re-runs them. Actions minutes are a hard monthly budget for the whole org.
- Merge one PR at a time, on green CI. Vercel builds one at a time across the team, so wait for the production deploy before the next merge. Verify on production before calling anything done.

**What we say (all public copy)**
- Never type a price, plan or term into copy. Read it from the offer source (`ADVISORY_PRICING` and the like). Prices are USD.
- JMC sells the Operator Pass (annual) and Build advisory. Build has no minimum term, and the fee runs until the client's team passes the handover test. No client caps or seat scarcity.
- Office hours are WEEKLY and included with Operator Pass (Jay 10-27). Never name a day or time, never 'with Jay'. Never promise a send cadence for emails.
- No unsourced statistics. No invented names. Public copy gets a fresh-context review before merge. Jay's own words on jaymount.com need his OK.

**Models** (Jay 2026-10-27; applies to every person and agent. Details: `jmc-architecture/docs/model-policy.md`, catalog and shortlists: `jmc-research/models/`)
1. Embeddings are Voyage, called direct, always.
2. Code or Jev first for classification, scoring and yes/no.
3. Everything else: shortlist 3+ candidates from the catalog, eval each, take the cheapest that meets the bar, and record the decision.
4. Buy direct, OpenRouter last.
5. Spread production across providers.
6. Check spend headroom before batches.
- Code: model calls, embeddings, gold, splits and evals use the shared packages in `jmc-packages` (`model-client`, `eval-core`, `openrouter-policy`, `decision-routing`), vendored with its `vendor-sync` script; never copy that code. Claude Code: skill `jmc-packages/skills/jmc-model-lab`. How-to: `jmc-architecture/docs/how-we-pick-and-train-models.md`.

**Secrets**
- Keys live in the vault: `jmc-key`, and `run-with <project> -- <cmd>` per command. Never print a value, never export keys globally, never use the macOS Keychain.
<!-- jmc-shared:end -->
