# SnowUI CSS Reference (English)

[查看中文文档](./SNOWUI_USAGE.zh.md)

All classes can be applied directly in HTML, Svelte, or JSX. Numeric suffixes denote nominal pixel values at a `16px` root baseline (for example, `p-12` = `0.75rem` = `12px` at `16px`).

With `snowui-base.css`, rem-based typography, border widths, sizing, padding, margin, gap, offsets, and ordinary radius utilities scale smoothly with the `14px–16px` responsive root font size. `rounded-full` remains the semantic `9999px` exception.

## Entrypoints & Responsive Utilities

| Import | File | Scope |
| --- | --- | --- |
| `@snowui-design-system/styles` | `snowui.css` | Default bundle (`base` + `utilities` + `themes` + `extra`) |
| `@snowui-design-system/styles/base` | `snowui-base.css` | Browser reset, root font scaling, native scrollbars, app root isolation |
| `@snowui-design-system/styles/themes` | `snowui-themes.css` | Light/dark theme tokens and color scales |
| `@snowui-design-system/styles/utilities` | `snowui-utilities.css` | Static utility classes documented below |
| `@snowui-design-system/styles/responsive` | `snowui-responsive.css` | Optional mobile-first breakpoint utilities |
| `@snowui-design-system/styles/extra` | `snowui-extra.css` | Supplemental extension stylesheet |

Import `@snowui-design-system/styles/responsive` (or `snowui-responsive.css`) to enable mobile-first prefixes: `sm:` (`640px`), `md:` (`768px`), `lg:` (`1024px`), `xl:` (`1280px`), and `2xl:` (`1536px`).

```html
<div class="grid grid-cols-1 gap-8 p-8 md:grid-cols-2 md:gap-16 lg:grid-cols-3 lg:p-24"></div>
```

Responsive phase-one allowlist (`scripts/generate-responsive-utilities.mjs`):
- **Display**: `block`, `inline-block`, `inline`, `flex`, `inline-flex`, `grid`, `inline-grid`, `hidden`
- **Flexbox**: `flex-row`, `flex-row-reverse`, `flex-col`, `flex-col-reverse`, `flex-wrap`, `flex-nowrap`, `flex-1`, `flex-auto`, `flex-initial`, `flex-none`, `grow`, `grow-0`, `shrink`, `shrink-0`
- **Grid**: `grid-cols-1..12`, `col-span-1..12`, `col-span-full`
- **Alignment**: `justify-{start,end,center,between,around,evenly}`, `items-{start,end,center,baseline,stretch}`, `self-{auto,start,end,center,stretch,baseline}`
- **Gap & Padding**: `gap-{0,4,8,12,16,20,24,28,40,48}`, `{p,px,py}-{0,4,8,12,16,20,24,28,40,48}`
- **Sizing**: `{w,h}-{12,16,20,24,28,32,40,48,56,64,72,80}`, `{w,h}-{full,screen,hug,fill}`, `min-{w,h}-{0,screen}`, `max-{w,h}-{10,20,30,40,50,60,70,80,90,100}p`
- **Overflow / Whitespace**: `overflow-{auto,hidden,visible,scroll}`, `overflow-{x,y}-{auto,hidden}`, `whitespace-{pre-wrap,nowrap}`

Margin, single-side padding (`pt/pr/pb/pl`), `size-*`, fixed `min/max-w/h-12..80`, `grid-rows-*`, `row-span-*`, colors, borders, gradients, shadows, blur, positioning/z-index, typography, interactivity, opacity, and masks remain static-only.

---

## 1. Color Utilities

Color border utilities (`border-*`) apply a `0.5px` (`0.03125rem`) solid border; inset border utilities (`inset-*`) apply a `0.5px` (`0.03125rem`) inner stroke via `box-shadow: inset` without affecting box dimensions.

### Theme-Aware Black & White Scales

`-100` steps also provide bare aliases (`bg-black`, `text-black`, `border-black`, `inset-black`, `bg-white`, `text-white`, `border-white`, `inset-white`).

