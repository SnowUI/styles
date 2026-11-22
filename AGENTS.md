<!-- AI-CONTRACT: tier=L1 | id=snowui-styles | scope=snowui/styles -->
# SnowUI Styles 仓库规则（L1）

读者：在 `snowui/styles` 工作的维护者与 AI。本仓库维护公开包 `@snowui-design-system/styles`（主题变量、浏览器基础层、静态工具类与可选响应式工具类）。

## 红线与章节索引

- `[STYLES-READ-01]` 必读顺序：[Project/AGENTS.md](../../AGENTS.md) → [snowui/AGENTS.md](../AGENTS.md) → 本文件 → 命中专题 → §1
- `[STYLES-THEME-01]` `snowui-themes.css` 是 `components/src/styles/themes.css` 的同步目标，严禁脱离上游独立手改漂移 → §2
- `[STYLES-RESP-01]` `snowui-responsive.css` 由生成器产出且必须保持可选入口，严禁并入默认 `snowui.css` 或手工修改生成文件 → §2
- `[STYLES-LANG-01]` 本公开仓库根 [README.md](README.md) 与 [SNOWUI_USAGE.md](SNOWUI_USAGE.md) 用英文，[SNOWUI_USAGE.zh.md](SNOWUI_USAGE.zh.md) 用中文，CSS／脚本代码注释统一用英文 → §2

## 1. 启动阅读链与一跳路由

开始任何任务前，先完成 `[Project/AGENTS.md](../../AGENTS.md) → [snowui/AGENTS.md](../AGENTS.md) → 本文件`（独立检出缺少上层文件时先说明缺口并定位规则，不假称已读取），再按意图一跳直达：

| 任务意图 | 本仓与共享权威落点 |
| --- | --- |
| 颜色 Token、视觉层级与圆角／间距规范 | [StyleSpec.md](../docs/standards/StyleSpec.md) · [FigmaComponentMap.md](../docs/reference/FigmaComponentMap.md) · [FigmaToSnowUI.md](../docs/reference/FigmaToSnowUI.md) |
| 浏览器基础层与全局排版／滚动条／链接基线 | [snowui-base.css](snowui-base.css) · [snowui.css](snowui.css) |
| 静态工具类与双语使用对照表 | [snowui-utilities.css](snowui-utilities.css) · [snowui-extra.css](snowui-extra.css) · [SNOWUI_USAGE.md](SNOWUI_USAGE.md) · [SNOWUI_USAGE.zh.md](SNOWUI_USAGE.zh.md) |
| 响应式工具类生成与体积预算门禁 | [scripts/generate-responsive-utilities.mjs](scripts/generate-responsive-utilities.mjs) → [snowui-responsive.css](snowui-responsive.css) |
| 发布、CDN／GitHub 同步与门禁 | [ReleaseSpec.md](../docs/standards/ReleaseSpec.md) · [package.json](package.json) |

## 2. 仓库职责与维护边界

1. **主题单一来源**：主题与颜色变量的唯一 AI 可编辑源位于 `../components/src/styles/themes.css`；修改后须通过 `../components/scripts/sync-themes.mjs` 同步至本仓 [snowui-themes.css](snowui-themes.css) 与其他消费端，不单独修改本仓副本。
2. **工具类与响应式同步**：新增或修改 [snowui-utilities.css](snowui-utilities.css) 工具类或响应式 allowlist 时，必须同步更新 [SNOWUI_USAGE.md](SNOWUI_USAGE.md) 与 [SNOWUI_USAGE.zh.md](SNOWUI_USAGE.zh.md)，并运行纯生成命令 `pnpm generate:responsive` 更新 [snowui-responsive.css](snowui-responsive.css)（预算上限 `44,000 B` raw / `5,250 B` gzip）。
3. **公开交付与验收纪律**：[README.md](README.md) 保持简洁英文且不含本机私有路径或更新日志；校验与测试命令（如 `pnpm check:responsive` 及工作区检查脚本）遵守上层验收门禁，仅在 Owner 发出验收指令后执行。
