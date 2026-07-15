# GitHub Product Studio Profile Implementation Plan

> **For Claude:** REQUIRED SUB-SKILL: Use superpowers:executing-plans to implement this plan task-by-task.

**Goal:** Replace the existing profile README with a product-studio showcase, add an automatically refreshed contribution snake, and verify the result on the public GitHub profile.

**Architecture:** The root `README.md` is the profile surface because the public repository name matches the GitHub username. Static Markdown and remote SVG badges provide the visual presentation. A minimal GitHub Actions workflow generates theme-aware snake SVGs on an orphan `output` branch.

**Tech Stack:** GitHub Flavored Markdown, shields.io, readme-typing-svg, GitHub Readme Activity Graph, Platane/snk, GitHub Actions

---

### Task 1: Product-studio profile README

**Files:**
- Modify: `README.md`

**Step 1: Replace the generic introduction**

Create a centered hero for `Hypeboyo`, identify the role as `AI Product Builder`, and use a typing SVG containing these lines:

```text
One-Person AI Product Studio
Shipping Consumer Apps Fast
Turning Ideas Into Real Products
```

**Step 2: Add proof and positioning**

Add follower, star, profile-view, and website badges. Follow with this positioning statement:

```text
AI 소비자 앱을 빠르게 출시하는 1인 프로덕트 스튜디오입니다.
I turn useful ideas into shipped products with AI, automation, and a tight feedback loop.
```

**Step 3: Add verified technology badges**

Use shields for TypeScript, Python, React, React Native, Claude, OpenAI, and Supabase. Do not claim technologies unsupported by the account's repositories.

**Step 4: Add the shipped-products table**

Link `beep-get`, `designlens`, `refable`, and `katalk-link-analyzer`. Each description must explain the user outcome in one sentence and must not invent metrics.

**Step 5: Add live activity and current focus**

Embed the activity graph for `slimex200-wq`, add a theme-aware snake `<picture>` referencing the `output` branch, and add a compact current-focus block.

**Step 6: Validate the Markdown**

Run: `git diff --check && grep -q 'One-Person AI Product Studio' README.md && grep -q 'output/github-contribution-grid-snake-dark.svg' README.md`

Expected: exit code 0 with no whitespace errors and both required profile elements present.

### Task 2: Contribution snake automation

**Files:**
- Create: `.github/workflows/snake.yml`

**Step 1: Add the scheduled workflow**

Use this structure:

```yaml
name: Generate contribution snake

on:
  schedule:
    - cron: "0 0 * * *"
  workflow_dispatch:

permissions:
  contents: write

jobs:
  generate:
    runs-on: ubuntu-latest
    timeout-minutes: 10
    steps:
      - name: Generate light and dark SVGs
        uses: Platane/snk/svg-only@v3
        with:
          github_user_name: ${{ github.repository_owner }}
          outputs: |
            dist/github-contribution-grid-snake.svg
            dist/github-contribution-grid-snake-dark.svg?palette=github-dark
        env:
          GITHUB_TOKEN: ${{ secrets.GITHUB_TOKEN }}
      - name: Publish SVGs to output branch
        uses: crazy-max/ghaction-github-pages@v4
        with:
          build_dir: dist
          branch: output
        env:
          GITHUB_TOKEN: ${{ secrets.GITHUB_TOKEN }}
```

**Step 2: Validate the workflow**

Run: `ruby -e "require 'yaml'; YAML.load_file('.github/workflows/snake.yml'); puts 'valid yaml'"`

Expected: `valid yaml` and exit code 0.

### Task 3: Publish and observe the profile

**Files:**
- Modify: `docs/plans/2026-07-15-github-profile-design.md`
- Create: `docs/plans/2026-07-15-github-profile.md`

**Step 1: Review the complete branch**

Run: `git status --short && git diff --check && git diff --stat origin/main...HEAD`

Expected: only the README, workflow, and two plan documents are changed.

**Step 2: Commit and push the branch**

Run: `git add README.md .github/workflows/snake.yml docs/plans && git commit -m "feat: refresh GitHub product studio profile" && git push -u origin profile/product-studio-readme`

Expected: one scoped commit pushed to the feature branch.

**Step 3: Merge through GitHub**

Create a pull request, verify available checks, merge it, and confirm `main` contains the exact reviewed commit.

**Step 4: Generate and verify the snake**

Run the workflow manually on `main`. Confirm the workflow concludes successfully and that both SVG paths exist on the `output` branch.

**Step 5: Verify the public surface**

Open `https://github.com/slimex200-wq` and confirm the profile README is visible at the top, the hero and badges render, project links are correct, and the contribution visuals load.

**Step 6: Review public repository candidates**

Read the separate private-repository audit. Report candidates and their blockers without changing repository visibility because publication can expose history, secrets, licenses, or personal data.
