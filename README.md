# DESIGN.md skill for Claude

Define each project's design system once, then have Claude follow it for every page, social post, deck and app screen.

The skill gives Claude:

- **An interactive builder**: color wheel with palette suggestions and WCAG contrast checks, a Google Fonts picker with a Cyrillic filter, custom font upload, spacing, radius, buttons, icons, logo upload with color extraction, and a live preview.
- **A DESIGN.md export** per project: brand brief, color tokens, typography, layout, components, rules for designers and AI tools, and a ready-to-paste CSS token block.
- **Instructions to apply a DESIGN.md** whenever you attach one or keep one in a project or repo.

## Download

**[⬇ Download design-md.zip](https://github.com/aitiquette/design-md-skill/raw/main/design-md.zip)**

Don't unzip it if you're installing in the Claude app.

## Install in Claude (web, desktop, mobile)

1. Turn on code execution: **Settings → Capabilities → "Code execution and file creation"** (called "Create and edit files" in the newer layout). On Team and Enterprise plans, an owner enables skills under **Organization settings → Plugins & skills → Policy**.
2. Go to **Customize → Skills**.
3. Click **+**, then **Create skill**, then **Upload a skill**, and choose `design-md.zip`.
4. Check that `design-md` is in your list with its toggle on.

Official help: [Use skills in Claude](https://support.claude.com/en/articles/12512180-use-skills-in-claude)

## Install in Claude Code

Copy the `design-md` folder from this repo into `~/.claude/skills/` (all projects) or `.claude/skills/` inside a repository (that project only), then start a new session.

```bash
git clone https://github.com/aitiquette/design-md-skill.git
cp -r design-md-skill/design-md ~/.claude/skills/
```

## Use it

Start a new chat and ask in plain words:

- "Open the DESIGN.md builder."
- "Create a DESIGN.md for my bakery client. Ask me what you need."
- "Use the attached DESIGN.md and build a landing page for the spring campaign."
- "Make five Instagram carousel slides that follow our DESIGN.md."

To keep a design system for a client across chats, create a Claude Project, add the DESIGN.md to its files, and add "Follow DESIGN.md for all visual work." to the Project instructions. In a code repository, put `DESIGN.md` at the root.

## Use the builder without Claude

Download [`builder.html`](builder.html) and open it in any browser. Projects are saved in that browser; use **Download .md** to keep your files and **Import .md** to edit them again.

## What's in this repo

| Path | What it is |
|---|---|
| `design-md.zip` | The packaged skill, ready to upload to Claude |
| `design-md/SKILL.md` | The skill's instructions |
| `design-md/references/format.md` | The DESIGN.md file format |
| `design-md/assets/design-md-builder.html` | The interactive builder |
| `builder.html` | A copy of the builder to open directly in a browser |

## License

MIT. See [LICENSE](LICENSE).
