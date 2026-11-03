---
name: design-md
description: Create, edit or apply a DESIGN.md design system for a project. Use when the user wants to define a project's colors, fonts, spacing, components, logo and rules, opens the DESIGN.md builder, attaches or mentions a DESIGN.md, or asks for pages, posts, decks or UI that should follow one.
---

# DESIGN.md

A DESIGN.md is one Markdown file per project that records its visual identity: brand brief, color tokens with contrast checks, typography, layout and shape, components, icons and motion, logo and imagery, rules, and a CSS token block. This skill helps the user create one and makes sure later work follows it.

Decide which job the user is asking for, then follow that section.

## 1. Create or edit a DESIGN.md

### Preferred: the interactive builder

`assets/design-md-builder.html` is a self-contained interactive builder: color wheel with harmony suggestions and WCAG contrast checks, Google Fonts picker with a Cyrillic filter and custom font upload, layout and component settings, logo upload with palette extraction, a live preview, and export of the finished DESIGN.md.

- **If an Artifact tool is available:** publish `assets/design-md-builder.html` as the user's own artifact with these capabilities:
  `{"db": {}, "user": {}, "assets": {}, "downloads": true}`
  Projects are stored per person under `data/users/<id>`, so each viewer's projects stay private. Tell the user in one sentence what the page does.
- **If there is no Artifact tool** (for example in a terminal or IDE): copy the file into the user's working folder and tell them to open it in a browser. It runs without Claude and keeps projects in that browser.
- **If the user attaches a DESIGN.md exported from the builder** and wants to keep editing it: open the builder and tell them to use **Import .md**. Every exported file ends with an HTML comment `<!-- design-md-builder:v1 {...} -->` that restores the full project.

### Fallback: write it in chat

If the user prefers not to use the builder, or it cannot run, ask for what is missing in one short round (only what you can't infer):

1. Project name, client, one-line summary, audience
2. Personality (2–3 words) and channels (website, Instagram, LinkedIn…)
3. Brand colors they already have, or a single primary color to build from
4. Fonts they already use, or the feel they want
5. Logo files and any must-follow rules

Then write the file following `references/format.md` exactly. Check every text/background pair with the WCAG 2.2 formula and report the real ratios; never invent them. Deliver it as a file named `DESIGN.md`.

## 2. Apply a DESIGN.md to new work

When a DESIGN.md is attached, sits in the project or repo, or the user says to follow it:

1. Read the whole file before designing anything.
2. Use only its tokens: colors, fonts, weights, type sizes, spacing, radius, borders, shadows, motion. Paste its `:root` CSS block as the base of any web output.
3. Follow the Do / Don't rules and the tone of voice for any copy you write.
4. Respect the contrast table: never use a pair marked "Fail" for text, and use "AA large" pairs only for text 24 px and up (or 19 px bold).
5. Load Google Fonts with the embed URL given in the file. For custom font files, ask the user for the files or fall back to the stated stack.
6. If the work needs something the file doesn't define (a chart palette, a dark theme, a new component), derive it from the nearest tokens and say in one line what you added, so the user can add it to their DESIGN.md.

Do not restate the design system back to the user; just apply it.

## 3. Using it across projects

Suggest this setup when the user works on several clients:

- **claude.ai Projects:** one Project per client, with that client's DESIGN.md in the Project files and a line in the Project instructions such as "Follow DESIGN.md for all visual work."
- **Code repositories:** `DESIGN.md` at the repo root, plus a line in `CLAUDE.md`: "Read DESIGN.md before any UI work and use only its tokens."
