# CLAUDE.md

Guidance for Claude Code when working in this repository.

## What this is

The **SWAT Lab** (Social Work and Technology Lab) website — a static
[Quarto](https://quarto.org) website. It is a plain, hand-styled site: no
Bootstrap theme (`theme: none`), all styling lives in `style.css`.

## Build, preview, deploy

- **Render the whole site:** `quarto render` → output goes to `_site/`
- **Render one page:** `quarto render opportunities.qmd`
- **Go live:** the site is hosted on **Netlify**, but it is NOT linked to
  GitHub — pushing to `main` does not deploy. Deploy = `quarto render`, then
  `quarto publish netlify --no-prompt --no-browser --no-render` (site id in
  `_publish.yml`). Also commit and push to `main` to keep the repo in sync.
- There should normally be only one branch (`main`).

## Structure

| File / folder        | What it is                                             |
|----------------------|--------------------------------------------------------|
| `index.qmd`          | Home page                                              |
| `people/index.qmd`   | People / team page                                     |
| `research.qmd`       | Research page — project themes with APA publication lists |
| `opportunities.qmd`  | "Join Us" — job / project opportunity cards            |
| `contact.qmd`        | Contact page (uses Quarto's `about` template)          |
| `style.css`          | **All** site styling (colors, nav, cards, callouts)    |
| `_quarto.yml`        | Site + navbar config                                   |
| `images/`            | Site images                                            |
| `brand/`             | Brand kit: `BRAND.md`, `tokens.json`, `logos/`          |
| `_brand.yml`         | Quarto brand config (colours, fonts, logos)            |
| `_nav-logo.md`       | Shared nav logo (inline SVG), included on every page   |
| `_site/`             | Rendered HTML output (generated — don't edit by hand)  |
| `old/`               | Archived old page(s), not linked in nav                |

### Conventions

- **Navigation** is a hand-built `.custom-nav` block at the top of each page
  (not Quarto's navbar, since `theme: none`). When adding a page, add its link
  to the `.custom-nav` on **every** page. Current links: Home, People, Research, Join Us.
- **Colors** come from the "Sage & Clay" brand tokens as CSS variables in
  `style.css` (`:root`), e.g. `--sage-deep` `#56654F` (links, primary),
  `--clay` `#B5876E` (small accent), `--surface` `#F2EFE8` (background).
  Reuse these variables rather than hard-coding colors. See "Design and
  branding" at the end of this file.
- **Logo in the nav:** each page's `.custom-nav` starts with
  `{{< include _nav-logo.md >}}` (`../_nav-logo.md` from `people/`), which
  inlines `brand/logos/swatlab-wordmark.svg` so it can use the Fraunces font.
- Emoji/HTML entities like `&amp;` are fine inside the raw `<ul>` blocks.

## Adding a job / project opportunity card

Cards live in `opportunities.qmd` inside the `::: {.opp-grid}` block. They lay
out two-per-row on desktop, one column on mobile.

### IMPORTANT — always ask these questions first

When the user wants to add an opportunity, **ask them these three prompts** and
wait for answers before writing the card. Do not invent content or reorder the
requirement lines.

1. **Title of the project?**
2. **What is the project about?** (1–2 sentence description)
3. **Who are you looking for / what's involved?** — this fills the three ✅
   lines, one per question, **in this exact order**:
   - ✅ **What kind of work?** (e.g. "Research and Admin", "Qualitative &
     quantitative text analysis, data annotation, writing")
   - ✅ **Who are we looking for?** (e.g. "NUS Students", or a combined line
     like "Researchers, NUS Students & Graduate Students")
   - ✅ **How much time is involved?** (e.g. "2–3 hours a week for a semester")

**Do NOT ask about the status pill.** Every card always uses `Recruiting` —
this is a job-opportunity page, so recruiting is a given. Include the
`[Recruiting]{.opp-status}` line automatically.

Rules for the ✅ lines:
- **One ✅ per question.** If several audiences answer "who," put them on a
  **single** line joined with commas / `&amp;` — do **not** split them into
  separate ✅ points.
- Keep the order: **work → who → time**.

### Card template

```markdown
::: {.opp-card}
[Recruiting]{.opp-status}

### <PROJECT TITLE>

<1–2 sentence description of what the project is about>

<ul class="opp-reqs">
  <li><span class="check">✔</span> <what kind of work?></li>
  <li><span class="check">✔</span> <who are we looking for?></li>
  <li><span class="check">✔</span> <how much time is involved?></li>
</ul>
:::
```

Insert the new card as another `::: {.opp-card}` block inside `::: {.opp-grid}`.

### Related styling (in `style.css`)

- `.opp-grid` / `.opp-card` — the card grid and card box
- `.opp-status` — the "Recruiting" pill
- `.opp-reqs` + `.check` — the ✅ requirement list (green check circles)
- `.opp-note` — the stand-out callout box near the top of the page (used for
  the "also open for honours thesis / final year project" note)

## After making changes

1. `quarto render` (or render the single page you changed)
2. Show/verify the result if useful
3. Commit and push to `main` only when the user asks to publish

# Design and branding

This site and any apps made from this folder use the SWAT Lab "Sage & Clay" style.

- Before any visual work (pages, components, apps, logos, charts, slides), read `brand/BRAND.md`.
- Use only the colours in `brand/BRAND.md` / `brand/tokens.json`. Matte and earthy. Never add bright or saturated colours (no bright orange, yellow, red or electric blue).
- Fonts: Fraunces (headings, weight 500) and Work Sans (text), from Google Fonts.
- Logos are in `brand/logos/`. Use them as they are: never redraw, recolour or stretch them. Use the `-reverse` versions on dark backgrounds.
- Quarto picks up colours, fonts and logos from `_brand.yml`. If the site also has a custom `.scss` theme, keep it consistent with `_brand.yml` rather than overriding it.
- Borders, not shadows. Soft corners. Buttons at least 44px tall. Sentence case for headings and buttons.
- For R charts, use this colour order: #56654F, #B5876E, #8A9A83, #2D2F2A, #5F625B.
- Note for this site: because it uses `theme: none`, Quarto does not apply the
  colours and fonts from `_brand.yml` automatically. They are set by hand in
  `style.css` — keep the two in sync if the brand changes.
