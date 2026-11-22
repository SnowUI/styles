# SnowUI CSS 全量使用对照表（中文）

[View English Documentation](./SNOWUI_USAGE.md)

所有类名可直接用于 HTML、Svelte 或 JSX。数值后缀表示 `16px` 根字号基准下的名义 px 值（如 `p-12` = `0.75rem`，在 `16px` 根字号下为 `12px`）。

引入 `snowui-base.css` 后，基于 rem 的字号、边框宽度、尺寸、内外边距、Gap、定位偏移与普通圆角工具类会随 `14px–16px` 响应式根字号平滑缩放；`rounded-full` 保持语义性 `9999px` 例外。

## 样式入口与响应式工具类

| 包导出 | 文件 | 作用范围 |
| --- | --- | --- |
| `@snowui-design-system/styles` | `snowui.css` | 默认全量入口（`base` + `utilities` + `themes` + `extra`） |
| `@snowui-design-system/styles/base` | `snowui-base.css` | 浏览器初始化、响应式根字号、原生滚动条、应用根隔离 |
| `@snowui-design-system/styles/themes` | `snowui-themes.css` | 明暗主题变量与色阶 Token |
| `@snowui-design-system/styles/utilities` | `snowui-utilities.css` | 本文档列出的全部静态工具类 |
| `@snowui-design-system/styles/responsive` | `snowui-responsive.css` | 可选 mobile-first 响应式断点工具类 |
| `@snowui-design-system/styles/extra` | `snowui-extra.css` | 补充扩展样式入口 |

额外引入 `@snowui-design-system/styles/responsive`（或 `snowui-responsive.css`）即可启用 mobile-first 前缀：`sm:`（`640px`）、`md:`（`768px`）、`lg:`（`1024px`）、`xl:`（`1280px`）、`2xl:`（`1536px`）。

```html
<div class="grid grid-cols-1 gap-8 p-8 md:grid-cols-2 md:gap-16 lg:grid-cols-3 lg:p-24"></div>
```

第一阶段响应式 allowlist（`scripts/generate-responsive-utilities.mjs`）：
- **Display**：`block`、`inline-block`、`inline`、`flex`、`inline-flex`、`grid`、`inline-grid`、`hidden`
- **Flexbox**：`flex-row`、`flex-row-reverse`、`flex-col`、`flex-col-reverse`、`flex-wrap`、`flex-nowrap`、`flex-1`、`flex-auto`、`flex-initial`、`flex-none`、`grow`、`grow-0`、`shrink`、`shrink-0`
- **Grid**：`grid-cols-1..12`、`col-span-1..12`、`col-span-full`
- **Alignment**：`justify-{start,end,center,between,around,evenly}`、`items-{start,end,center,baseline,stretch}`、`self-{auto,start,end,center,stretch,baseline}`
- **Gap 与 Padding**：`gap-{0,4,8,12,16,20,24,28,40,48}`、`{p,px,py}-{0,4,8,12,16,20,24,28,40,48}`
- **Sizing**：`{w,h}-{12,16,20,24,28,32,40,48,56,64,72,80}`、`{w,h}-{full,screen,hug,fill}`、`min-{w,h}-{0,screen}`、`max-{w,h}-{10,20,30,40,50,60,70,80,90,100}p`
- **Overflow / Whitespace**：`overflow-{auto,hidden,visible,scroll}`、`overflow-{x,y}-{auto,hidden}`、`whitespace-{pre-wrap,nowrap}`

Margin、单侧内边距（`pt/pr/pb/pl`）、`size-*`、固定 `min/max-w/h-12..80`、`grid-rows-*`、`row-span-*`、颜色、边框、渐变、阴影、模糊、定位与层级、排版、交互、透明度与遮罩保持静态工具类，不生成响应式矩阵。

---

## 1. 颜色工具类

颜色描边类（`border-*`）生成 `0.5px`（`0.03125rem`）实线边框；内描边类（`inset-*`）通过 `box-shadow: inset` 实现 Figma 风格 `0.5px` 内描边，不占用盒模型空间。

### 随主题变化的黑白阶

`-100` 档位同时提供简写别名（`{bg,text,border,inset}-black` 与 `{bg,text,border,inset}-white`）。

