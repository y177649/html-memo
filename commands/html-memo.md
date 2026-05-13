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
- ベースカラー: 背景 `#121212` / テキスト `#E0E0E0`
- アクセントカラー: `#D97757`

# Markup Rules (body内の構成)
- タイトルは `<h1>` を使用。
- セクション見出しは `<h2>` または `<h3>` を使用。
- 重要なキーワードは `<strong>` で囲む（自動的にアクセントカラーになります）。
- 考察、重要なインサイト、引用は `<blockquote>` で囲む。
- コードブロックは `<pre><code>` を使用。

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
    :root { --bg-dark: #121212; --text-main: #E0E0E0; --claude-orange: #D97757; --border-color: #333333; }
    body { background-color: var(--bg-dark); color: var(--text-main); font-family: "Yu Mincho", "Hiragino Mincho ProN", "Noto Serif JP", serif; line-height: 1.8; max-width: 800px; margin: 0 auto; padding: 40px 20px; letter-spacing: 0.05em; }
    h1, h2, h3 { color: var(--claude-orange); font-weight: normal; }
    h1 { font-size: 2.2rem; border-bottom: 2px solid var(--border-color); padding-bottom: 10px; margin-bottom: 30px; }
    h2 { font-size: 1.6rem; border-left: 4px solid var(--claude-orange); padding-left: 15px; margin-top: 40px; }
    p { margin-bottom: 1.5rem; }
    strong { color: var(--claude-orange); font-weight: bold; }
    blockquote { margin: 0; padding: 15px 20px; background-color: rgba(217, 119, 87, 0.05); border-left: 4px solid var(--claude-orange); color: #B0B0B0; font-style: italic; }
    code { font-family: "Fira Code", "Consolas", monospace; background-color: #222; padding: 3px 6px; border-radius: 4px; color: #FFB8A1; font-size: 0.9em; }
    pre { background-color: #0A0A0A; border: 1px solid var(--border-color); padding: 20px; border-radius: 6px; overflow-x: auto; }
    pre code { background-color: transparent; padding: 0; color: var(--text-main); }
  </style>
</head>
<body>
  <h1>{タイトル}</h1>
  {コンテンツ}
</body>
</html>
```
