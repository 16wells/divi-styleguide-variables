# Test prompts

Use these prompts to validate triggering, functionality, and over/under-triggering.

## Should trigger

- "Convert this style guide into a Divi 5 Global Variables JSON I can import."
- "Generate a Divi `global_colors` + `global_variables` file from these design tokens."
- "Create a Divi 5 `context: et_builder` Global Variables import from this token table."
- "Extract explicit colors/fonts/type scale from this brand guide and output Divi variables."

## Should NOT trigger

- "How do I import a Divi layout JSON?"
- "Write me a brand style guide."
- "What is WCAG contrast?"
- "Help me design a logo."

## Functional edge cases

- Prose mentions colors by name but no hex values → must list missing colors, not invent.
- Tokens include duplicate names → must de-dupe and/or suffix IDs deterministically.
- Tokens include rgba/hsl → should preserve string (or normalize if hex is also given).
- Fonts mentioned but not available on site → mention as a post-import requirement.

