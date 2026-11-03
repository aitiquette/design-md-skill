# DESIGN.md format

Write the file with these sections, in this order. Leave a field as "—" rather than inventing content the user didn't give. Keep the token names exactly as shown so files stay consistent across projects.

```markdown
# <Project name> — DESIGN.md

> <One-line summary>

Client: <client>
Last updated: <YYYY-MM-DD>

## 1. Brand
- **Audience:** …
- **Personality:** …
- **Channels:** …
- **Languages:** …
- **Tone of voice:** …

## 2. Color
| Token | Hex | Use |
|---|---|---|
| `--color-primary` | #… | Main actions, links, key brand moments |
| `--color-secondary` | #… | Supporting brand color, secondary surfaces |
| `--color-accent` | #… | Highlights and small details, used sparingly |
| `--color-background` | #… | Page background |
| `--color-surface` | #… | Cards, panels, inputs |
| `--color-text` | #… | Body copy and headings |
| `--color-muted` | #… | Captions, helper text, metadata |
| `--color-border` | #… | Dividers and outlines |
| `--color-success` | #… | Confirmations |
| `--color-warning` | #… | Cautions |
| `--color-error` | #… | Errors and destructive actions |
| `--color-on-primary` | #… | Text and icons placed on Primary (white or Text, whichever contrasts more) |

### Contrast (WCAG 2.2)
| Pair | Ratio | Result |
|---|---|---|
| Text on Background | x.xx:1 | AAA / AA / AA large / Fail |
| Text on Surface | … | … |
| Muted on Background | … | … |
| On-primary on Primary | … | … |
| Primary on Background | … | … |
| Secondary on Surface | … | … |

Thresholds: AAA ≥ 7, AA ≥ 4.5, AA large ≥ 3, otherwise Fail.

## 3. Typography
| Role | Font | Weight |
|---|---|---|
| Headings | <family> (Google Fonts / custom file / system stack) | 700 |
| Body | … | 400 |
| Accent / mono | … | 400 |

- Base size <n> px, scale ratio <r>, body line height <lh>, heading letter spacing <ls> em.
- Google Fonts embed: `https://fonts.googleapis.com/css2?family=…&display=swap`

| Level | Size |
|---|---|
| Display | base × r⁵ |
| H1 | base × r⁴ |
| H2 | base × r³ |
| H3 | base × r² |
| H4 | base × r |
| Body | base |
| Small | base ÷ r |
(Round each to whole px.)

## 4. Layout & shape
- Spacing base unit, density, and the spacing scale (unit × 1, 2, 3, 4, 6, 8, 12, 16).
- Grid columns and max content width.
- Corner radius for cards and for buttons.
- Border width and elevation (with the box-shadow value).

## 5. Components
- Primary button style and shape; one primary button per view.
- Secondary button, inputs and focus ring.
- Icons: set, style, stroke width.
- Motion: duration, easing; respect `prefers-reduced-motion`.

## 6. Logo & imagery
- Logo files, clear space and minimum size.
- Photography and illustration direction; mood board references.

## 7. Rules
**Do** — bullet list
**Don't** — bullet list
Extra notes.

**For AI tools and developers:** use only the tokens below. Don't introduce new colors, fonts, radii or shadows. If something is missing, derive it from the nearest token and flag it.

## 8. Tokens
```css
:root {
  --color-…: …;            /* every color token above */
  --font-heading: "<family>", <fallback>;
  --font-body: …;
  --font-mono: …;
  --font-weight-heading: …;
  --font-weight-body: …;
  --text-display … --text-small: <rem>;
  --line-height-body: …;
  --letter-spacing-heading: …em;
  --space-1 … --space-16: <px>;
  --radius: …px;
  --radius-button: …;
  --border-width: …px;
  --shadow: …;
  --container-max: …px;
  --duration: …ms;
  --easing: …;
}
```
```

Files exported from the interactive builder also end with an HTML comment `<!-- design-md-builder:v1 {json} -->`. Keep it intact when editing such a file by hand, or update the matching fields in the JSON, so the builder can re-import it.
