# GitHub Product Studio Profile Design

## Goal

Present Hypeboyo as a one-person product studio that rapidly ships AI consumer apps, while giving the profile the visual energy of the Yeachan-Heo reference.

## Direction

Use a product-studio profile rather than a statistics-heavy clone. The top of the README should communicate the positioning within seconds, then prove it with real products. GitHub activity visuals support the story but do not replace it.

## Content Architecture

1. Centered hero with the Hypeboyo name, a concise role, and an animated positioning line.
2. Social-proof badges for followers, stars, profile views, and the studio website.
3. A short studio statement in Korean and English.
4. Technology badges focused on the tools actually visible across the account: TypeScript, Python, React, React Native, Claude, OpenAI, and Supabase.
5. A four-project showcase using stable repository links and concise outcome-oriented descriptions.
6. A live contribution activity graph and a light/dark contribution snake.
7. A compact current-focus block and a branded footer.

## Representative Projects

- `beep-get`: mobile product and shipping work.
- `designlens`: AI design-system extraction and feedback product with a live demo.
- `refable`: reusable AI-agent procedures and orchestration tooling.
- `katalk-link-analyzer`: the account's most-starred public automation project.

`slime-lab` is intentionally omitted until it has a public description. `hby-studio` is linked as the studio destination rather than presented as a product.

## Automation

Add a scheduled and manually dispatchable GitHub Actions workflow using `Platane/snk/svg-only@v3`. It writes light and dark SVGs to an orphan `output` branch with the repository `GITHUB_TOKEN`. The README uses a `<picture>` element so GitHub selects the correct image for the viewer's theme.

## Safety and Resilience

- Do not expose private repository names or personal contact details in the profile README.
- Keep external image providers limited to established README services and provide descriptive alt text.
- Pin the snake action to its supported major release and grant the workflow only `contents: write`.
- If a third-party badge service is unavailable, the text and project links still communicate the profile's core story.

## Validation

- Run `git diff --check` and inspect all generated Markdown and YAML.
- Verify every repository and website link returns successfully.
- Trigger the snake workflow and confirm the `output` branch contains both SVGs.
- After merge, load the public GitHub profile and visually confirm the README appears at the top with rendered images.
- Treat repository pinning as a separate profile-setting action and verify the public profile after applying it.
