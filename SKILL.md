---
name: frontend
description: "Rules for front-end code: layout code that holds at every width, keyboard focus and reduced motion in CSS and scripts, CSS specificity, component state, and browser tests and screenshots. Use when building, changing, reviewing or fixing front-end code. Not for how a screen looks, and not for server-side code."
license: Apache-2.0. Complete terms in LICENSE.
metadata:
  version: "0.1.1"
---

# Frontend

Use only the rules that fit the change. Keep existing code in place unless restructuring is the task. A visual brief or an approved design decides how the screen looks. These rules decide how the code delivers it.

## Quality floor

Build to this floor in each change without announcing it.

1. **Layout holds at every width.** Use flex, grid, `min()`, `max()` and `clamp()`. Do not give a page column or a container a fixed pixel width. The page body never scrolls sideways.
2. **Measure narrow widths on the real served page.** A test column or a story frame can be wider than the app shell, so the page can still overflow.
3. **Keyboard focus works.** Show focus with `:focus-visible`. Never remove an outline without a replacement. Keep the tab order the same as the reading order.
4. **Motion obeys `prefers-reduced-motion`.** Put nonessential CSS motion inside `@media (prefers-reduced-motion: no-preference)`. A script reads `matchMedia("(prefers-reduced-motion: reduce)")` before it starts an animation.
5. **Content is accessible to assistive technology.** Give each control an accessible name. Use landmarks and one `h1` for each page. Give an image an `alt` text, or `alt=""` when it is decoration.

## CSS specificity

6. **Keep selectors flat and of equal weight.** Use one class for each rule. Do not mix a type selector such as `.section p` with a class such as `.cta` on the same property. They cancel each other out. This often happens with padding and margin between sections.
7. **Put spacing between sections in one place.** The parent sets the gap with `gap` or one spacing rule. A child does not add outer margin.
8. **Do not use `!important` or IDs for styling.** If a rule loses, find the conflicting selector and fix it. Use `@layer` or the project's scoping method to order styles.

## Components and state

9. **Keep one source of truth for each value.** Derive other values from it while rendering. Do not copy server data into local state.
10. **Fetch server data through the project's one data layer.** Give each response a type. Handle the loading, empty and error results of each request in code.
11. **Keep the URL as the state of the page.** Filters, tabs and selection that a person can share go in the URL.
12. **Let the framework own the DOM.** Do not change elements that a component renders from outside that component.

## Browser tests and screenshots

13. **Find elements as a person does.** Use the role and the accessible name, then the label or text. Use a test id only when nothing else is stable.
14. **Set the time zone of each browser test.** Set `timezoneId` in the browser context and build dates with `Date.UTC`. Use `"UTC"` by default. If the test checks local dates or a daylight-saving change, use the zone that the behaviour needs. A test without a set zone uses the developer's zone, so its result changes.
15. **Take screenshots only from the served page after a fresh build.** Never take them from a stale static folder. Old files show a screen that the code no longer makes.
16. **Wait for a condition, not a time.** Wait for an element, a response or a state. Do not sleep for a fixed time.
