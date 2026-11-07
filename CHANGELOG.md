# Changelog

## 0.1.0 — Unreleased

The frontend skill gives an agent rules for front-end code when it builds, changes, reviews or fixes a web front end.

### Added

- **Quality floor.** The agent writes layout code that holds at every width, keeps keyboard focus working, obeys the reduced-motion setting and gives controls accessible names.
- **CSS specificity rules.** The agent keeps selectors flat, puts section spacing in one place and uses the project's tokens, so styles do not cancel each other out.
- **Component and state rules.** The agent keeps one source of truth for each value and fetches server data through one data layer.
- **Browser test rules.** The agent measures narrow widths on the served page, runs browser tests in UTC and takes screenshots only from a fresh build.
