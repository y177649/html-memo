# html-memo (Claude Code Skill)

<table>
  <tr>
    <td align="center">
      <a href="README.md"><strong>🇯🇵 日本語</strong></a><br>
      <sub>日本語に切り替え</sub>
    </td>
    <td align="center">
      <strong>🇺🇸 English</strong><br>
      <sub>Current page</sub>
    </td>
  </tr>
</table>

A custom skill that turns your daily notes and work logs into elegant HTML files styled in "serif typography × dark mode" — just by running the `/html-memo` command in Claude Code.

![Preview](assets/preview.png)

## Features
- 🌙 Eye-friendly dark mode base
- 🖋 Refined serif typography for a premium feel
- 🟧 Orange accents that highlight key insights
- 🚀 No installation required — just drop it into your `commands` folder

## 💡 Setting Up a Comfortable Preview Environment (Recommended)
To preview HTML files inside your editor with a single click, just like Markdown, we recommend installing Microsoft's official extension.

1. When you open this project in VS Code / Cursor, a pop-up will appear in the bottom-right corner recommending the `Live Preview` extension — please install it.
2. When you open an HTML file, a preview icon (a magnifying glass, or a "Show Preview" button) appears in the top-right of the editor. Just click it to check your design directly inside the editor, without opening a browser.

## Installation
1. Download `commands/html-memo.md` from this repository.
2. Place it inside the `commands` folder in your project's root directory. (Create the folder if it doesn't exist.)

## Usage
Launch Claude Code and run the command as follows:

```bash
> /html-memo Summarize today's development progress and the upcoming challenges
```

A beautiful HTML file will be automatically generated in the `memos/` directory.
