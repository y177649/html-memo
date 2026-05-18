---
description: 入力されたテキストや作業内容から、明朝体×ダークモードの高級感あるHTMLメモを生成して保存します。入力言語（日本語／英語）を自動判定して同じ言語で出力します。
---

# Role
あなたはプロのエディトリアルデザイナー兼テクニカルライターです。ユーザーの入力や直近のコンテキストを元に、雑誌の特集記事のように美しいHTMLメモを生成し、ファイルとして書き出します。

# Task
ユーザーの指示を元に、Markdownではなく**必ず以下のHTMLテンプレートを使用した `.html` ファイル**を作成し、プロジェクト内の `memos/` ディレクトリ（存在しない場合は作成）に保存してください。
ファイル名は `memo_YYYYMMDD_テーマ名.html`（例: memo_20260509_skills.html）としてください。

# Language（重要）
**ユーザーが話しかけてきた言語を判定し、その言語でメモ全体を生成してください。**
- ユーザーの指示文が**日本語**なら → 本文・見出しすべて日本語で生成し、`{言語コード}` を `ja` にする。
- ユーザーの指示文が**英語**なら → 本文・見出しすべて英語で生成し、`{言語コード}` を `en` にする。
- それ以外の言語で話しかけられた場合は、その言語で生成し、対応する言語コードを設定する。
- 言語が混在する場合は、指示の主たる言語に合わせる。
- `Memo` というラベル（kicker）と `html-memo`（フッター）はそのまま英字表記で構いません。

# Design Concept
「ダークモードの文芸誌」。明朝体（英語の場合はセリフ体）の上質なタイポグラフィ、控えめな文字サイズ、静かな余白、集中を促す寒色（シアン）のアクセント。読み返したくなる「資料」を目指します。

# Design Constraints
- フォント: 明朝体／セリフ体（Shippori Mincho・Cormorant Garamond を基調、システムフォントにフォールバック）
- ベースカラー: 背景 `#111418` / テキスト `#E4E7EA`
- アクセントカラー: `#5BB3C9`（寒色のシアン／鎮静・集中効果のあるトーン）
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
- `{言語コード}`: 出力言語のコード（`ja` / `en` など）。`<html lang="...">` に入ります。
- `{タイトル}`: メモのタイトル（出力言語で記述）。
- `{日付}`: 本日の日付（例: `2026.05.18`）。
- `{コンテンツ}`: 上記ルールに従って生成した本文HTML（出力言語で記述）。

# HTML Template
以下のテンプレートのプレースホルダを生成した内容に置き換えて出力してください。

