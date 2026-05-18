---
description: 入力されたテキストや作業内容から、明朝体×ダークモードの高級感あるHTMLメモを生成して保存します。
---

# Role
あなたはプロのエディトリアルデザイナー兼テクニカルライターです。ユーザーの入力や直近のコンテキストを元に、雑誌の特集記事のように美しいHTMLメモを生成し、ファイルとして書き出します。

# Task
ユーザーの指示を元に、Markdownではなく**必ず以下のHTMLテンプレートを使用した `.html` ファイル**を作成し、プロジェクト内の `memos/` ディレクトリ（存在しない場合は作成）に保存してください。
ファイル名は `memo_YYYYMMDD_テーマ名.html`（例: memo_20260509_skills.html）としてください。

# Design Concept
「ダークモードの文芸誌」。明朝体の上質なタイポグラフィ、温かみのある余白、控えめなオレンジのアクセント。読み返したくなる「資料」を目指します。

# Design Constraints
- フォント: 明朝体（Shippori Mincho を基調、システム明朝体にフォールバック）
- ベースカラー: 背景 `#121212` / テキスト `#E9E5DC`
- アクセントカラー: `#D97757`（Claudeオレンジ）
- スタイル（CSS）は一切変更せず、テンプレートのまま使用してください。

# Markup Rules（`<div class="memo-body">` 内の構成）
- セクション見出しは `<h2>` を使用（自動で連番が振られます）。サブ見出しは `<h3>`。
- 本文は `<p>` で記述。最初の段落の頭文字は自動でドロップキャップになります。
- 重要なキーワードは `<strong>` で囲む（自動的にアクセントカラーになります）。
- 考察・インサイト・引用は `<blockquote>` で囲む。
- コードは `<code>`、コードブロックは `<pre><code>`。
- 箇条書きは `<ul>`/`<ol>`、比較や一覧は `<table>` を活用すると映えます。
- セクションの区切りに `<hr>` を使うと装飾的なディバイダになります。
- リッチな表現（リスト・引用・テーブル・コード）を積極的に使い、単調な文章の羅列を避けてください。

# Placeholders
- `{タイトル}`: メモのタイトル。
- `{日付}`: 本日の日付（例: `2026.05.18`）。
- `{コンテンツ}`: 上記ルールに従って生成した本文HTML。

# HTML Template
以下のテンプレートのプレースホルダを生成した内容に置き換えて出力してください。

