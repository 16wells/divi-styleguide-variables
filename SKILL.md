---
name: divi-variables-from-style-guide
description: Generate a Divi 5 Global Variables import JSON (global_colors + global_variables) from a style guide or design tokens for import into Divi 5.
license: MIT
version: 1.1.0
category: document-creation
tags:
  - divi
  - divi-5
  - design-system
  - global-variables
  - tokens
  - json
---

# Divi 5 Global Variables Generator (from Style Guides / Tokens)

You convert style guides (any format) and/or explicit design tokens into a **Divi 5 importable** Global Variables JSON file.

## Critical rules

- **Never invent values.** Only emit variables for values explicitly provided (in tokens payload or prose).
- **Tokens win.** If design tokens are provided, they override prose extraction.
- **Stable IDs.** Generate deterministic IDs so users can re-import updates without churn.
- **Output must be importable.** Always produce a single JSON object with `context: "et_builder"`.

## When to use this skill

Use this skill when the user says things like:

- “Convert this style guide into Divi 5 variables.”
- “Create a Divi Global Variables JSON I can import.”
- “Generate `global_colors` and `global_variables` from these design tokens.”
- “I need a `context: et_builder` JSON for Divi global variables.”

Do NOT use this skill for:

- Importing Divi **layouts** (`context: et_builder_layouts`)
- Importing Divi **presets** only
- Writing a style guide from scratch

## Step-by-step workflow

### Step 0 — Gather inputs

Ask for:

- **Brand name** (for filename + labels)
- **Style guide text** (paste, upload, or copied sections)
- **Optional tokens payload** (preferred):
  - JSON tokens, or
  - a table/CSV with `name`, `type`, `value` (optional `notes`)

If the user provides tokens, prefer them. If they only provide prose, extract only explicit values.

### Step 1 — Build a token set (tokens-first)

Create a canonical token set with names like:

- `color.brand.*`, `color.neutral.*`, `color.semantic.*`
- `font.heading.family`, `font.body.family`
- `type.h1.size`, `type.h1.lineHeight`, `type.h1.letterSpacing`, etc.
- `space.*`, `radius.*`, `shadow.*`
- `layout.container.max`, `layout.text.max`
- `link.*`, `string.*`

If tokens payload is missing common essentials (e.g. no neutral colors), do **not** invent—just note it as missing.

Reference: `references/token-table-template.md`

### Step 2 — Normalize values

- Colors: keep `#RRGGBB` if present; otherwise keep `rgb/rgba/hsl/hsla(...)` string as-is.
- Numbers: store as strings with units when applicable (`"16px"`, `"1200px"`) or unitless strings (`"1.2"`).
- Fonts: store font family string (e.g. `"Roboto"`, `"Open Sans"`).
- Links: store URL string.
- Strings: plain text.

### Step 3 — Generate stable IDs

Create deterministic IDs from token names:

- Colors (global_colors): `gcid-<slug>`
- Variables (global_variables): `gvid-<slug>`

Slug rules:

- lowercase
- replace non-alphanumerics with `-`
- collapse repeated `-`
- trim leading/trailing `-`

If collisions occur, append `-2`, `-3`, etc.

### Step 4 — Emit Divi import JSON

You MUST output this root shape:

```json
{
  "context": "et_builder",
  "data": [],
  "presets": [],
  "global_colors": [],
  "global_variables": [],
  "canvases": [],
  "images": [],
  "thumbnails": []
}
```

#### 4.1 `global_colors`

For each color token, include a tuple:

`[ "gcid-…", { "color": "<value>", "status": "active", "label": "<Label>" } ]`

#### 4.2 `global_variables`

For each token, include an object:

- `id`, `label`, `value`
- `order`: `""`
- `status`: `"active"`
- `lastUpdated`: ISO 8601 string (generation time)
- `variableType`: same as `type`
- `type`: one of `colors | numbers | strings | fonts | images | links`
- `groupKey`: best-effort grouping (e.g. `colors`, `type`, `space`, `layout`, `fonts`, `links`, `strings`)

Important: For every color you add to `global_colors`, also add a corresponding `global_variables` entry of `type: "colors"` so presets/layouts can reference it consistently.

### Step 5 — Produce the human-facing report

After the JSON, output:

1. **Token report table** with columns: `token name`, `divi id`, `type`, `value`, `label`
2. **Missing/ambiguous checklist** for anything mentioned but not specified explicitly

## Examples

### Example: user provides a token table

User provides a table matching `references/token-table-template.md`.

You output:

- filename suggestion: `<Brand>_Global-Variables.json`
- JSON import file
- report table
- missing checklist (likely short)

### Example: user provides prose only

If the prose includes:

- “Brand Navy: #1A2332”
- “H1 size: 48px”

Extract those exact values. If it says:

- “Use a deep navy as the primary color”

Do NOT invent a hex; put it in Missing/ambiguous.

## Troubleshooting (guidance you should include when relevant)

- **Import blocked**: mention hosts/security plugins may block `.json` uploads; suggest allowing JSON uploads.
- **Fonts not rendering**: variables can store font family names, but fonts must be available on the site (uploaded/served).
- **Too many tokens**: recommend starting with a baseline set (palette, fonts, type scale, spacing, radii, widths), then iterate.

## References

- `references/token-table-template.md`
- `references/test-prompts.md`
- `references/example-output-minimal.json`

