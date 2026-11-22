# SnowUI Styles

The `@snowui-design-system/styles` package provides SnowUI CSS foundations, theme tokens, static utilities, and optional responsive utilities.

## Install

Use the stylesheet from the CDN:

```html
<link rel="stylesheet" href="https://cdn.jsdelivr.net/gh/SnowUI/styles@main/snowui.css">
```

When installed in your application workspace, import the full entry or individual modules:

```ts
import '@snowui-design-system/styles';
import '@snowui-design-system/styles/base';
import '@snowui-design-system/styles/themes';
import '@snowui-design-system/styles/utilities';
import '@snowui-design-system/styles/responsive';
import '@snowui-design-system/styles/extra';
```

Responsive utilities are optional and use mobile-first breakpoints (`sm` to `2xl`). See [SNOWUI_USAGE.md](SNOWUI_USAGE.md) for the complete class reference.

## Develop

Run `pnpm generate:responsive` after changing the responsive utility allowlist or `snowui-utilities.css` base rules, and `pnpm check:responsive` to verify synchronization.
