# Rodot — Claude Code Project Instructions

## Project mission

Rodot is an experimental game-creation editor built by customizing a fork of the Godot Engine. Its goal is to make scene creation and game development feel approachable and workflow-driven like Roblox Studio, while preserving Godot's proven engine systems wherever practical.

Rodot is **not affiliated with or endorsed by Roblox Corporation or the Godot project**. Treat “Roblox Studio-like” as a product/workflow reference, not permission to copy proprietary assets, branding, or source code.

## Current priorities

Work in small, buildable increments, in this order:

1. Establish a reproducible, clean Godot fork and build environment.
2. Learn the existing editor architecture before changing it.
3. Improve editor usability: layout, panels, shortcuts, selection, viewport navigation, transform gizmos, snapping, inspector, and asset workflows.
4. Add Rodot-specific behavior through editor plugins or isolated modules when practical.
5. Design editing operations and undo/redo with future collaboration in mind.
6. Only then prototype multi-user collaboration.

Do not implement Team Create-style networking until the local editor workflow is stable and the collaboration requirements have been explicitly scoped.

## Engineering rules

- Inspect the repository, current branch, Godot version, build instructions, and relevant code before editing.
- Prefer the smallest change that solves the stated task.
- Preserve upstream Godot behavior unless a change is intentional, documented, and tested.
- Prefer editor plugins and existing extension points over core modifications when they can meet the requirement.
- If a core change is necessary, isolate it, explain why, and keep the patch easy to rebase.
- Do not perform broad refactors, mass formatting, or unrelated cleanup.
- Never overwrite or discard user changes. Check `git status` before operations that could affect working files.
- Do not run destructive Git commands (including `reset --hard`, `clean -fd`, forced checkout, or force-push) unless the user explicitly authorizes the exact action.
- Do not rewrite public/shared Git history without explicit authorization.
- Do not commit, push, create releases, or change repository visibility unless asked.
- Do not invent APIs, paths, build targets, test results, or successful outcomes. Verify them in the checkout or official documentation.
- Do not add dependencies without explaining the reason and trade-offs.
- Keep secrets, access tokens, credentials, and private project data out of source control and logs.

## Before coding

1. Summarize the intended change and identify the likely files/subsystems.
2. Inspect the relevant implementation and adjacent tests.
3. State any meaningful uncertainty or risk.
4. Make the change in a focused patch.
5. Run the narrowest relevant checks, then broader checks if practical.
6. Report exactly what changed, what was tested, results, and any remaining limitations.

For small, obvious changes, keep this process concise; do not create unnecessary ceremony.

## Godot-specific guidance

- Treat the checked-out Godot source and its matching documentation as the source of truth. APIs and build instructions can vary by version.
- Do not assume editor plugin APIs can replace every desired behavior; verify the available extension points.
- For UI, shortcuts, viewport interactions, gizmos, inspector behavior, and scene-tree behavior, identify whether the feature belongs in an editor plugin, editor module, or core editor code before choosing an implementation.
- Avoid changing engine runtime behavior to solve an editor-only problem.
- Preserve platform portability and Godot's existing coding conventions.
- Follow the repository's contribution guidelines, formatting rules, and test/build procedures.
- Do not copy Roblox proprietary code, assets, icons, or branding. Use original Rodot design and assets.

## Future collaboration principles

Collaboration is a later milestone, but new editor architecture should avoid making it unnecessarily difficult:

- Use stable identities for editable objects where the existing scene model permits it.
- Keep edits expressible as discrete, validated operations when practical.
- Preserve undo/redo semantics and distinguish local UI state from project state.
- Consider reconnect/replay, operation ordering, conflict handling, permissions, and persistence before implementing a network protocol.
- Do not assume a simple file sync or broadcasting complete scene files is sufficient for simultaneous editing.
- Do not introduce a CRDT, database, networking stack, or collaboration service before the requirements justify it.

## Definition of done

A task is complete only when:

- The change is focused and consistent with the existing architecture.
- Relevant tests, build checks, or manual verification steps have been run where feasible.
- Any unrun checks are clearly disclosed.
- No unrelated files or user changes were modified.
- The final response explains behavior, changed areas, verification, and known limitations.

## Working style

Be direct, pragmatic, and honest. Prefer a working, maintainable vertical slice over speculative architecture. If a request is ambiguous or could cause significant destructive changes, ask one targeted question before proceeding. When multiple approaches are viable, recommend one and briefly explain the trade-off.
