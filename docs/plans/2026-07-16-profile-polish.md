# GitHub Profile Polish Implementation Plan

> **For Claude:** REQUIRED SUB-SKILL: Use superpowers:executing-plans to implement this plan task-by-task.

**Goal:** Refine the Hypeboyo GitHub profile into a concise product-studio portfolio with accurate Refable lineage.

**Architecture:** Replace the current badge-heavy README hierarchy with a compact hero, selected-work table, derived-work disclosure, build principles, and a single activity visual. Keep the existing contribution-snake workflow intact and reorder the six pinned repositories through GitHub's profile UI.

**Tech Stack:** GitHub-flavored Markdown, GitHub Actions, GitHub profile settings

---

### Task 1: Rewrite the profile README

**Files:**
- Modify: `README.md`

**Step 1: Replace the hero**

Remove the typing SVG, follower/star/view badges, and duplicated studio badge. Add a compact brand heading, positioning sentence, and useful navigation links.

**Step 2: Curate selected work**

Feature `beep-get`, `designlens`, and `katalk-link-analyzer`. Move `refable` to `Labs & tools` and describe it as an MIT-licensed `fablize` derivative with original additions.

**Step 3: Simplify activity**

Remove the redundant activity graph and keep the theme-aware contribution snake.

**Step 4: Validate the document**

Run link checks, `git diff --check`, and a structural assertion for the expected headings and attribution text.

**Step 5: Commit**

```bash
git add README.md docs/plans/2026-07-16-profile-polish-design.md docs/plans/2026-07-16-profile-polish.md
git commit -m "polish GitHub product studio profile"
```

### Task 2: Publish and visually verify

**Files:**
- No additional files

**Step 1: Push the isolated branch**

```bash
git push -u origin agent/profile-polish-v2
```

**Step 2: Open and merge a profile-only pull request**

Confirm the PR diff contains only the README and planning documents, then merge after validation.

**Step 3: Reorder pinned repositories**

Set the order to `beep-get`, `designlens`, `katalk-link-analyzer`, `hby-studio`, `refable`, and `ai-threads`.

**Step 4: Perform live QA**

Open the public profile and verify the hero, selected work, Refable attribution, pinned repositories, and contribution snake are visible.