| Scale | Background | Text | Border (`0.5px`) | Inset Stroke (`0.5px`) |
| --- | --- | --- | --- | --- |
| Black 100 / 80 / 40 / 20 / 10 / 4 | `bg-black-{100,80,40,20,10,4}` | `text-black-{100,80,40,20,10,4}` | `border-black-{100,80,40,20,10,4}` | `inset-black-{100,80,40,20,10,4}` |
| White 100 / 80 / 40 / 20 / 10 / 4 | `bg-white-{100,80,40,20,10,4}` | `text-white-{100,80,40,20,10,4}` | `border-white-{100,80,40,20,10,4}` | `inset-white-{100,80,40,20,10,4}` |

### Static Black & White Scales (Theme-Independent)

`-100` steps also provide bare aliases (`{bg,text,border,inset}-static-black` and `{bg,text,border,inset}-static-white`).

| Scale | Background | Text | Border (`0.5px`) | Inset Stroke (`0.5px`) |
| --- | --- | --- | --- | --- |
| Static Black 100 / 80 / 40 / 20 / 10 / 4 | `bg-static-black-{100,80,40,20,10,4}` | `text-static-black-{100,80,40,20,10,4}` | `border-static-black-{100,80,40,20,10,4}` | `inset-static-black-{100,80,40,20,10,4}` |
| Static White 100 / 80 / 40 / 20 / 10 / 4 | `bg-static-white-{100,80,40,20,10,4}` | `text-static-white-{100,80,40,20,10,4}` | `border-static-white-{100,80,40,20,10,4}` | `inset-static-white-{100,80,40,20,10,4}` |

### Backgrounds, Surfaces & Semantic Tokens

| Category | Classes | Description |
| --- | --- | --- |
| Page & Layered Backgrounds | `bg-background`, `bg-background-1`, `bg-background-2`, `bg-background-3` | Active theme background and layered containers |
| Surface Levels | `bg-surface-1`, `bg-surface-2`, `bg-surface-3` | Elevated surface tokens |
| Accent Tokens | `bg-color-1`, `bg-color-2` | Theme accent fill tokens |
| Transparent | `bg-transparent`, `border-transparent`, `inset-transparent` | Transparent background or `0.5px` stroke |
| Semantic Roles | `{bg,text,border,inset}-{primary,foreground,brand}` | Primary, foreground, and brand tokens |
| Secondary Palette | `{bg,text,border,inset}-{purple,indigo,blue,cyan,mint,green,yellow,orange,red}` | Full secondary palette across fill, text, border, and inset stroke |

---

## 2. Background Gradients

| Class | Description |
| --- | --- |
| `bg-gradient-primary` | Glass primary gradient |
| `bg-gradient-gray` | Subtle neutral panel gradient |
| `bg-gradient-black` | Deep static-black glass gradient |
| `bg-gradient-{purple,indigo,blue,cyan,mint,green,yellow,orange,red}` | Secondary color glass gradients |

---

## 3. Visual Effects (Shadows & Backdrop Blur)

| Class | Effect |
| --- | --- |
| `shadow-glass-1` | Light glass shadow + `1px` translucent white border + `8px` (`0.5rem`) backdrop blur |
| `shadow-glass-2` | Elevated glass shadow + `1px` translucent white border + `20px` (`1.25rem`) backdrop blur |
| `shadow-glow` | Dual black/white outer glow |
| `shadow-focus` | `4px` (`0.25rem`) focus halo |
| `shadow-inner` | Multi-layer inset highlight and depth shadow |
| `shadow-drop-1` | Subtle `0.5px` drop shadow |
| `shadow-drop-2` | Soft `2px / 4px` drop shadow |
| `shadow-image-hover` | Top inset shadow for media hover overlays |
| `shadow-none` | Removes box-shadow (`box-shadow: none`) |
| `backdrop-blur-40` | Backdrop blur `20px` (`1.25rem`) |
| `backdrop-blur-100` | Backdrop blur `50px` (`3.125rem`) |

---

## 4. Borders & Radius

### Border Radius (`rounded-*`)

Value set: `0`, `4`, `8`, `12`, `16`, `20`, `24`, `28`, `32`, `40`, `48`, `80` (nominal px in rem).

