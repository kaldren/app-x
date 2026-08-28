---
name: spec-new
description: Draft a new feature spec by delegating to the spec-writer subagent, which interviews the user and writes docs/specs/<slug>.md. Use when the user asks to write/create a spec, plan out a new feature before building it, or invokes "/spec-new".
---

# Spec New

Delegate spec creation to the `spec-writer` subagent rather than interviewing the user yourself — it's tuned to judge which questions are actually worth asking for a given feature, and owns the full research → interview → draft → approval flow.

## Steps

1. Take the feature name/one-liner from the invocation args, or ask the user for one if none was given.
2. Launch the Agent tool with `subagent_type: spec-writer`, passing the feature request verbatim plus any relevant context already established in this conversation (don't make the subagent re-ask something the user already told you here).
3. Let the subagent run its full flow — research, interview via `AskUserQuestion`, drafting, revision, and approval sign-off. Don't intercept or duplicate its questions.
4. Once it reports back, confirm to the user where the spec landed (`docs/specs/<slug>.md`) and its status.

## Non-goals

Don't do the interview or drafting inline here — that logic lives in `spec-writer` so it stays in one place.
