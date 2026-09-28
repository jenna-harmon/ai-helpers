# Changelog

## Unreleased

- `uxd-research-heuristic-eval`: the specialist-lenses clarifying question now
  goes through the interactive `AskUserQuestion` mechanism (like the framework
  question) instead of free-text prose, and is explicitly non-blocking —
  defaulting to "None" and continuing when unanswered. Previously, prose
  questioning stalled non-interactive/agent callers indefinitely, so the
  evaluation never ran (surfaced by the eval's `avoids_design_recommendations`
  judge failing on the `no-recommendations` case).
- `uxd-research-heuristic-eval`: the Step 4 researcher **review-format**
  question (spreadsheet vs. chat) now routes through `AskUserQuestion` as a
  hard-stop gate, matching the design brief's stated intent
  (`references/human-vs-agent-operation.md`). Previously it was delegated to a
  reference doc and asked as free-text prose, so it was surfaced
  nondeterministically — the skill sometimes presented findings inline without
  offering the format choice, failing the `gates_on_researcher_review` judge on
  the `researcher-gate` case. Since this question only arises in Mode A (a human
  is present; Mode B always carries `--review`), hard-stop-and-wait is safe.
- `uxd-research-heuristic-eval`: ambiguous/incomplete interface input is now
  handled explicitly instead of as an open prose ask — Mode A asks and waits;
  Mode B stops with a clear error (like a missing `--framework`) rather than
  hanging on a question no agent caller can answer. The skill never proceeds on
  incomplete input.

## 1.1.0

- Added `patternfly` meta-plugin — one install gets all PatternFly skills
- Bumped all plugin versions to fix stale cache bug
- Moved `pf-assist` routing agent to the `patternfly` plugin
- Delisted empty plugins (`pf-a11y`, `pf-code-review`) from marketplace
- Cleaned up plugin manifests — removed unused custom fields
