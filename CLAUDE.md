# app-x

## Spec-driven development

Features are specced before they're built. See `docs/specs/README.md` for the full convention.

- Specs live in `docs/specs/<slug>.md`, one file per feature, with a `status` field (`draft` → `approved` → `in-progress` → `done`) in the frontmatter.
- Use `/spec-new` to draft a spec — it delegates to the `spec-writer` subagent, which decides what's worth asking and interviews you before writing. Use `/spec-implement` to build an approved one.
- Mobile implementation (`src/mobile`) routes through the `expo-react-native-developer` subagent, not ad hoc in the main thread.
- All UI/UX work — design system, screens, components, visual/interaction design, motion, accessibility — routes through the `ux-expert` subagent, not ad hoc in the main thread.
- Every Acceptance Criterion in a spec must have a corresponding automated test before it's checked off.
