# Token table template (recommended)

If you can supply tokens in this table format, the skill can generate Divi variables deterministically.

## Columns

- `name` (required): canonical token name, e.g. `color.brand.navy`, `type.h1.size`, `space.2`
- `type` (required): one of `colors`, `numbers`, `fonts`, `strings`, `links`, `images`
- `value` (required): token value as used in Divi variables (strings are fine)
- `notes` (optional): any human description

## Example

| name | type | value | notes |
|---|---|---|---|
| `color.brand.navy` | `colors` | `#1A2332` | Primary background |
| `color.semantic.success` | `colors` | `#00D47E` | Success state |
| `font.heading.family` | `fonts` | `Roboto` | Headings |
| `font.body.family` | `fonts` | `Open Sans` | Body text |
| `type.h1.size` | `numbers` | `48px` | Desktop |
| `type.h1.lineHeight` | `numbers` | `1.2` | Unitless |
| `space.2` | `numbers` | `16px` | Spacing scale |
| `radius.sm` | `numbers` | `4px` | Buttons/inputs |
| `shadow.sm` | `numbers` | `0 2px 8px rgba(0,0,0,0.08)` | Card shadow |
| `link.site` | `links` | `https://example.com` | Canonical URL |

