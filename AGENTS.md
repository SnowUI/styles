# SnowUI Styles — AI Entry

`@snowui-design-system/styles` provides SnowUI CSS foundations, light/dark theme tokens, static utility classes, and optional responsive utilities.

## Documentation & Reference Entrypoints

- Package overview & entrypoints: [README.md](./README.md)
- Complete utility class & layout reference (English): [SNOWUI_USAGE.md](./SNOWUI_USAGE.md)
- Complete utility class & layout reference (Simplified Chinese): [SNOWUI_USAGE.zh.md](./SNOWUI_USAGE.zh.md)
- Full SnowUI component & token AI documentation: https://snowui.dev/llms-en.txt (Chinese: https://snowui.dev/llms.txt · Tokens: https://snowui.dev/llms/tokens.json)

## Usage Guidelines for AI

1. **Optional for external applications**: `@snowui-design-system/components` ships its own self-contained component styles (`@snowui-design-system/components/styles`) and does **not** require installing `@snowui-design-system/styles`. Use this package only when your application wants SnowUI's page reset, theme sheet, and utility classes.
2. **Entrypoints**:
   - `@snowui-design-system/styles` — combined base, theme tokens, and static utilities (`snowui.css`)
   - `@snowui-design-system/styles/themes` — light/dark theme CSS variables (`snowui-themes.css`)
   - `@snowui-design-system/styles/utilities` — static page layout, spacing, typography, radius, and surface classes (`snowui-utilities.css`)
   - `@snowui-design-system/styles/responsive` — optional mobile-first responsive utilities (`sm:` through `2xl:`, `snowui-responsive.css`)
3. **Token discipline**: check [SNOWUI_USAGE.md](./SNOWUI_USAGE.md) before inventing utility names; gradient classes use nominal pixel suffixes (such as `.gap-8`, `.p-16`, `.rounded-12`), while CSS variables use tier indices (`--gap-2`, `--padding-4`, `--radius-3`).