| 色阶 | 背景类 | 文字类 | 边框类（`0.5px`） | 内描边类（`0.5px`） |
| --- | --- | --- | --- | --- |
| Black 100 / 80 / 40 / 20 / 10 / 4 | `bg-black-{100,80,40,20,10,4}` | `text-black-{100,80,40,20,10,4}` | `border-black-{100,80,40,20,10,4}` | `inset-black-{100,80,40,20,10,4}` |
| White 100 / 80 / 40 / 20 / 10 / 4 | `bg-white-{100,80,40,20,10,4}` | `text-white-{100,80,40,20,10,4}` | `border-white-{100,80,40,20,10,4}` | `inset-white-{100,80,40,20,10,4}` |

### 静态黑白阶（不随主题变化）

`-100` 档位同时提供简写别名（`{bg,text,border,inset}-static-black` 与 `{bg,text,border,inset}-static-white`）。

| 色阶 | 背景类 | 文字类 | 边框类（`0.5px`） | 内描边类（`0.5px`） |
| --- | --- | --- | --- | --- |
| Static Black 100 / 80 / 40 / 20 / 10 / 4 | `bg-static-black-{100,80,40,20,10,4}` | `text-static-black-{100,80,40,20,10,4}` | `border-static-black-{100,80,40,20,10,4}` | `inset-static-black-{100,80,40,20,10,4}` |
| Static White 100 / 80 / 40 / 20 / 10 / 4 | `bg-static-white-{100,80,40,20,10,4}` | `text-static-white-{100,80,40,20,10,4}` | `border-static-white-{100,80,40,20,10,4}` | `inset-static-white-{100,80,40,20,10,4}` |

### 背景层级、表面与语义色

| 分类 | 类名 | 说明 |
| --- | --- | --- |
| 页面与容器背景 | `bg-background`、`bg-background-1`、`bg-background-2`、`bg-background-3` | 当前主题页面背景与分层容器背景 |
| 表面层级 | `bg-surface-1`、`bg-surface-2`、`bg-surface-3` | 浮层与卡片表面背景 Token |
| 强调填充 | `bg-color-1`、`bg-color-2` | 主题辅助填充色 |
| 透明 | `bg-transparent`、`border-transparent`、`inset-transparent` | 透明背景或 `0.5px` 透明描边占位 |
| 核心语义色 | `{bg,text,border,inset}-{primary,foreground,brand}` | 主色、前景色与品牌色 |
| 辅助色板 | `{bg,text,border,inset}-{purple,indigo,blue,cyan,mint,green,yellow,orange,red}` | 9 色辅助色板（同时提供背景、文字、边框、内描边） |

---

## 2. 背景渐变

| 类名 | 说明 |
| --- | --- |
| `bg-gradient-primary` | 主色玻璃高光渐变 |
| `bg-gradient-gray` | 中性灰阶面板渐变 |
| `bg-gradient-black` | 静态深黑玻璃渐变 |
| `bg-gradient-{purple,indigo,blue,cyan,mint,green,yellow,orange,red}` | 辅助色玻璃渐变 |

---

## 3. 视觉效果（阴影与毛玻璃）

| 类名 | 效果 |
| --- | --- |
| `shadow-glass-1` | 轻量玻璃阴影 + `1px` 半透明白边 + `8px`（`0.5rem`）背景模糊 |
| `shadow-glass-2` | 强玻璃浮层阴影 + `1px` 半透明白边 + `20px`（`1.25rem`）背景模糊 |
| `shadow-glow` | 黑白双层外发光 |
| `shadow-focus` | `4px`（`0.25rem`）焦点光环 |
| `shadow-inner` | 多层内高光与内凹阴影 |
| `shadow-drop-1` | `0.5px` 轻投影 |
| `shadow-drop-2` | `2px / 4px` 柔和投影 |
| `shadow-image-hover` | 媒体卡片顶部内阴影遮罩 |
| `shadow-none` | 清除阴影（`box-shadow: none`） |
| `backdrop-blur-40` | 背景模糊 `20px`（`1.25rem`） |
| `backdrop-blur-100` | 背景模糊 `50px`（`3.125rem`） |

---

## 4. 边框与圆角

### 圆角（`rounded-*`）

取值档位：`0`、`4`、`8`、`12`、`16`、`20`、`24`、`28`、`32`、`40`、`48`、`80`（基于 rem 的名义 px）。

