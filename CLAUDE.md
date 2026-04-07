# CLAUDE.md

本文件为 Claude Code (claude.ai/code) 提供该仓库的代码操作指引。

## 项目概述

这是一个名为 **水墨 Theme** 的 VS Code 主题扩展，包含 4 款中国传统风格的配色主题：

- **竹简（浅色）** - 棕色系列，WCAG AA 对比度，适合白天长时编码
- **水墨丹青（浅色）** - 水墨风系列，淡雅柔和，降低浅色环境下的视觉负担
- **竹简墨夜（深色）** - 棕色系列，玄墨底色搭配赭石与竹青语义分层，适合夜间专注
- **月涌大江流（深色）** - 深蓝夜江系列，深蓝底色配银蓝点缀，层级清晰、对比充足

## 构建命令

```bash
# 将扩展打包为 .vsix 文件
npm run build
# 或直接运行：
npx @vscode/vsce package
```

## 开发工作流

1. **在 VS Code 中测试主题**：按 F5 打开扩展开发宿主（Extension Development Host）加载主题
2. **应用主题更改**：在开发宿主中，运行 `Preferences: Color Theme` 切换不同主题
3. **主题文件位置**：所有主题 JSON 文件位于 `/themes/` 目录

## 架构说明

### 主题结构

每个主题都是标准的 VS Code 颜色主题 JSON 文件：

```json
{
  "name": "主题名称",
  "type": "light|dark",
  "colors": { /* UI 颜色 */ },
  "tokenColors": [ /* 语法高亮 */ ]
}
```

### 关键文件

- `package.json` - 扩展清单，在 `contributes.themes` 中注册主题
- `themes/*.json` - 各主题定义文件
- `previews/` - 各主题的 HTML 预览页面
- `.vscode/launch.json` - F5 调试配置，用于扩展开发

### 配色理念

主题使用具有语义含义的中国传统色：
- **竹简系列**：棕/米色背景（`#f0e6d3`、`#e8ddca`）配赤陶色强调（`#8b4b34`）
- **水墨丹青**：更浅的墨染灰色调，带微妙的蓝绿色点缀
- **月涌大江流**：深海军蓝（`#0d1117`）配银蓝色高亮（`#a8c5e8`）

语义 Token 为以下语言做了完善的映射：TypeScript/JavaScript、Vue、Python、Java、Go。

## 发布

扩展使用 `vsce package` 打包为 `.vsix` 文件，可手动上传或发布到 VS Code 扩展市场。
