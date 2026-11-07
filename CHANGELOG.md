# Changelog

## 0.1.1 — 2026-11-07

### Changed

- **The skill stands alone.** The description and the body name no other skill and link to no issue or pull request. The attribution of the adapted text moved to `NOTICE`.

## 0.1.0 — 2026-11-07

The frontend skill gives an agent rules for front-end code when it builds, changes, reviews or fixes a web front end.

### Added

- **Quality floor.** The agent writes layout code that holds at every width, keeps keyboard focus working, obeys the reduced-motion setting and gives controls accessible names.
- **CSS specificity rules.** The agent keeps selectors flat and puts section spacing in one place, so styles do not cancel each other out.
- **Component and state rules.** The agent keeps one source of truth for each value and fetches server data through one data layer.
- **Browser test rules.** The agent measures narrow widths on the served page, sets the time zone of each browser test, with UTC as the default, and takes screenshots only from a fresh build.