| 家族 | 类名 | 说明 |
| --- | --- | --- |
| 全局四角 | `rounded-{0,4,8,12,16,20,24,28,32,40,48,80}` | 兼容别名：`rounded-lg`（`8`）、`rounded-xl`（`12`）、`rounded-2xl`（`16`）、`rounded-3xl`（`24`） |
| 胶囊／正圆 | `rounded-full` | `border-radius: 9999px; object-fit: cover` |
| 单侧双角 | `rounded-{t,r,b,l}-{0,4,8,12,16,20,24,28,32,40,48,80}` | 上、右、下、左单边圆角 |
| 单角 | `rounded-{tl,tr,br,bl}-{0,4,8,12,16,20,24,28,32,40,48,80}` | 左上、右上、右下、左下独立圆角 |

### 边框宽度与单边黑色描边

| 家族 | 类名 | 说明 |
| --- | --- | --- |
| 边框宽度 | `border-0`、`border-0.5`、`border-1`、`border-2`、`border-4` | `0`、`0.5px`、`1px`、`2px`、`4px`（非零宽度自带 `solid`） |
| 单边 Black 描边 | `border-{t,r,b,l}-black`、`border-{t,r,b,l}-black-{100,80,40,20,10,4}` | 上、右、下、左单侧 `0.5px`（`0.03125rem`）实线边框 |

---

## 5. 间距（Padding、Margin、Gap）

名义步进档位：`0`、`4`、`8`、`12`、`16`、`20`、`24`、`28`、`40`、`48`（rem）。

| 家族 | 前缀／类名 | 说明 |
| --- | --- | --- |
| 内边距 | `p-*`、`px-*`、`py-*`、`pt-*`、`pr-*`、`pb-*`、`pl-*` | `p/px/py` 已纳入 `snowui-responsive.css` |
| 外边距 | `m-*`、`mx-*`、`my-*`、`mt-*`、`mr-*`、`mb-*`、`ml-*`、`m` | `m` 为 `m-4`（`4px`）简写别名；仅静态可用 |
| 间距 Gap | `gap-*` | Flex / Grid 容器间距（`0`–`48`）；支持响应式前缀 |

---

## 6. 尺寸（`size-*`、`w-*`、`h-*`、`min-*`、`max-*`）

固定尺寸档位：`12`、`16`、`20`、`24`、`28`、`32`、`40`、`48`、`56`、`64`、`72`、`80`（rem）。

| 家族 | 类名 | 说明 |
| --- | --- | --- |
| 等宽高 | `size-{12,16,20,24,28,32,40,48,56,64,72,80}` | 同时设置相等的 `width` 与 `height` |
| 固定宽／高 | `w-{12..80}`、`h-{12..80}` | 独立 rem 宽度或高度 |
| 容器与视口 | `w-full`（`100%`）、`h-full`（`100%`）、`w-screen`（`100vw`）、`h-screen`（`100vh`） | 百分比与视口尺寸 |
| 自适应与填充 | `w-hug`（`fit-content`）、`h-hug`（`fit-content`）、`w-fill`（`flex: 1; width: 100%`）、`h-fill`（`flex: 1; height: 100%; align-self: stretch`） | 对齐 Figma Hug / Fill 语义 |
| 最小宽／高 | `min-w-0`、`min-h-0`、`min-w-{12..80}`、`min-h-{12..80}`、`min-w-screen`、`min-h-screen` | 最小尺寸约束 |
| 最大宽／高（固定） | `max-w-{12..80}`、`max-h-{12..80}` | 最大 rem 尺寸约束 |
| 最大宽／高（百分比） | `max-w-{10,20,30,40,50,60,70,80,90,100}p`、`max-h-{10,20,30,40,50,60,70,80,90,100}p` | `10%`–`100%` 最大尺寸约束 |

---

## 7. 布局（Layout）

| 分组 | 类名 |
| --- | --- |
| Display | `block`、`inline-block`、`inline`、`flex`、`inline-flex`、`grid`、`inline-grid`、`hidden` |
| Flex 方向与换行 | `flex-row`、`flex-row-reverse`、`flex-col`、`flex-col-reverse`（均自带 `display: flex`）、`flex-wrap`、`flex-nowrap` |
| Flex 子项伸缩 | `flex-1`、`flex-auto`、`flex-initial`、`flex-none`、`grow`、`grow-0`、`shrink`、`shrink-0` |
| Grid 行列轨道 | `grid-cols-{1..12}`、`grid-rows-{1..6}` |
| Grid 跨度 | `col-span-{1..12}`、`col-span-full`、`row-span-{1..6}`、`row-span-full` |
| 对齐方式 | `justify-{start,end,center,between,around,evenly}`、`items-{start,end,center,baseline,stretch}`、`self-{auto,start,end,center,stretch,baseline}` |
| 定位模式与 Z-index | `relative`、`absolute`、`fixed`、`sticky`；`z-{0,10,20,30,40,50,100,auto}` |
| 溢出与空白换行 | `overflow-{auto,hidden,visible,scroll}`、`overflow-x-{auto,hidden}`、`overflow-y-{auto,hidden}`、`whitespace-pre-wrap`、`whitespace-nowrap` |

