# GitHub Profile Polish Design

## Goal

Make the profile feel like a focused one-person AI product studio instead of a dashboard of badges and activity widgets.

## Direction

Use a brand-first, product-second layout:

1. A compact `Hypeboyo` hero with a single positioning sentence.
2. Three selected products with clear outcomes and one primary link each.
3. A smaller `Labs & tools` section for experimental and derived work.
4. One concise build philosophy line and one contribution visualization.

The hero drops the animated typing banner and vanity counters. GitHub already shows followers and contribution totals around the README, so repeating them adds noise and makes the page slower to settle visually.

## Project framing

- `beep-get`, `designlens`, and `katalk-link-analyzer` are presented as selected original product work.
- `refable` stays visible, but its description explicitly says it is derived from the MIT-licensed `fablize` project and names the original additions.
- `hby-studio` and `ai-threads` stay in the pinned repository grid instead of competing for space in the selected-work table.

## Visual system

- Keep the existing violet accent (`#6C63FF`) for a recognizable brand thread.
- Use plain GitHub Markdown and small flat badges only where they carry meaning.
- Prefer short sentences, generous whitespace, and one activity graphic.
- Keep light and dark theme support for the contribution snake.

## Verification

- Validate Markdown links and image endpoints.
- Confirm the workflow YAML remains unchanged and valid.
- Render the profile on GitHub and verify the hero, selected work, Refable attribution, pinned order, and contribution snake in the live page.
