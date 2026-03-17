# Divi Variables From Style Guide (Claude Skill)

**Canonical repo:** [github.com/16wells/divi-styleguide-variables](https://github.com/16wells/divi-styleguide-variables)

Generate a **Divi 5 Global Variables** import JSON (`context: "et_builder"`) from:

- a style guide (any prose format), and/or
- design tokens (JSON or a simple table/CSV)

This produces a file you can import into **Divi → Divi Library → Import & Export → Import Global Variables**.

## What’s in this repo

- `SKILL.md` — the skill definition (this repo is structured so the **repo root is uploadable**)
- `references/` — optional helper files referenced by `SKILL.md`
- `docs/screenshots/` — optional README images

---

## Install

### Install in Claude.ai (detailed)

1. **Get the skill**
   - Clone: `git clone https://github.com/16wells/divi-styleguide-variables.git`
   - Or download the repo as a ZIP from GitHub and extract it.

2. **Upload in Claude**
   - Open [Claude.ai](https://claude.ai) and sign in.
   - Go to **Settings** (gear or profile menu).
   - Open **Capabilities** (or **Skills**, depending on the UI).
   - Click **Upload skill** (or **Add skill**).
   - Select the extracted folder (it will typically be named like `divi-styleguide-variables-main/` and must contain `SKILL.md` at its top level). Wait for the upload to finish.

3. **Enable the skill**
   - Find **Divi Variables From Style Guide** (or `divi-variables-from-style-guide`) in the list.
   - Turn the skill **on**. It should stay on for your session (or per your account settings).

4. **Verify**
   - Start a new conversation and say: *“I want to convert a style guide into Divi 5 Global Variables JSON.”*
   - Claude should acknowledge the skill and ask for your brand name and style guide (or tokens). If it does, the skill is active.

### Install in Claude Code

Place this repo folder (the one containing `SKILL.md`) into your Claude Code skills directory (the path shown in your Claude Code settings). Restart or reload Claude Code if the skill doesn’t appear.

---

## How to use

Try prompts like:

- “Convert this style guide into a Divi 5 Global Variables JSON I can import.”
- “Here are our tokens in a table—generate Divi `global_colors` and `global_variables`.”
- “Extract only explicit values from this brand guide and produce Divi variables; list anything missing.”

---

## Output you should expect

The skill outputs, in order:

1. **Suggested filename** — e.g. `MyBrand_Global-Variables.json`
2. **Importable JSON** — a single code block you can copy and save as a `.json` file
3. **Token report table** — IDs, labels, values, and types for each variable
4. **Missing/ambiguous checklist** — anything the style guide mentioned but didn’t define with explicit values

---

### Optional: Screenshots

You can add screenshots to `docs/screenshots/` to illustrate install and usage:

| File | What to capture |
|------|------------------|
| `install-claude-settings.png` | Claude.ai Settings → Capabilities/Skills: upload area and skill toggle on |
| `example-conversation.png` | Claude chat: user message with style guide/tokens + skill reply with JSON and report |
| `divi-import-dialog.png` | Divi WP admin: Divi Library → Import & Export, Global Variables option and file picker |

See `docs/screenshots/README.md` in this repo for details.

---

## License

MIT. See [LICENSE](LICENSE) in this repo.

