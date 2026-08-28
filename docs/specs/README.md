# Specs

This folder holds one Markdown file per feature: `docs/specs/<kebab-case-slug>.md`. No per-feature subfolders, no separate plan/tasks/research files — everything about a feature lives in its one spec file.

## Status

Each spec has a `status` field in its frontmatter:

- `draft` — being written or reviewed, not yet ready to build.
- `approved` — reviewed and ready to implement.
- `in-progress` — implementation underway.
- `done` — all acceptance criteria met and verified by passing tests.
- `abandoned` — dropped before completion.

## Workflow

- `/spec-new` — delegates to the `spec-writer` subagent, which researches, asks whatever clarifying questions actually matter for the feature, and drafts a new spec file.
- `/spec-implement` — implements an `approved` spec, delegating the coding to the `expo-react-native-developer` subagent.

Each Acceptance Criterion in a spec becomes an automated test during implementation, so write criteria as concrete, checkable conditions rather than vague goals.
