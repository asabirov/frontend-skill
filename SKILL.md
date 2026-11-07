---
name: frontend
description: "Rules for front-end code: layout code that holds at every width, keyboard focus and reduced motion in CSS and scripts, CSS specificity, component state, and browser tests and screenshots. Use when building, changing, reviewing or fixing front-end code. Not for how a screen looks, which the `design` skill covers, and not for server-side code."
license: Apache-2.0. Complete terms in LICENSE.
metadata:
  version: "0.1.0"
---

# Frontend

Use only the rules that fit the change. Keep existing code in place unless restructuring is the task. A visual brief or an approved design decides how the screen looks. These rules decide how the code delivers it.

## Quality floor

Build to this floor in each change without announcing it.

1. **Layout holds at every width.** Use flex, grid, `min()`, `max()` and `clamp()`. Do not give a page column or a container a fixed pixel width. The page body never scrolls sideways.
2. **Measure narrow widths on the real served page.** A test column or a story frame can be wider than the app shell, so the page can still overflow. ([source](https://github.com/asabirov/frontend-skill/issues/1))
3. **Keyboard focus works.** Use the native element for its job: `button`, `a`, `input`, `select`. Show focus with `:focus-visible`. Never remove an outline without a replacement. Keep the tab order the same as the reading order.
4. **Motion obeys `prefers-reduced-motion`.** Put nonessential CSS motion inside `@media (prefers-reduced-motion: no-preference)`. A script reads `matchMedia("(prefers-reduced-motion: reduce)")` before it starts an animation.
5. **Content is accessible to assistive technology.** Give each control an accessible name. Use landmarks and one `h1` for each page. Give an image an `alt` text, or `alt=""` when it is decoration.

## CSS specificity

6. **Keep selectors flat and of equal weight.** Use one class for each rule. Do not mix a type selector such as `.section p` with a class such as `.cta` on the same property. They cancel each other out. This often happens with padding and margin between sections.
7. **Put spacing between sections in one place.** The parent sets the gap with `gap` or one spacing rule. A child does not add outer margin.
8. **Do not use `!important` or IDs for styling.** If a rule loses, find the conflicting selector and fix it. Use `@layer` or the project's scoping method to order styles.
9. **Use the project's tokens.** Take colours, spacing, type sizes and radii from CSS custom properties or the project's theme. Do not hard-code a value that a token holds.

## Components and state

10. **Keep one source of truth for each value.** Derive other values from it while rendering. Do not copy server data into local state.
11. **Fetch server data through the project's one data layer.** Give each response a type. Handle the loading, empty and error results of each request in code.
12. **Keep the URL as the state of the page.** Filters, tabs and selection that a person can share go in the URL.
13. **Let the framework own the DOM.** Do not change elements that a component renders from outside that component.

## Browser tests and screenshots

14. **Find elements as a person does.** Use the role and the accessible name, then the label or text. Use a test id only when nothing else is stable.
15. **Make browser tests use UTC dates.** Build dates with `Date.UTC` and set `timezoneId: "UTC"` in the browser context. The developer's browser does not run at UTC, so local dates change the result. ([source](https://github.com/asabirov/amberstone/pull/2955))
16. **Take screenshots only from the served page after a fresh build.** Never take them from a stale static folder. Old files show a screen that the code no longer makes. ([source](https://github.com/asabirov/frontend-skill/issues/1))
17. **Wait for a condition, not a time.** Wait for an element, a response or a state. Do not sleep for a fixed time.

## Attribution

Rules 1, 3, 4, 5 and 6 adapt the quality floor and the CSS specificity advice of the `frontend-design` skill in [anthropics/skills](https://github.com/anthropics/skills/tree/41bbe19d1a1a7eaab5e7bb9050a417e5c6cffc8f/skills/frontend-design), under the Apache License 2.0. This file changes and extends that text.
