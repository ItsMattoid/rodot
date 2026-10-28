# Rodot

Rodot is an experimental fork of the [Godot Engine](https://github.com/godotengine/godot) exploring a more guided, Roblox Studio-inspired game creation workflow.

## Status

Early planning / repository setup. No promise of feature completeness or compatibility yet.

Current base: Godot `4.7.2-stable`. Engine source is unmodified so far.

## Direction

- A familiar scene-building workflow with practical viewport tools and gizmos
- Customizable shortcuts, panels, inspector, and asset workflows
- Preserve Godot's rendering, scene, resource, and runtime systems wherever practical
- Consider collaborative editing after the local editor workflow is stable

## Build

Follow the official Godot build instructions that match the exact checked-out branch:  
https://docs.godotengine.org/en/stable/contributing/development/compiling/

## Upstream sync

Upstream Godot is tracked as the `upstream` remote. Rodot moves forward by merging upstream stable release tags into `main`, preserving Godot's history:

```sh
git fetch upstream --tags
git switch -c sync/<tag> main
git merge <tag>        # e.g. 4.7.3-stable
```

Resolve conflicts on the sync branch, build and test, then merge it into `main`.

## Relationship to upstream

Rodot is an independent project and is not affiliated with or endorsed by the Godot project or Roblox Corporation. Godot is distributed under the MIT license; retain and comply with applicable upstream license and copyright notices.

## Project guidance

See [`CLAUDE.md`](./CLAUDE.md) for AI-assisted development rules.
