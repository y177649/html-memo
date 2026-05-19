<div align="center">

# html-memo

**将每日的笔记与工作日志，用一条命令转换为「明朝体 × 暗色模式」的优雅 HTML 文件。只需在 Claude Code 提示中输入 `/html-memo`，就能生成一份让人想反复回顾的「文档」。**

> 这是一个 Claude Code 自定义技能，可将常被遗留为纯 Markdown 的信息升华为精致的文档。无需安装，只需放入 `commands` 文件夹即可运行。

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)
[![Style](https://img.shields.io/badge/Style-Serif_%C3%97_Dark-111418)](#)
[![Claude Code](https://img.shields.io/badge/Claude_Code-Skill-D97757)](https://claude.ai/claude-code)
<img src="assets/claude-icon.png" alt="Claude" height="20">

[![日本語](https://img.shields.io/badge/Lang-%E6%97%A5%E6%9C%AC%E8%AA%9E-87CEEB.svg)](README.md)
[![English](https://img.shields.io/badge/Lang-English-87CEEB.svg)](README.en.md)
[![한국어](https://img.shields.io/badge/Lang-%ED%95%9C%EA%B5%AD%EC%96%B4-87CEEB.svg)](README.ko.md)
[![简体中文](https://img.shields.io/badge/Lang-%E7%AE%80%E4%BD%93%E4%B8%AD%E6%96%87-87CEEB.svg)](README.zh.md)
[![繁體中文](https://img.shields.io/badge/Lang-%E7%B9%81%E9%AB%94%E4%B8%AD%E6%96%87-87CEEB.svg)](README.tw.md)

</div>

---

## 输出示例

通过 `/html-memo` 生成的 HTML 文件，会呈现如下设计。

<div align="center">
  <img src="assets/example.en.png" alt="html-memo 输出示例" width="700">
</div>

---

## 特性

| | |
|---|---|
| **以暗色模式为基础** | 采用比纯黑更柔和的 `#111418`，长时间阅读也不易使眼睛疲劳 |
| **明朝体字体** | 为文本赋予格调与可读性的高级排版 |
| **冷色调强调色** | 具有沉静、聚焦效果的冷色青色 `#5BB3C9`，自然地突出重要洞见 |
| **无需安装** | 只需将一个文件放入 `commands` 文件夹即可运行 |
| **多语言支持** | 自动识别你输入时所用的语言，并以相同语言输出笔记 |

---

## 快速开始

无需手动放置文件。**只需将本仓库的 URL 交给 Claude Code，并请它帮你设置好该技能**，即可完成配置。

启动 Claude Code，并如下指示它。

```text
让我可以使用这个仓库中的技能：
https://github.com/y177649/html-memo
```

Claude Code 会读取仓库内容，并将 `commands/html-memo.md` 放入你项目的 `commands` 文件夹。完成后即可直接使用 `/html-memo` 命令。

---

## 手动安装

如果你不使用 Claude Code，想自行配置，可按以下步骤放置。

1. 从本仓库下载 `commands/html-memo.md`。
2. 将其放入你项目根目录下的 `commands` 文件夹中。（若文件夹不存在，请自行创建。）

---

## 使用方法

启动 Claude Code，并如下执行命令。

```bash
> /html-memo 总结今天的开发进展以及今后的课题
```

`memos/` 目录中会自动生成精美的 HTML 文件。

---

## 搭建舒适的预览环境（推荐）

为了像 Markdown 一样在编辑器内一键预览 HTML 文件，推荐安装 Microsoft 官方扩展。

1. 在 VS Code / Cursor 中打开本项目时，右下角会弹出推荐安装 `Live Preview` 扩展的提示，请进行安装。
2. 打开 HTML 文件后，编辑器右上角会显示预览图标（放大镜标志，或「显示预览」按钮）。只需点击它，无需打开浏览器，即可在编辑器内直接确认设计。

---

## 许可证

基于 [MIT License](LICENSE) 公开发布。
