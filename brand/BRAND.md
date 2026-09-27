# SWAT Lab — Sage & Clay

The visual style of the Social Work and Technology (SWAT) Lab at the NUS School of Social Work, led by Gerard Chung. The lab studies how digital tools can support social workers and the people they serve, while keeping the human side of care at the centre. The style should feel calm, warm, kind and trustworthy: matte, earthy colours, never bright or loud.

Use it for the lab website, gerardchung.com, research apps and tools, slides, posters, reports and charts.

## Voice

- Plain, warm and clear. Short sentences. Explain research in everyday words first, then add the technical term if needed.
- People first: "social workers", "young people", "service users". Technology is the helper, never the hero.
- Do: be specific about what a tool or study does. Don't: hype ("revolutionary", "AI-powered!"), exclamation marks, emoji.
- The lab name is written **SWAT Lab** in running text and **swat:lab** in the logo.

## Colour

Matte and earthy. Linen (`surface`) is the ground almost everywhere; Charcoal (`ink`) is the text.

- `sage-deep` is the one primary colour: buttons, links, active states. Text on it is `on-sage-deep`.
- `sage` is for shapes and illustration (the logo circle, chart fills), not for text.
- `clay` is a small accent only — the colon in the logo, a highlight, one line in a chart. Keep it under about 10% of any layout. Use `clay-text` when clay must be read as text.
- `sage-soft` with `sage-text` for tags and chips.
- Never use bright or saturated colours (no bright orange, yellow, red or electric blue). If a new colour is needed, mix it toward grey and keep it at about the same softness as sage and clay.
- Borders, not shadows: cards are `surface-raised` with a 1px `line` border.

For charts, use this order: `sage-deep`, `clay`, `sage`, `ink`, then `ink-muted`.

## Type

- Headings: **Fraunces** (Google Fonts), weight 500. Warm, a little old-style, friendly.
- Text: **Work Sans** (Google Fonts), 400 for reading, 600 for labels and buttons.
- Sentence case for headings and buttons ("Open project", not "OPEN PROJECT"). Small uppercase with wide letter-spacing only for tiny over-line labels.

## Shape and space

- Soft corners: buttons `radius-md`, cards `radius-lg`, big panels `radius-xl`, tags `radius-pill`.
- Generous space: cards use `space-6` padding, columns `space-8` apart, sections `space-12`.
- Buttons are at least 44px tall. Primary = `sage-deep` fill; secondary = 1.5px `sage-deep` outline on transparent.

## Logo

The mark is a heart inside code brackets `< ♥ >`: care held inside technology. The brackets are `sage-deep` and the heart is `clay`. The wordmark is the mark plus "swat:lab" in Fraunces 500 with a clay colon. See the Logos group for files: the full-colour mark for light grounds, the reverse mark for dark grounds (brackets in light sage, heart in light clay), and the app icon (Linen brackets and a soft clay heart on a `sage-deep` square). Give the logo clear space of at least half its height on every side. Don't recolour, stretch, rotate or add effects.

## Iconography

Simple line icons with a 1.5–2px stroke and rounded ends, in `ink` or `sage-deep`. No filled, glossy or emoji icons.

## Colour values

| Token | Light | Dark | Use |
| --- | --- | --- | --- |
| surface | #F2EFE8 | #23251F | Page background (Linen) |
| surface-raised | #FAF8F3 | #2D302A | Cards, panels |
| line | #DEDAD0 | #3E4238 | 1px borders |
| ink | #2D2F2A | #EEEAE0 | Main text (Charcoal) |
| ink-body | #45483F | #D6D2C6 | Paragraph text |
| ink-muted | #5F625B | #AFAC9F | Captions, labels |
| sage | #8A9A83 | #8A9A83 | Shapes, chart fills (not text) |
| sage-deep | #56654F | #A3B39B | Primary: buttons, links |
| on-sage-deep | #F2EFE8 | #23251F | Text on sage-deep |
| sage-soft | #E4E9E0 | #343B31 | Tag / chip background |
| sage-text | #3F4C3A | #C3CDB9 | Text on sage-soft |
| clay | #B5876E | #C49A82 | Small accent only |
| clay-text | #8E5E48 | #D8B3A0 | Clay as readable text |

## Type scale

Headings (Fraunces 500): display 56/60, h1 40/46, h2 28/34, h3 22/28.
Text (Work Sans): body-lg 18/28, body 16/26, small 14/20, label 13/18 (600).

## Spacing and radius

Spacing: 4, 8, 12, 16, 24, 32, 48 px. Radius: 6 (inputs), 10 (buttons), 16 (cards), 20 (panels), 999 (tags).

## Logo files

In `brand/logos/`: `swatlab-mark` (light grounds), `swatlab-mark-reverse` (dark grounds), `swatlab-app-icon` (favicon, app icon), `swatlab-wordmark` and `swatlab-wordmark-reverse` (mark + "swat:lab"). SVG for the web, PNG for slides and documents.