```html
<!DOCTYPE html>
<html lang="ja">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>{タイトル}</title>
  <style>
    @import url('https://fonts.googleapis.com/css2?family=Shippori+Mincho:wght@400;500;600;700;800&family=Cormorant+Garamond:ital,wght@0,500;0,600;1,500&display=swap');

    *, *::before, *::after { box-sizing: border-box; }

    :root {
      --bg: #121212;
      --ink: #E9E5DC;
      --ink-soft: #9d978a;
      --ink-faint: #6b665d;
      --accent: #D97757;
      --accent-2: #E8A98F;
      --rule: #2c2925;
      --code-bg: #0c0b0a;
    }

    html { scroll-behavior: smooth; }

    body {
      margin: 0;
      background-color: var(--bg);
      background-image:
        radial-gradient(900px 520px at 82% -8%, rgba(217,119,87,0.11), transparent 70%),
        radial-gradient(720px 600px at -12% 108%, rgba(217,119,87,0.06), transparent 72%);
      background-attachment: fixed;
      color: var(--ink);
      font-family: "Shippori Mincho", "Yu Mincho", "Hiragino Mincho ProN", "Noto Serif JP", serif;
      line-height: 1.95;
      letter-spacing: 0.04em;
      -webkit-font-smoothing: antialiased;
      text-rendering: optimizeLegibility;
    }

    body::before {
      content: "";
      position: fixed;
      inset: 0;
      pointer-events: none;
      z-index: 9999;
      opacity: 0.04;
      background-image: url("data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' width='200' height='200'%3E%3Cfilter id='n'%3E%3CfeTurbulence type='fractalNoise' baseFrequency='0.82' numOctaves='3' stitchTiles='stitch'/%3E%3C/filter%3E%3Crect width='100%25' height='100%25' filter='url(%23n)'/%3E%3C/svg%3E");
    }

    ::selection { background: rgba(217,119,87,0.32); color: #fff; }

    article {
      max-width: 720px;
      margin: 0 auto;
      padding: 104px 32px 120px;
      position: relative;
    }

    /* --- Header --- */
    .memo-header {
      margin-bottom: 8px;
      padding-bottom: 30px;
      border-bottom: 1px solid var(--rule);
    }
    .kicker {
      display: flex;
      align-items: center;
      gap: 12px;
      margin: 0 0 22px;
      font-family: "Cormorant Garamond", serif;
      font-size: 0.92rem;
      font-weight: 600;
      letter-spacing: 0.34em;
      text-transform: uppercase;
      color: var(--accent);
    }
    .kicker::before {
      content: "";
      width: 30px;
      height: 1px;
      background: var(--accent);
    }
    .memo-header h1 {
      margin: 0;
      font-size: clamp(2.1rem, 5.4vw, 3.15rem);
      font-weight: 800;
      line-height: 1.4;
      letter-spacing: 0.015em;
      color: #F4F1EA;
    }

    /* --- Body --- */
    .memo-body { counter-reset: section; margin-top: 52px; }

    .memo-body h2 {
      margin: 78px 0 22px;
      font-size: 1.58rem;
      font-weight: 700;
      line-height: 1.55;
      color: #F4F1EA;
    }
    .memo-body h2::before {
      counter-increment: section;
      content: counter(section, decimal-leading-zero);
      display: block;
      margin-bottom: 8px;
      font-family: "Cormorant Garamond", serif;
      font-size: 1.05rem;
      font-weight: 600;
      letter-spacing: 0.22em;
      color: var(--accent);
    }
    .memo-body > h2:first-child { margin-top: 0; }

    .memo-body h3 {
      margin: 44px 0 14px;
      font-size: 1.2rem;
      font-weight: 600;
      color: var(--accent-2);
    }

    .memo-body p { margin: 0 0 1.6rem; }

    .memo-body > p:first-of-type::first-letter {
      float: left;
      margin: 0.04em 0.14em -0.06em 0;
      font-family: "Cormorant Garamond", serif;
      font-size: 4.7rem;
      font-weight: 600;
      line-height: 0.78;
      color: var(--accent);
    }

    strong { color: var(--accent); font-weight: 700; }
    em { color: var(--accent-2); }

    a {
      color: var(--accent-2);
      text-decoration: none;
      border-bottom: 1px solid rgba(217,119,87,0.42);
      transition: border-color 0.2s ease;
    }
    a:hover { border-bottom-color: var(--accent); }

    /* --- Blockquote --- */
    blockquote {
      margin: 46px 0;
      padding: 26px 32px 28px;
      background: linear-gradient(180deg, rgba(217,119,87,0.07), rgba(217,119,87,0.015));
      border: 1px solid var(--rule);
      border-left: 3px solid var(--accent);
      border-radius: 2px;
      font-size: 1.12rem;
      font-style: italic;
      color: #cdc7b9;
    }
    blockquote::before {
      content: "\201C";
      display: block;
      height: 0.42em;
      font-family: "Cormorant Garamond", serif;
      font-size: 3.4rem;
      font-style: normal;
      line-height: 1;
      color: var(--accent);
    }
    blockquote p:last-child { margin-bottom: 0; }

    /* --- Lists --- */
    ul, ol { margin: 0 0 1.6rem; padding-left: 1.5em; }
    li { margin-bottom: 0.55rem; padding-left: 0.3em; }
    li::marker { color: var(--accent); }
    ol li::marker { font-family: "Cormorant Garamond", serif; font-weight: 600; }

    /* --- Code --- */
    code {
      font-family: "JetBrains Mono", "Fira Code", "Consolas", monospace;
      font-size: 0.83em;
      letter-spacing: 0;
      background: var(--code-bg);
      border: 1px solid var(--rule);
      padding: 2px 7px;
      border-radius: 4px;
      color: var(--accent-2);
    }
    pre {
      margin: 32px 0;
      padding: 24px 26px;
      background: var(--code-bg);
      border: 1px solid var(--rule);
      border-radius: 6px;
      overflow-x: auto;
      position: relative;
    }
    pre::before {
      content: "";
      position: absolute;
      top: 0; left: 0; right: 0;
      height: 2px;
      background: linear-gradient(90deg, var(--accent), transparent 60%);
    }
    pre code {
      background: none;
      border: none;
      padding: 0;
      font-size: 0.86em;
      line-height: 1.75;
      color: #d8d3c8;
    }

    /* --- Table --- */
    table {
      width: 100%;
      border-collapse: collapse;
      margin: 34px 0;
      font-size: 0.96rem;
    }
    th, td {
      padding: 13px 16px;
      text-align: left;
      border-bottom: 1px solid var(--rule);
    }
    thead th {
      color: var(--accent);
      font-weight: 700;
      letter-spacing: 0.06em;
      border-bottom: 2px solid var(--accent);
    }
    tbody tr { transition: background 0.18s ease; }
    tbody tr:hover { background: rgba(217,119,87,0.045); }

    img { max-width: 100%; border: 1px solid var(--rule); border-radius: 4px; }

    /* --- Divider --- */
    hr {
      border: none;
      height: 1px;
      width: 64%;
      margin: 58px auto;
      background: linear-gradient(90deg, transparent, var(--rule), transparent);
      position: relative;
    }
    hr::after {
      content: "\25C7";
      position: absolute;
      left: 50%; top: 50%;
      transform: translate(-50%, -50%);
      padding: 0 14px;
      background: var(--bg);
      color: var(--accent);
      font-size: 0.66rem;
    }

    /* --- Footer --- */
    .memo-footer {
      display: flex;
      justify-content: space-between;
      align-items: baseline;
      margin-top: 92px;
      padding-top: 26px;
      border-top: 1px solid var(--rule);
      font-family: "Cormorant Garamond", serif;
      font-size: 0.92rem;
      letter-spacing: 0.2em;
      text-transform: uppercase;
      color: var(--ink-faint);
    }
    .memo-footer .mark { color: var(--accent); }

    /* --- Entrance --- */
    @keyframes rise {
      from { opacity: 0; transform: translateY(18px); }
      to   { opacity: 1; transform: none; }
    }
    .memo-header, .memo-body > *, .memo-footer {
      animation: rise 0.72s cubic-bezier(0.2,0.7,0.2,1) both;
    }
    .memo-header { animation-delay: 0.04s; }
    .memo-body > *:nth-child(1) { animation-delay: 0.14s; }
    .memo-body > *:nth-child(2) { animation-delay: 0.20s; }
    .memo-body > *:nth-child(3) { animation-delay: 0.26s; }
    .memo-body > *:nth-child(4) { animation-delay: 0.32s; }
    .memo-body > *:nth-child(5) { animation-delay: 0.38s; }
    .memo-body > *:nth-child(6) { animation-delay: 0.44s; }
    .memo-footer { animation-delay: 0.5s; }

    @media (prefers-reduced-motion: reduce) {
      .memo-header, .memo-body > *, .memo-footer { animation: none; }
    }

    @media (max-width: 560px) {
      article { padding: 72px 22px 88px; }
      blockquote { padding: 22px 22px 24px; }
    }
  </style>
</head>
<body>
  <article>
    <header class="memo-header">
      <p class="kicker">Memo &middot; {日付}</p>
      <h1>{タイトル}</h1>
    </header>
    <div class="memo-body">
      {コンテンツ}
    </div>
    <footer class="memo-footer">
      <span class="mark">html-memo</span>
      <span>{日付}</span>
    </footer>
  </article>
</body>
</html>
```
