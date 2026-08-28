---
name: spec-implement
description: Implement an approved spec from docs/specs/, delegating the actual coding to the expo-react-native-developer subagent and writing a test per acceptance criterion. Use when the user asks to build/implement a spec, or invokes "/spec-implement".
---

# Spec Implement

Build an `approved` spec from `docs/specs/`, following the workflow documented in `docs/specs/README.md`. This skill orchestrates; it does not write feature code itself.

## Steps

1. **Resolve which spec to implement.** If a slug/path was given, use it. Otherwise, list `docs/specs/*.md` whose frontmatter has `status: approved` and ask the user which one.
2. **Check status.** If the spec's status is `draft`, stop and tell the user it needs to be approved first (via `/spec-new`'s review step, or by manually editing the frontmatter) — don't implement a draft without explicit override from the user.
3. **Mark it in progress.** Edit the spec's frontmatter: `status: in-progress`, `updated: <today>`.
4. **Delegate the coding.** Use the Agent tool with `subagent_type: expo-react-native-developer`. Pass it the spec's Context, Requirements, Acceptance Criteria, and Constraints as the brief, plus these two rules:
   - Implement enough to satisfy every requirement and acceptance criterion.
   - For **each** acceptance criterion, write (or update) an automated test that asserts that specific condition, using the project's existing test setup. If no test framework exists yet in `src/mobile`, set one up first (Expo's standard is `jest-expo`) rather than skipping tests.
5. **Update the spec as work lands.** For each acceptance criterion that now has a passing test, check it off (`- [ ]` → `- [x]`) in `## Acceptance Criteria`. Don't check one off just because the feature code exists — the test must exist and pass.
6. **Finish.** Once every acceptance criterion is checked, set `status: done` and `updated: <today>`. If the subagent gets blocked on something only the user can decide, surface that rather than guessing.

## Non-goals

Don't rewrite or reinterpret the spec's requirements here — if something in the spec is ambiguous or wrong, flag it to the user rather than silently implementing your own interpretation.
