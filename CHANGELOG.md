# Changelog

## Unreleased

- `uxd-research-heuristic-eval`: the specialist-lenses clarifying question now
  goes through the interactive `AskUserQuestion` mechanism (like the framework
  question) instead of free-text prose, and is explicitly non-blocking —
  defaulting to "None" and continuing when unanswered. Previously, prose
  questioning stalled non-interactive/agent callers indefinitely, so the
  evaluation never ran (surfaced by the eval's `avoids_design_recommendations`
  judge failing on the `no-recommendations` case).

## 1.1.0

- Added `patternfly` meta-plugin — one install gets all PatternFly skills
- Bumped all plugin versions to fix stale cache bug
- Moved `pf-assist` routing agent to the `patternfly` plugin
- Delisted empty plugins (`pf-a11y`, `pf-code-review`) from marketplace
- Cleaned up plugin manifests — removed unused custom fields