---

## 8. 定位偏移（Offsets）

偏移档位：`0`、`4`、`8`、`12`、`16`、`20`、`24`、`28`、`40`、`48`（rem）：
- `top-{0,4,8,12,16,20,24,28,40,48}`
- `right-{0,4,8,12,16,20,24,28,40,48}`
- `bottom-{0,4,8,12,16,20,24,28,40,48}`
- `left-{0,4,8,12,16,20,24,28,40,48}`

---

## 9. 字体排版（Typography）

| 类名 | 兼容别名 | 字号 / 行高 | `.paragraph` 段落底边距 |
| --- | --- | --- | --- |
| `text-12` | `text-xs` | `12px / 16px`（`0.75rem / 1rem`） | `text-12.paragraph` → `8px` |
| `text-14` | `text-sm` | `14px / 20px`（`0.875rem / 1.25rem`） | `text-14.paragraph` → `10px` |
| `text-16` | `text-base` | `16px / 24px`（`1rem / 1.5rem`） | `text-16.paragraph` → `12px` |
| `text-18` | `text-lg` | `18px / 28px`（`1.125rem / 1.75rem`） | `text-18.paragraph` → `14px` |
| `text-24` | `text-2xl` | `24px / 32px`（`1.5rem / 2rem`） | `text-24.paragraph` → `18px` |
| `text-32` | `text-4xl` | `32px / 40px`（`2rem / 2.5rem`） | `text-32.paragraph` → `24px` |
| `text-48` | `text-5xl` | `48px / 56px`（`3rem / 3.5rem`） | `text-48.paragraph` → `36px` |
| `text-64` | — | `64px / 72px`（`4rem / 4.5rem`） | `text-64.paragraph` → `48px` |

- **字重**：`font-regular` / `font-normal`（`400`）、`font-semibold`（`600`）
- **大小写与字距**：`uppercase`（`text-transform: uppercase`）、`tracking-wide`（`letter-spacing: 0.05em`）

---

## 10. 交互、透明度与遮罩

| 分类 | 类名 | 说明 |
| --- | --- | --- |
| 指针与选择 | `cursor-pointer`、`select-none` | 手型光标、禁止文本选中 |
| 尺寸拖拽 | `resize-none`、`resize-y`、`resize-x`、`resize` | 元素缩放方向控制 |
| 透明度 | `opacity-{0,4,10,20,40,80,100}` | 透明度 `0`、`0.04`、`0.1`、`0.2`、`0.4`、`0.8`、`1` |
| 渐变遮罩 | `mask-fade-bottom` | 底部渐隐线性遮罩（通过 `--mask-height` 控制高度，默认 `2em`） |

---

## 基础层说明（`snowui-base.css`）

- `:root` 与 `[theme="..."]` / `.theme-*` 提供 SnowUI / iOS 明暗主题变量（`snowui-themes.css`）。
- `@layer base` 设置 `box-sizing: border-box`、`14px–16px` 响应式根字号（`clamp(14px, 0.875vw + 10px, 16px)`）、`body` 与内联 `code` 默认排版、`Black/20%` 细原生滚动条，以及标题、列表、媒体和原生表单控件的基础初始化。
- 未由 `[data-snowui-frame]` 承载的普通 `<a href>` 默认使用 `--black-40` 且无下划线，`:hover` / `:focus-visible` 过渡为 `--black-100`，显式添加下划线的原生链接在 hover 时隐藏下划线；`Link`、`Button href` 等组件链接保持组件自身公开状态。
- `#root`、`#__next`、`#app` 与 `[data-snowui-app-root]` 建立 `isolation: isolate` 独立层叠上下文；挂到 `body` 的 Portal（如 `Dialog`、`Tooltip`）必须位于该根节点外，确保 `backdrop-filter` 可采样页面内容。
- Phosphor Duotone 图标默认 `0.2` 的背景层透明度统一归一化为 `0.08`。
