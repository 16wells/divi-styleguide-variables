# Divi Variables From Style Guide (Claude Skill)

Generate a **Divi 5 Global Variables** import JSON (`context: "et_builder"`) from:

- a style guide (any prose format), and/or
- design tokens (JSON or a simple table/CSV)

This produces a file you can import into **Divi → Divi Library → Import & Export → Import Global Variables**.

## What’s in this repo

- `divi-variables-from-style-guide/` — the **skill folder** you upload into Claude (contains `SKILL.md` and optional `references/`)

> Note: Anthropic’s skills best practices recommend keeping the skill folder free of `README.md` files. Human docs live at the repo root; the skill folder is optimized for Claude ingestion.

---

## Install

### Install in Claude.ai (detailed)

1. **Get the skill**
   - Clone: `git clone https://github.com/16wells/divi-styleguide-variables.git`
   - Or download the repo as a ZIP from GitHub and extract it.

2. **Zip only the skill folder**
   - On macOS: Right-click `divi-variables-from-style-guide` → **Compress "divi-variables-from-style-guide"**
   - On Windows: Right-click the folder → **Send to → Compressed (zipped) folder**
   - The ZIP must contain the folder contents (e.g. `SKILL.md` and `references/` at the top level of the ZIP). Do **not** zip the whole repo or nest an extra folder.

3. **Upload in Claude**
   - Open [Claude.ai](https://claude.ai) and sign in.
   - Go to **Settings** (gear or profile menu).
   - Open **Capabilities** (or **Skills**, depending on the UI).
   - Click **Upload skill** (or **Add skill**).
   - Select the ZIP you created. Wait for the upload to finish.

4. **Enable the skill**
   - Find **Divi Variables From Style Guide** (or `divi-variables-from-style-guide`) in the list.
   - Turn the skill **on**. It should stay on for your session (or per your account settings).

5. **Verify**
   - Start a new conversation and say: *“I want to convert a style guide into Divi 5 Global Variables JSON.”*
   - Claude should acknowledge the skill and ask for your brand name and style guide (or tokens). If it does, the skill is active.

![Placeholder: Claude.ai Settings > Capabilities/Skills with Upload skill and the skill toggled on](docs/screenshots/install-claude-settings.png)  
*Add a screenshot here: Claude.ai Settings → Capabilities/Skills, showing the upload option and the skill enabled.*

### Install in Claude Code

Place the `divi-variables-from-style-guide/` folder into your Claude Code skills directory (the path shown in your Claude Code settings). No need to zip. Restart or reload Claude Code if the skill doesn’t appear.

---

## How to use

Try prompts like:

- “Convert this style guide into a Divi 5 Global Variables JSON I can import.”
- “Here are our tokens in a table—generate Divi `global_colors` and `global_variables`.”
- “Extract only explicit values from this brand guide and produce Divi variables; list anything missing.”

![Placeholder: Claude chat with a style guide pasted and the skill generating JSON + report](docs/screenshots/example-conversation.png)  
*Add a screenshot here: A Claude conversation with a style guide (or token table) in the message and the skill’s reply showing the JSON block and token report.*

---

## Output you should expect

The skill outputs, in order:

1. **Suggested filename** — e.g. `MyBrand_Global-Variables.json`
2. **Importable JSON** — a single code block you can copy and save as a `.json` file
3. **Token report table** — IDs, labels, values, and types for each variable
4. **Missing/ambiguous checklist** — anything the style guide mentioned but didn’t define with explicit values

![Placeholder: Divi Library Import & Export dialog with Global Variables JSON selected](docs/screenshots/divi-import-dialog.png)  
*Add a screenshot here: Divi → Divi Library → Import & Export, with “Import Global Variables” checked and the generated file selected.*

---

## Screenshots (for maintainers)

To complete the README for public release, add real screenshots to a `docs/screenshots/` folder and replace the placeholders above:

| File | What to capture |
|------|------------------|
| `install-claude-settings.png` | Claude.ai Settings → Capabilities/Skills: upload area and skill toggle on |
| `example-conversation.png` | Claude chat: user message with style guide/tokens + skill reply with JSON and report |
| `divi-import-dialog.png` | Divi WP admin: Divi Library → Import & Export, Global Variables option and file picker |

---

## License

MIT. See [LICENSE](LICENSE) in this repo.