| Family | Classes | Notes |
| --- | --- | --- |
| All corners | `rounded-{0,4,8,12,16,20,24,28,32,40,48,80}` | Semantic aliases: `rounded-lg` (`8`), `rounded-xl` (`12`), `rounded-2xl` (`16`), `rounded-3xl` (`24`) |
| Pill / Circle | `rounded-full` | `border-radius: 9999px; object-fit: cover` |
| Single edge | `rounded-{t,r,b,l}-{0,4,8,12,16,20,24,28,32,40,48,80}` | Top, right, bottom, or left two corners |
| Single corner | `rounded-{tl,tr,br,bl}-{0,4,8,12,16,20,24,28,32,40,48,80}` | Individual corner radius |

### Border Width & Directional Black Borders

| Family | Classes | Effect |
| --- | --- | --- |
| Border width | `border-0`, `border-0.5`, `border-1`, `border-2`, `border-4` | `0`, `0.5px`, `1px`, `2px`, `4px` (`solid` for non-zero widths) |
| Directional Black | `border-{t,r,b,l}-black`, `border-{t,r,b,l}-black-{100,80,40,20,10,4}` | Single-side `0.5px` (`0.03125rem`) solid border on the Black scale |

---

## 5. Spacing (Padding, Margin, Gap)

Nominal step scale: `0`, `4`, `8`, `12`, `16`, `20`, `24`, `28`, `40`, `48` (rem-based).

| Family | Prefixes / Classes | Notes |
| --- | --- | --- |
| Padding | `p-*`, `px-*`, `py-*`, `pt-*`, `pr-*`, `pb-*`, `pl-*` | `p/px/py` also available in `snowui-responsive.css` |
| Margin | `m-*`, `mx-*`, `my-*`, `mt-*`, `mr-*`, `mb-*`, `ml-*`, `m` | `m` is an alias for `m-4` (`4px`); static-only |
| Gap | `gap-*` | Flex/Grid gap (`0`–`48`); included in responsive allowlist |

---

## 6. Sizing (`size-*`, `w-*`, `h-*`, `min-*`, `max-*`)

Fixed nominal scale: `12`, `16`, `20`, `24`, `28`, `32`, `40`, `48`, `56`, `64`, `72`, `80` (rem-based).

| Family | Classes | Description |
| --- | --- | --- |
| Square size | `size-{12,16,20,24,28,32,40,48,56,64,72,80}` | Sets equal `width` and `height` |
| Fixed width / height | `w-{12..80}`, `h-{12..80}` | Explicit rem width or height |
| Viewport & Container | `w-full` (`100%`), `h-full` (`100%`), `w-screen` (`100vw`), `h-screen` (`100vh`) | Percentage and viewport dimensions |
| Intrinsic & Flex Fill | `w-hug` (`fit-content`), `h-hug` (`fit-content`), `w-fill` (`flex: 1; width: 100%`), `h-fill` (`flex: 1; height: 100%; align-self: stretch`) | Figma-aligned Hug / Fill layout helpers |
| Min width / height | `min-w-0`, `min-h-0`, `min-w-{12..80}`, `min-h-{12..80}`, `min-w-screen`, `min-h-screen` | Minimum dimension constraints |
| Max width / height (fixed) | `max-w-{12..80}`, `max-h-{12..80}` | Maximum rem dimensions |
| Max width / height (`%`) | `max-w-{10,20,30,40,50,60,70,80,90,100}p`, `max-h-{10,20,30,40,50,60,70,80,90,100}p` | `10%` to `100%` maximum dimensions |

---

## 7. Layout

| Group | Classes |
| --- | --- |
| Display | `block`, `inline-block`, `inline`, `flex`, `inline-flex`, `grid`, `inline-grid`, `hidden` |
| Flex Direction & Wrap | `flex-row`, `flex-row-reverse`, `flex-col`, `flex-col-reverse` (each includes `display: flex`), `flex-wrap`, `flex-nowrap` |
| Flex Item | `flex-1`, `flex-auto`, `flex-initial`, `flex-none`, `grow`, `grow-0`, `shrink`, `shrink-0` |
| Grid Tracks | `grid-cols-{1..12}`, `grid-rows-{1..6}` |
| Grid Span | `col-span-{1..12}`, `col-span-full`, `row-span-{1..6}`, `row-span-full` |
| Justify & Align | `justify-{start,end,center,between,around,evenly}`, `items-{start,end,center,baseline,stretch}`, `self-{auto,start,end,center,stretch,baseline}` |
| Position & Z-index | `relative`, `absolute`, `fixed`, `sticky`; `z-{0,10,20,30,40,50,100,auto}` |
| Overflow & Whitespace | `overflow-{auto,hidden,visible,scroll}`, `overflow-x-{auto,hidden}`, `overflow-y-{auto,hidden}`, `whitespace-pre-wrap`, `whitespace-nowrap` |