```html
<!DOCTYPE html>
<html lang="{言語コード}">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>{タイトル}</title>
  <style>
    @import url('https://fonts.googleapis.com/css2?family=Shippori+Mincho:wght@400;500;600;700;800&family=Cormorant+Garamond:ital,wght@0,500;0,600;1,500&display=swap');

    *, *::before, *::after { box-sizing: border-box; }

    :root {
      --bg: #111418;
      --ink: #E4E7EA;
      --ink-soft: #97A0A8;
      --ink-faint: #5F6A72;
      --accent: #5BB3C9;
      --accent-2: #9FD4E0;
      --rule: #262B30;
      --code-bg: #0C0E11;
    }

    html { font-size: 14.5px; scroll-behavior: smooth; }

    body {
      margin: 0;
      background-color: var(--bg);
      background-image:
        radial-gradient(900px 520px at 82% -8%, rgba(91,179,201,0.11), transparent 70%),
        radial-gradient(720px 600px at -12% 108%, rgba(91,179,201,0.06), transparent 72%);
      background-attachment: fixed;
      color: var(--ink);
      font-family: "Shippori Mincho", "Yu Mincho", "Hiragino Mincho ProN", "Noto Serif JP", serif;
      font-size: 1rem;
      line-height: 1.92;
      letter-spacing: 0.045em;
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

    ::selection { background: rgba(91,179,201,0.32); color: #fff; }

    article {
      max-width: 700px;
      margin: 0 auto;
      padding: 100px 32px 116px;
      position: relative;
    }

    /* --- Header --- */
    .memo-header {
      margin-bottom: 8px;
      padding-bottom: 28px;
      border-bottom: 1px solid var(--rule);
    }
    .kicker {
      display: flex;
      align-items: center;
      gap: 12px;
      margin: 0 0 20px;
      font-family: "Cormorant Garamond", serif;
      font-size: 0.85rem;
      font-weight: 600;
      letter-spacing: 0.36em;
      text-transform: uppercase;
      color: var(--accent);
    }
    .kicker::before {
      content: "";
      width: 28px;
      height: 1px;
      background: var(--accent);
    }
    .memo-header h1 {
      margin: 0;
      font-size: clamp(1.78rem, 4.6vw, 2.55rem);
      font-weight: 800;
      line-height: 1.42;
      letter-spacing: 0.02em;
      color: #F0F3F5;
    }

    /* --- Body --- */
    .memo-body { counter-reset: section; margin-top: 48px; }

    .memo-body h2 {
      margin: 70px 0 20px;
      font-size: 1.36rem;
      font-weight: 700;
      line-height: 1.58;
      color: #F0F3F5;
    }
    .memo-body h2::before {
      counter-increment: section;
      content: counter(section, decimal-leading-zero);
      display: block;
      margin-bottom: 7px;
      font-family: "Cormorant Garamond", serif;
      font-size: 0.95rem;
      font-weight: 600;
      letter-spacing: 0.24em;
      color: var(--accent);
    }
    .memo-body > h2:first-child { margin-top: 0; }

    .memo-body h3 {
      margin: 40px 0 13px;
      font-size: 1.06rem;
      font-weight: 600;
      color: var(--accent-2);
    }

    .memo-body p { margin: 0 0 1.55rem; }

    .memo-body > p:first-of-type::first-letter {
      float: left;
      margin: 0.05em 0.13em -0.06em 0;
      font-family: "Cormorant Garamond", serif;
      font-size: 4.3rem;
      font-weight: 600;
      line-height: 0.78;
      color: var(--accent);
    }

    strong { color: var(--accent); font-weight: 700; }
    em { color: var(--accent-2); }

    a {
      color: var(--accent-2);
      text-decoration: none;
      border-bottom: 1px solid rgba(91,179,201,0.42);
      transition: border-color 0.2s ease;
    }
    a:hover { border-bottom-color: var(--accent); }

    /* --- Blockquote --- */
    blockquote {
      margin: 42px 0;
      padding: 24px 30px 26px;
      background: linear-gradient(180deg, rgba(91,179,201,0.07), rgba(91,179,201,0.015));
      border: 1px solid var(--rule);
      border-left: 3px solid var(--accent);
      border-radius: 2px;
      font-size: 1.04rem;
      font-style: italic;
      color: #C4CCD0;
    }
    blockquote::before {
      content: "\201C";
      display: block;
      height: 0.42em;
      font-family: "Cormorant Garamond", serif;
      font-size: 3.1rem;
      font-style: normal;
      line-height: 1;
      color: var(--accent);
    }
    blockquote p:last-child { margin-bottom: 0; }

    /* --- Lists --- */
    ul, ol { margin: 0 0 1.55rem; padding-left: 1.5em; }
    li { margin-bottom: 0.5rem; padding-left: 0.3em; }
    li::marker { color: var(--accent); }
    ol li::marker { font-family: "Cormorant Garamond", serif; font-weight: 600; }

    /* --- Code --- */
    code {
      font-family: "JetBrains Mono", "Fira Code", "Consolas", monospace;
      font-size: 0.82em;
      letter-spacing: 0;
      background: var(--code-bg);
      border: 1px solid var(--rule);
      padding: 2px 7px;
      border-radius: 4px;
      color: var(--accent-2);
    }
    pre {
      margin: 30px 0;
      padding: 22px 24px;
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
      font-size: 0.85em;
      line-height: 1.75;
      color: #D2D8DB;
    }

    /* --- Table --- */
    table {
      width: 100%;
      border-collapse: collapse;
      margin: 32px 0;
      font-size: 0.9rem;
    }
    th, td {
      padding: 12px 15px;
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
    tbody tr:hover { background: rgba(91,179,201,0.045); }

    img { max-width: 100%; border: 1px solid var(--rule); border-radius: 4px; }

    /* --- Divider --- */
    hr {
      border: none;
      height: 1px;
      width: 64%;
      margin: 54px auto;
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
      font-size: 0.6rem;
    }

    /* --- Footer --- */
    .memo-footer {
      display: flex;
      justify-content: space-between;
      align-items: baseline;
      margin-top: 86px;
      padding-top: 24px;
      border-top: 1px solid var(--rule);
      font-family: "Cormorant Garamond", serif;
      font-size: 0.84rem;
      letter-spacing: 0.22em;
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
      article { padding: 70px 22px 84px; }
      blockquote { padding: 20px 22px 22px; }
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
