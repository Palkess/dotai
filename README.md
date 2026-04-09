# dotai

Personal collection of prompts, templates, and strategies for working effectively
with LLMs in day-to-day development.

Inspired by the dotfiles tradition — these are the AI workflow configs and hard-won
practices I keep coming back to.

## Contents

- **.claude/skills/** — Reusable skill definitions (Claude Code skills); mirrors `~/.claude/skills/`
  - `init-agent-docs` — Generates an AGENTS.md/CLAUDE.md documentation structure
    for a project, including modular reference files for conventions, architecture,
    decisions, and more
  - `a11y-audit` — Runs a WCAG 2.2 AA accessibility audit against a locally hosted
    website using axe-cli, pa11y, or Lighthouse; reports violations grouped by WCAG
    criterion with remediation advice and a prioritized fix list
  - `grill-me` — Interviews you relentlessly about a plan or design, resolving each branch of
    the decision tree one question at a time, until reaching shared understanding.
    - Author credit: https://github.com/mattpocock/skills/tree/main/grill-me
  - `doc-changes` — Updates README(s) and agent docs after a task by diffing tracked changes
    and untracked files, selecting the nearest relevant docs, and writing surgical updates
- **strategies/** — Focused write-ups on getting the most out of LLMs
  - _(more to come)_

## Philosophy

- Prompts should be specific enough to be immediately useful, not generic enough
  to sound impressive. A prompt like "generate documentation for my project" leaves
  too much open to interpretation and produces mediocre results every time. Compare:

  ❌ "Act as a senior software architect and generate comprehensive documentation
  for this project."

  ✅ "Create a decisions.md file using ADR format (Context → Decision → Consequences).
  Date-stamp each entry. Only document decisions not already obvious from the code.
  Cross-reference bugs.md where a decision is the known cause of an issue."

  The second prompt is longer but produces a consistent, useful result across any
  project without needing to be rewritten.

- Strategies should reflect actual experience, not best guesses
- Everything here gets updated when it stops working

## Resources

- [AGENTS.md standard](https://agents.md) — the open standard these prompts are
  built around
- [Claude Code docs](https://docs.claude.ai) — official Claude Code documentation