---

## 8. Positioning Offsets

Offset step scale: `0`, `4`, `8`, `12`, `16`, `20`, `24`, `28`, `40`, `48` (rem-based):
- `top-{0,4,8,12,16,20,24,28,40,48}`
- `right-{0,4,8,12,16,20,24,28,40,48}`
- `bottom-{0,4,8,12,16,20,24,28,40,48}`
- `left-{0,4,8,12,16,20,24,28,40,48}`

---

## 9. Typography

| Class | Alias | Font Size / Line Height | `.paragraph` Bottom Margin |
| --- | --- | --- | --- |
| `text-12` | `text-xs` | `12px / 16px` (`0.75rem / 1rem`) | `text-12.paragraph` → `8px` |
| `text-14` | `text-sm` | `14px / 20px` (`0.875rem / 1.25rem`) | `text-14.paragraph` → `10px` |
| `text-16` | `text-base` | `16px / 24px` (`1rem / 1.5rem`) | `text-16.paragraph` → `12px` |
| `text-18` | `text-lg` | `18px / 28px` (`1.125rem / 1.75rem`) | `text-18.paragraph` → `14px` |
| `text-24` | `text-2xl` | `24px / 32px` (`1.5rem / 2rem`) | `text-24.paragraph` → `18px` |
| `text-32` | `text-4xl` | `32px / 40px` (`2rem / 2.5rem`) | `text-32.paragraph` → `24px` |
| `text-48` | `text-5xl` | `48px / 56px` (`3rem / 3.5rem`) | `text-48.paragraph` → `36px` |
| `text-64` | — | `64px / 72px` (`4rem / 4.5rem`) | `text-64.paragraph` → `48px` |

- **Font weight**: `font-regular` / `font-normal` (`400`), `font-semibold` (`600`)
- **Transform & Tracking**: `uppercase` (`text-transform: uppercase`), `tracking-wide` (`letter-spacing: 0.05em`)

---

## 10. Interactivity, Opacity & Masks

| Category | Classes | Description |
| --- | --- | --- |
| Cursor & Selection | `cursor-pointer`, `select-none` | Pointer cursor and disabled text selection |
| Resize | `resize-none`, `resize-y`, `resize-x`, `resize` | Element resize axis controls |
| Opacity | `opacity-{0,4,10,20,40,80,100}` | Opacity `0`, `0.04`, `0.1`, `0.2`, `0.4`, `0.8`, `1` |
| Mask | `mask-fade-bottom` | Bottom linear-gradient fade mask (`--mask-height`, default `2em`) |

---

## Base Layer (`snowui-base.css`)

- `:root` and `[theme="..."]` / `.theme-*` provide SnowUI and iOS light/dark theme tokens (`snowui-themes.css`).
- `@layer base` sets `box-sizing: border-box`, a responsive `14px–16px` root font size (`clamp(14px, 0.875vw + 10px, 16px)`), default `body` / inline `code` typography, thin `Black/20%` native scrollbars, and document-flow resets for headings, lists, media, and form controls.
- Plain `<a href>` elements outside `[data-snowui-frame]` default to `--black-40` with no underline, transition to `--black-100` on `:hover` / `:focus-visible`, and hide explicit underlines on hover; SnowUI `Link` and `Button href` retain their own component states.
- `#root`, `#__next`, `#app`, and `[data-snowui-app-root]` establish `isolation: isolate`; body-level portals (`Dialog`, `Tooltip`, etc.) must mount outside that root so `backdrop-filter` can sample page content.
- Phosphor Duotone background layers (`opacity="0.2"`) are normalized to `0.08`.
