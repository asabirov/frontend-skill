# frontend-skill

An agent skill with rules for front-end code. The agent reads it when it builds, changes, reviews or fixes a web front end.

## Why it exists

The owner wants a robust front-end architecture and code. Agents that build screens make the same code mistakes again: layouts that overflow on a phone, removed focus outlines, CSS rules that cancel each other out, browser tests that depend on the local time zone, screenshots of an old build, and lockfiles that a different npm rewrites. This skill holds the short rules that prevent them.

The skill covers code only. How a screen looks comes from a visual brief or an approved design, which another skill or a person supplies. The skill states no visual rule, so the two cannot conflict.

**What it turned down:**

| Candidate | Why not |
| --- | --- |
| Copying the whole upstream `frontend-design` skill | Most of it is visual direction. A visual skill already covers that. |
| A framework or a stack choice | The rules must hold in React, Svelte, Vue and plain HTML. |
| Size, complexity and duplication limits | A code-size check already holds them. |

## Overlap check

Before the first release, each rule was compared with the other installed skills that touch front-end work. No rule conflicts with or repeats one of their rules.

| Skill | What it covers | How this skill stays apart |
| --- | --- | --- |
| `design` | How a screen looks: reflow at narrow widths, visible focus, reduced motion, states to render, design tokens and native controls | This skill says how code delivers those results, such as `:focus-visible` and the reduced-motion media query. It leaves tokens and native controls to `design`, and says nothing about the look. |
| `backend` | Server modules, API contracts, permission checks | This skill covers browser code only. |
| `code-smells` | Code size, complexity, duplication and imports | This skill sets no size or duplication limit. |
| `agent-browser` | How to drive a browser and take a screenshot | This skill says which page to capture, not how. |
| `run` | How to start the app | This skill only requires a fresh build before a screenshot. |

## What's where

| Path | What it holds |
| --- | --- |
| `SKILL.md` | The rules the agent reads. |
| `README.md` | This page, for people. |
| `CHANGELOG.md` | What changed in each version. |
| `LICENSE` | The Apache License 2.0. |
| `NOTICE` | The attribution for the adapted upstream text. |

## Version

The version source is the quoted `metadata.version` in the frontmatter of `SKILL.md`. Each release has a `vMAJOR.MINOR.PATCH` tag and a GitHub release that match it.

## Install, update, roll back and remove

This repository is private. The owner's configuration repository installs it as a Git submodule at `skills/frontend`, with the authenticated URL `https://github.com/asabirov/frontend-skill.git`. A configuration pull request adds or moves the pin, and only to a released tag commit.

- **Install.** Add the submodule in a configuration pull request. Pin it to a released tag commit. Then run `git submodule update --init --recursive`.
- **Update.** In a configuration pull request, move the pin to the commit of the new tag. Keep the old commit in the pull request text.
- **Roll back.** Move the pin back to the old commit in a configuration pull request.
- **Remove.** Remove the submodule with `git rm skills/frontend` in a configuration pull request.

After each change, check the installed commit with `git -C skills/frontend rev-parse HEAD`. It must be the tag commit.

## Licence

Apache License 2.0. Part of `SKILL.md` adapts the `frontend-design` skill from [anthropics/skills](https://github.com/anthropics/skills). See `NOTICE`.
