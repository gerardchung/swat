# CLAUDE.md

Guidance for Claude Code when working in this repository.

## What this is

The **SWAT Lab** (Social Work and Technology Lab) website — a static
[Quarto](https://quarto.org) website. It is a plain, hand-styled site: no
Bootstrap theme (`theme: none`), all styling lives in `style.css`.

## Build, preview, deploy

- **Render the whole site:** `quarto render` → output goes to `_site/`
- **Render one page:** `quarto render opportunities.qmd`
- **Go live:** the site is hosted on **Netlify**. Deploy = `quarto render`,
  then commit and **push to `main`**. Netlify redeploys from `main`.
- `main` is the live site. There should normally be only one branch (`main`).

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
| `_site/`             | Rendered HTML output (generated — don't edit by hand)  |
| `old/`               | Archived old page(s), not linked in nav                |

### Conventions

- **Navigation** is a hand-built `.custom-nav` block at the top of each page
  (not Quarto's navbar, since `theme: none`). When adding a page, add its link
  to the `.custom-nav` on **every** page. Current links: Home, People, Research, Join Us.
- **Colors** come from CSS variables in `style.css` (`:root`):
  `--accent` = logo orange `#F16A37`, `--accent-secondary` = logo green `#8BA330`.
  Reuse these variables rather than hard-coding colors.
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
