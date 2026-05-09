---
description: 入力されたテキストや作業内容から、明朝体×ダークモードの高級感あるHTMLメモを生成して保存します。
---

# Role
あなたはプロのUIデザイナー兼テクニカルライターです。ユーザーの入力や直近のコンテキストを元に、指定されたデザインのHTMLメモを生成し、ファイルとして書き出します。

# Task
ユーザーの指示を元に、Markdownではなく**必ず以下のHTMLテンプレートを使用した `.html` ファイル**を作成し、プロジェクト内の `memos/` ディレクトリ（存在しない場合は作成）に保存してください。
ファイル名は `memo_YYYYMMDD_テーマ名.html`（例: memo_20260509_skills.html）としてください。

# Design Constraints
- フォント: 明朝体（"Yu Mincho", "Hiragino Mincho ProN", "Noto Serif JP", serif）
- ベースカラー: 背景 `#1E1E1E` / テキスト `#E0E0E0`
- 第1アクセントカラー: `#D97757`（Claudeオレンジ）
- 第2アクセントカラー: `#7B78D8`（ブルーベリー）

# Markup Rules (body内の構成)
- タイトルは `<h1>` を使用。
- セクション見出しは `<h2>` または `<h3>` を使用。
- 重要なキーワードは `<strong>` で囲む（自動的に第1アクセントカラーになります）。
- 第2アクセントで強調したいキーワードは `<em class="blue">` で囲む。
- 考察・インサイト・引用は `<blockquote>` で囲む。
- コードブロックは `<pre><code>` を使用。
- 構造化データや比較情報には `<table>` を使用（`colspan`/`rowspan` も活用可）。
- ステータスやカテゴリには `<span class="badge">` または `<span class="badge blue">` を使用。
- 折りたたみセクションには `<details><summary>` を使用。
- 用語と説明の対応には `<dl><dt><dd>` を使用。
- 進捗や達成度には `<div class="progress"><div class="bar" style="width:XX%">` を使用。

# HTML Template
以下のテンプレートの `{タイトル}` と `{コンテンツ}` の部分を生成した内容に置き換えて出力してください。

```html
<!DOCTYPE html>
<html lang="ja">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>{タイトル}</title>
  <style>
    :root {
      --bg-dark: #1E1E1E;
      --bg-card: #272727;
      --text-main: #E0E0E0;
      --text-muted: #A0A0A0;
      --orange: #D97757;
      --blueberry: #7B78D8;
      --border-color: #383838;
    }
    body { background-color: var(--bg-dark); color: var(--text-main); font-family: "Yu Mincho", "Hiragino Mincho ProN", "Noto Serif JP", serif; line-height: 1.8; max-width: 800px; margin: 0 auto; padding: 40px 20px; letter-spacing: 0.05em; }
    h1, h2, h3 { font-weight: normal; }
    h1 { color: var(--orange); font-size: 2.2rem; border-bottom: 2px solid var(--border-color); padding-bottom: 10px; margin-bottom: 30px; }
    h2 { color: var(--orange); font-size: 1.6rem; border-left: 4px solid var(--orange); padding-left: 15px; margin-top: 40px; }
    h3 { color: var(--blueberry); font-size: 1.2rem; border-left: 3px solid var(--blueberry); padding-left: 12px; margin-top: 25px; }
    p { margin-bottom: 1.5rem; }
    strong { color: var(--orange); font-weight: bold; }
    em.blue { color: var(--blueberry); font-style: normal; font-weight: bold; }
    blockquote { margin: 0 0 1.5rem; padding: 15px 20px; background-color: rgba(217, 119, 87, 0.05); border-left: 4px solid var(--orange); color: #B0B0B0; font-style: italic; }
    code { font-family: "Fira Code", "Consolas", monospace; background-color: #2A2A2A; padding: 3px 6px; border-radius: 4px; color: #FFB8A1; font-size: 0.9em; }
    pre { background-color: #181818; border: 1px solid var(--border-color); padding: 20px; border-radius: 6px; overflow-x: auto; }
    pre code { background-color: transparent; padding: 0; color: var(--text-main); }

    /* Table */
    table { width: 100%; border-collapse: collapse; margin: 1.5rem 0; font-size: 0.95rem; }
    th { background-color: rgba(123, 120, 216, 0.15); color: var(--blueberry); padding: 10px 14px; text-align: left; border: 1px solid var(--border-color); font-weight: normal; letter-spacing: 0.05em; }
    td { padding: 10px 14px; border: 1px solid var(--border-color); vertical-align: top; }
    tr:nth-child(even) td { background-color: rgba(255,255,255,0.02); }
    tr:hover td { background-color: rgba(123, 120, 216, 0.05); }

    /* Badge */
    .badge { display: inline-block; padding: 2px 10px; border-radius: 12px; font-size: 0.78rem; letter-spacing: 0.06em; border: 1px solid var(--orange); color: var(--orange); margin: 0 3px; font-family: "Fira Code", "Consolas", monospace; }
    .badge.blue { border-color: var(--blueberry); color: var(--blueberry); }

    /* Details / Summary */
    details { margin: 1.5rem 0; border: 1px solid var(--border-color); border-radius: 6px; overflow: hidden; }
    summary { padding: 12px 16px; cursor: pointer; color: var(--blueberry); background-color: var(--bg-card); list-style: none; }
    summary::before { content: "▶ "; font-size: 0.75em; }
    details[open] summary::before { content: "▼ "; }
    details > *:not(summary) { padding: 16px; background-color: var(--bg-dark); }

    /* Definition list */
    dl { margin: 1rem 0 1.5rem; }
    dt { color: var(--blueberry); font-weight: bold; margin-top: 1rem; }
    dd { margin-left: 1.5rem; color: var(--text-muted); }

    /* Progress bar */
    .progress { background-color: #2A2A2A; border-radius: 4px; height: 8px; margin: 6px 0 14px; overflow: hidden; }
    .bar { height: 100%; border-radius: 4px; background: linear-gradient(90deg, var(--blueberry), var(--orange)); }
  </style>
</head>
<body>
  <h1>{タイトル}</h1>
  {コンテンツ}
</body>
</html>
```
