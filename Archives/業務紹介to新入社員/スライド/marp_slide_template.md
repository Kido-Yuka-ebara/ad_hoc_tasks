---
marp: true
title: プレゼンテーションタイトル
header: ' '
footer: 'Copyright(c) Ebara Corporation, All rights reserved'
paginate: true
# スライドサイズをcm単位で指定
width: 33.867cm
height: 19.05cm
---

<style>
/* ========================================
   1. 基本設定（色、フォント）
   ======================================== */
:root {
  --color-background: #ffffff;    /* 背景色：白 */
  --color-foreground: #000000;    /* 文字色：黒 */
  --color-heading: #000000;       /* 見出し色：黒 */
  --color-hr: #4472C4;            /* 水平線：青（#4472C4） */
  --font-default: 'Meiryo', sans-serif;
}

/* ========================================
   2. スライド全体のスタイル
   ======================================== */
section {
  background-color: var(--color-background);
  color: var(--color-foreground);
  font-family: var(--font-default);
  font-weight: 400;
  box-sizing: border-box;
  position: relative;
  line-height: 1.7;
  font-size: 22px;
  padding: 110px 56px 40px 56px;  /* 上 右 下 左（上だけ120pxに増加） */
  display: flex;
  flex-direction: column;
  justify-content: flex-start;  /* 上寄せ（デフォルト） */
}

/* ========================================
   3. 見出しのスタイル
   ======================================== */
h1, h2, h3, h4, h5, h6 {
  font-weight: 700;
  color: var(--color-heading);
  margin: 0;
  padding: 0;
}

h1 {
  font-size: 40px;
  line-height: 1.4;
  text-align: left;
}

h2 {
  position: absolute;
  top: 40px;
  left: 56px;
  right: 56px;
  font-size: 40px;
  padding-top: 0;
  padding-bottom: 16px;
}

h2::after {
  content: '';
  position: absolute;
  left: 0;
  bottom: 8px;
  width: 100%;
  height: 1.75pt;
  background-color: var(--color-hr);
}

h2 + * {
  margin-top: 0px;
}

h3 {
  color: var(--color-foreground);
  font-size: 28px;
  margin-top: 32px;
  margin-bottom: 12px;
}

/* ========================================
   4. 基本要素（リスト、フッター、ヘッダー）
   ======================================== */
ul, ol {
  padding-left: 32px;
}

li {
  margin-bottom: 10px;
}

footer {
  position: absolute;
  left: 56px;
  right: 56px;
  bottom: 20px;
  font-size: 14px;
  color: var(--color-foreground);
  text-align: left;
  text-indent: 184px;
}

section:not(.title):not(.closing) footer {
  border-top: 1.75pt solid black;
  padding-top: 8px;
}

section:not(.title):not(.closing)::after {
  content: attr(data-marpit-pagination) '/' attr(data-marpit-pagination-total);
  position: absolute;
  left: 150px;
  bottom: 20px;
  font-size: 14px;
}

.title::after,
.closing::after,
.title footer,
.closing footer {
  display: none;
}

/* titleスライドのフッターを非表示 */
section.title footer {
  display: none !important;
}

header {
  position: absolute;
  top: 20px;
  left: 56px;
  font-size: 14px;
  color: var(--color-foreground);
}

/* ========================================
   5. 特殊スライド（タイトル、クロージング、装飾）
   ======================================== */
.company-logo {
  position: absolute;
  top: 30px;
  right: -80px;
  width: 180px;
  height: 50px;
  background-image: url('./assets/ロゴ.jpg');
  background-repeat: no-repeat;
  background-size: contain;
}

.slogan {
  position: absolute;
  bottom: 0;
  right: 60px;
  width: 180px;
  height: 40px;
  background-image: url('./assets/文字.jpg');
  background-repeat: no-repeat;
  background-size: contain;
}

/* === 目次スライド === */
.toc-container {
  display: flex;
  margin-top: 0;  /* 中央寄せ時に下にずれないよう0に変更 */
  font-size: 20px;
  gap: 40px;
}

.toc-column {
  flex: 1;
  padding-left: 0;
}

.toc-column:last-child {
  border-left: 1px solid #4472C4;
  padding-left: 40px;
}

/* Markdown内のulを正しく表示 */
.toc-column ul {
  margin: 0;
  padding-left: 32px;
  list-style-type: disc;
  list-style-position: outside;
}

.toc-column li {
  margin-bottom: 10px;
  display: list-item;
}

/* === タイトルスライド === */
section.title {
  background-image: url('./assets/タイトル背景full.png');
  background-size: cover;
  background-position: center;
  background-repeat: no-repeat;
  padding: 0 !important;
  position: relative;
  overflow: hidden;
}

/* 発表者情報クラス（空要素にCSSで内容を注入） */
.presentation-author::after {
  content: 'コーポレート\A生産プロセス革新・品質保証統括部\A生産革新技術部\A生産プロセス技術開発課\A木戸　優花\A Email: kido.yuka@ebara.com';
  white-space: pre;
  display: block;
}

.presentation-author {
  position: absolute;
  left: 56px;
  bottom: 56px;
  text-align: left;
  font-size: 22px;
  z-index: 9999;
  line-height: 1.4;
  color: #000000;
}

.presentation-title {
  position: absolute;
  left: 1.12cm;
  top: 6.87cm;
  width: 30cm;
  max-width: 100%;
  font-size: 40px;
  font-weight: bold;
  color: var(--color-heading);
  z-index: 10;
  line-height: 1.4;
}

.presentation-subtitle {
  position: absolute;
  left: 1.12cm;
  top: 8.5cm;
  width: 30cm;
  max-width: 100%;
  font-size: 32px;
  font-weight: normal;
  color: var(--color-heading);
  z-index: 10;
}

section.closing {
  background-image: url('./assets/最後背景full.png');
  background-size: cover;
  background-position: center;
  background-repeat: no-repeat;
  padding: 0 !important;
  position: relative;
  overflow: hidden;
}

/* クロージングメッセージをCSSで自動挿入 */
section.closing::before {
  content: '　　　　　　　　　　　　　　　　　ありがとうございました。';
  position: absolute;
  left: 1.12cm;
  right: 1.12cm;
  top: 50%;
  transform: translateY(-50%);
  font-size: 40px;
  font-weight: bold;
  z-index: 10;
  color: #000000;
}

.toc-link {
  position: absolute;
  right: 120px;
  top: 55px;
  font-size: 22px;
  font-weight: normal;
}

/* ========================================
   1. ボックス単体の定義
   ======================================== */

/* --- 情報ボックス（標準：通常の情報用） --- */
.box-info {
  background-color: transparent;
  border-radius: 10px;
  padding: 20px;
  margin-bottom: 20px;
}

.box-info h3 {
  color: var(--color-foreground);
  margin: 0 0 15px 0;
  font-size: 22px;
}

.box-info p {
  font-size: 22px;
  margin: 0;
  line-height: 1.6;
}

/* --- 情報ボックス（中：やや重要な情報用） --- */
.box-info-mid {
  background-color: #f5f5f5;
  border-radius: 10px;
  padding: 20px;
  margin-bottom: 20px;
}

.box-info-mid h3 {
  color: var(--color-foreground);
  margin: 0 0 15px 0;
  font-size: 22px;
}

.box-info-mid p {
  font-size: 22px;
  margin: 0;
  line-height: 1.6;
}


/* --- 情報ボックス（高：スライド内で最も重要な情報用） --- */
.box-info-high {
  background-color: #e6eff9;
  border-radius: 15px;
  padding: 30px;
  border-left: 6px solid #4472C4;
  margin-bottom: 25px;
}

.box-info-high h3 {
  color: #4472C4;
  margin: 0 0 20px 0;
  font-size: 26px;
}

/* --- 対比ボックス（前：課題・問題点用） --- */
.box-contrast-bad {
  background-color: #fff5f5;
  border-radius: 15px;
  padding: 30px;
  border-left: 6px solid #f44336;
  margin-bottom: 25px;
}

.box-contrast-bad h3 {
  color: #d32f2f;
  margin: 0 0 20px 0;
  font-size: 26px;
}

/* --- 対比ボックス（後：解決・改善用） --- */
.box-contrast-good {
  background-color: #e8f5e9;
  border-radius: 15px;
  padding: 30px;
  border-left: 6px solid #4caf50;
  margin-bottom: 25px;
}

.box-contrast-good h3 {
  color: #2e7d32;
  margin: 0 0 20px 0;
  font-size: 26px;
}

/* --- 最重要ボックス（プレゼン全体で最も重要） --- */
.box-critical {
  background-color: #e6eff9;
  border-radius: 15px;
  padding: 25px;
  text-align: center;
  border: 3px solid #4472C4;
}

.box-critical p {
  font-size: 24px;
  margin: 0;
  font-weight: bold;
  color: #4472C4;
}

/* --- カードボックス（薄いグレー背景） --- */
.box-card {
  background-color: #f5f5f5;
  border-radius: 10px;
  padding: 20px;
  text-align: center;
}

.box-card .icon {
  font-size: 36px;
  margin: 0 0 10px 0;
}

.box-card .title {
  font-size: 20px;
  font-weight: bold;
  margin: 0 0 10px 0;
}

.box-card .description {
  font-size: 18px;
  margin: 0;
}

/* --- ステップボックス --- */
.box-step {
  background-color: #f5f5f5;
  border-radius: 15px;
  padding: 15px;
  display: flex;
  flex-direction: column;
  position: relative;
}

.box-step .step-number {
  position: absolute;
  top: -10px;
  left: 15px;
  background-color: #4472C4;
  color: white;
  width: 30px;
  height: 30px;
  border-radius: 50%;
  display: flex;
  align-items: center;
  justify-content: center;
  font-weight: bold;
  font-size: 18px;
  margin: 0;
}

.box-step .step-title {
  font-size: 20px;
  font-weight: bold;
  margin-bottom: 10px;
  color: #4472C4;
  margin-top: 10px;
}

.box-step .step-description {
  font-size: 18px;
  margin: 0;
  text-align: left;
  flex-grow: 1;
  display: flex;
  flex-direction: column;
  justify-content: center;
}

/* --- セリフボックス（誰かがしゃべっている言葉用） --- */
.box-line-left {
  position: relative;
  display: inline-block;
  padding: 12px 20px;
  margin: 0px 0 10px 20px;
  max-width: auto;
  color: #333;
  background: #f3f3f3ff;
  border: 2px solid #ccc;
  border-radius: 12px;
  text-align: left;
  line-height: 1.5;
}

.box-line-left:before,
.box-line-left:after {
  content: "";
  position: absolute;
  top: 10px;
  right: 100%;
  border: solid transparent;
  height: 0;
  width: 0;
  pointer-events: none;
}

.box-line-left:after {
  border-color: rgba(243, 243, 243, 0);
  border-right-color: #f3f3f3ff;
  border-width: 10px;
  margin-top: 0px;
}

.box-line-left:before {
  border-color: rgba(204, 204, 204, 0);
  border-right-color: #ccc;
  border-width: 12px;
  margin-top: -2px;
}

.box-line-left p {
  margin: 0;
  padding: 0;
}

/* --- セリフボックス（右側：返答・回答用） --- */
.box-line-right {
  position: relative;
  display: inline-block;
  padding: 12px 20px;
  margin: 0 20px 10px 0;
  max-width: auto;
  color: #333;
  background: #d4f4dd;
  border: 2px solid #8bc98b;
  border-radius: 12px;
  text-align: left;
  line-height: 1.5;
}

.box-line-right:before,
.box-line-right:after {
  content: "";
  position: absolute;
  top: 10px;
  left: 100%;
  border: solid transparent;
  height: 0;
  width: 0;
  pointer-events: none;
}

.box-line-right:after {
  border-color: rgba(212, 244, 221, 0);
  border-left-color: #d4f4dd;
  border-width: 10px;
  margin-top: 0px;
}

.box-line-right:before {
  border-color: rgba(139, 201, 139, 0);
  border-left-color: #8bc98b;
  border-width: 12px;
  margin-top: -2px;
}

.box-line-right p {
  margin: 0;
  padding: 0;
}

/* --- キーポイントボックス --- */
.box-key {
  position: absolute;
  bottom: 56px;
  left: 56px;
  right: 56px;
  background-color: #E6EFF9;
  border-left: 6px solid #4472C4;
  padding: 20px 24px 20px 85px;
  border-radius: 4px;
  font-size: 20px;
  line-height: 1.5;
  z-index: 10;
}

.box-key::before {
  content: "💡";
  position: absolute;
  left: 20px;
  top: 50%;
  transform: translateY(-50%);
  font-size: 40px;
  color: #4472C4;
}

/* ========================================
   1. レイアウトの定義
   ======================================== */

/* グリッドレイアウト：総幅優先で各要素のブロック幅を変えたり複数の行や列になってよい場合 */

/* --- グリッドレイアウト（列） --- */
.layout-grid-2 {
  display: grid;
  grid-template-columns: 1fr 1fr;
  row-gap: 25px;     /* 縦方向（行間）の余白 */
  column-gap: 15px;  /* 横方向（列間）の余白 */
}

.layout-grid-3 {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  row-gap: 20px;     /* 縦方向（行間）の余白 */
  column-gap: 10px;  /* 横方向（列間）の余白 */
}

.layout-grid-4 {
  display: grid;
  grid-template-columns: repeat(4, 1fr);
  row-gap: 15px;     /* 縦方向（行間）の余白 */
  column-gap: 10px;  /* 横方向（列間）の余白 */
}

/* --- グリッドレイアウト（行） --- */
.layout-grid-row-2 {
  display: grid;
  grid-template-rows: 1fr 1fr;
  grid-auto-flow: column;  /* 行が埋まったら次の列へ */
  row-gap: 15px;     /* 縦方向（行間）の余白 */
  column-gap: 25px;  /* 横方向（列間）の余白 */
}

.layout-grid-row-3 {
  display: grid;
  grid-template-rows: 1fr 1fr 1fr;
  grid-auto-flow: column;  /* 行が埋まったら次の列へ */
  row-gap: 10px;     /* 縦方向（行間）の余白 */
  column-gap: 20px;  /* 横方向（列間）の余白 */
}

/* フレックスレイアウト：各要素のブロック幅優先で1列に収めたく、総幅を変えてよい場合 */

/* --- フレックスレイアウト（横並び） --- */
.layout-flex {
  display: flex;
  gap: 20px;
  justify-content: center;
}

/* --- フレックスレイアウト（縦並び） --- */
.layout-flex-column {
  display: flex;
  flex-direction: column;
  gap: 20px;
  align-items: center;
}

/* ========================================
   垂直方向の配置調整
   ======================================== */

/* --- スライド全体を縦方向に中央寄せ --- */
section.v-center {
  justify-content: center;
}

/* --- スライド全体を縦方向に下寄せ --- */
section.v-bottom {
  justify-content: flex-end;
}

</style>

<!-- ▼ ▼ ▼ ▼ ▼ ▼ ▼ ▼ ▼ ▼ ▼ 以下スライド ▼ ▼ ▼ ▼ ▼ ▼ ▼ ▼ ▼ ▼ ▼ -->

<!-- タイトルスライド -->
<!-- _class: title -->
<!-- _paginate: false -->

<div class="presentation-title">プレゼンテーションタイトル</div>
<div class="presentation-subtitle">～サブタイトルをここに記入～</div>
<div class="presentation-author"></div>

---

<!-- _class: v-center -->

## 目次

<a id="slide-toc" style="position: absolute; top: 0"></a>

<div class="company-logo"></div>
<div class="slogan"></div>

<div class="toc-container">
<div class="toc-column">

- P.03 [セクション1](#slide-section1)
- P.04 [セクション2](#slide-section2)
- P.05 [セクション3](#slide-section3)

</div>
<div class="toc-column">

- P.06 [セクション4](#slide-section4)
- P.07 [セクション5](#slide-section5)
- P.08 [まとめ](#slide-summary)

</div>
</div>

---

## 基本スライド

<a id="slide-section1" style="position: absolute; top: 0"></a>

<div class="company-logo"></div>
<div class="slogan"></div>
<span class="toc-link"><a href="#slide-toc">目次に戻る</a></span>

ここに内容を記載します。

---



## サンプル1: 情報ボックス（通常）

<div class="company-logo"></div>
<div class="slogan"></div>
<span class="toc-link"><a href="#slide-toc">目次に戻る</a></span>

<div style="margin-top: 0px; line-height: 1.7; text-align: left; max-width: 100%; margin: 0 auto;">

<div class="box-info">
<h3>📝 標準の情報</h3>
<p>
標準的な情報をここに記載します。背景色なし、地の文に近い表示です。
</p>
</div>

</div>

---

## サンプル2: 情報ボックス（やや重要）

<div class="company-logo"></div>
<div class="slogan"></div>
<span class="toc-link"><a href="#slide-toc">目次に戻る</a></span>

<div style="margin-top: 0px; line-height: 1.7; text-align: left; max-width: 100%; margin: 0 auto;">

<div class="box-info-mid">
<h3>📋 やや重要な情報</h3>
<p>
少しだけ重要な情報をここに記載します。薄いグレーの背景で視覚的に区別します。
</p>
</div>

</div>

---

## サンプル3: 情報ボックス（重要）

<div class="company-logo"></div>
<div class="slogan"></div>
<span class="toc-link"><a href="#slide-toc">目次に戻る</a></span>

<div style="margin-top: 0px; line-height: 1.7; text-align: left; max-width: 100%; margin: 0 auto;">

<div class="box-info-high">
<h3>💡 スライド内で最も重要な情報</h3>
<p style="font-size: 20px; margin: 0; line-height: 1.6;">
このスライドで最も重要な情報やポイントをここに記載します。青色で目立たせることができます。
</p>
</div>

</div>

---

## サンプル4: 対比ボックス（前：課題・問題点）

<div class="company-logo"></div>
<div class="slogan"></div>
<span class="toc-link"><a href="#slide-toc">目次に戻る</a></span>

<div style="margin-top: 0px; line-height: 1.7; text-align: left; max-width: 100%; margin: 0 auto;">

<div class="box-contrast-bad">
<h3>⚠️ Before：課題・問題点</h3>
<p style="font-size: 20px; margin: 0; line-height: 1.6;">
改善前の課題や問題点、注意すべき事項をここに記載します。赤色で警告として表示されます。対比ボックス（後）とセットで使用します。
</p>
</div>

</div>

---

## サンプル5: 対比ボックス（後：解決・改善策）

<div class="company-logo"></div>
<div class="slogan"></div>
<span class="toc-link"><a href="#slide-toc">目次に戻る</a></span>

<div style="margin-top: 0px; line-height: 1.7; text-align: left; max-width: 100%; margin: 0 auto;">

<div class="box-contrast-good">
<h3>✅ After：解決・改善策</h3>
<p style="font-size: 20px; margin: 0; line-height: 1.6;">
改善後の解決策や改善提案、成功事例などをここに記載します。緑色でポジティブな印象を与えます。対比ボックス（前）とセットで使用します。
</p>
</div>

</div>

---

## サンプル6: 最重要ボックス（プレゼン全体で最も重要）

<div class="company-logo"></div>
<div class="slogan"></div>
<span class="toc-link"><a href="#slide-toc">目次に戻る</a></span>

<div style="margin-top: 0px; line-height: 1.7; text-align: left; max-width: 100%; margin: 0 auto;">

<div class="box-critical">
<p>プレゼン全体で最も重要なメッセージをここに記載</p>
</div>

</div>

---

## サンプル7: カードボックス

<div class="company-logo"></div>
<div class="slogan"></div>
<span class="toc-link"><a href="#slide-toc">目次に戻る</a></span>

<div style="margin-top: 0px; line-height: 1.7; text-align: left; max-width: 100%; margin: 0 auto;">

<div class="box-card">
<div class="icon">📊</div>
<div class="title">カードタイトル</div>
<div class="description">カードの説明文がここに入ります</div>
</div>

</div>

---

## サンプル8: ステップボックス

<div class="company-logo"></div>
<div class="slogan"></div>
<span class="toc-link"><a href="#slide-toc">目次に戻る</a></span>

<div style="margin-top: 0px; line-height: 1.7; text-align: left; max-width: 100%; margin: 0 auto;">

<div class="box-step">
<div class="step-number">01</div>
<div class="step-title">ステップタイトル</div>
<div class="step-description">このステップの説明文がここに入ります</div>
</div>

</div>

---

## サンプル9: セリフボックス（発言・引用用）

<div class="company-logo"></div>
<div class="slogan"></div>
<span class="toc-link"><a href="#slide-toc">目次に戻る</a></span>

<div style="margin-top: 0px; line-height: 1.7; text-align: left; max-width: 100%; margin: 0 auto;">

<div class="box-line-left">
誰かがしゃべっている言葉をここに記載します------------------
</div>

<div class="box-line-right">
誰かがしゃべっている言葉をここに記載します------------------
</div>

</div>

---

## サンプル10: キーポイントボックス

<div class="company-logo"></div>
<div class="slogan"></div>
<span class="toc-link"><a href="#slide-toc">目次に戻る</a></span>

<div style="margin-top: 0px; line-height: 1.7; text-align: left; max-width: 100%; margin: 0 auto;">

通常のコンテンツがここに入ります。

</div>

<div class="box-key">
スライド下部に固定表示される重要ポイント
</div>

---

## サンプル11: グリッドレイアウト（2列）

<div class="company-logo"></div>
<div class="slogan"></div>
<span class="toc-link"><a href="#slide-toc">目次に戻る</a></span>

<div style="margin-top: 0px; line-height: 1.7; text-align: left; max-width: 100%;">

<div class="layout-grid-2">
  <div class="box-card">
    <div class="icon">📊</div>
    <div class="title">項目1</div>
    <div class="description">説明文1</div>
  </div>
  <div class="box-card">
    <div class="icon">📈</div>
    <div class="title">項目2</div>
    <div class="description">説明文2</div>
  </div>
  <div class="box-card">
    <div class="icon">📈</div>
    <div class="title">項目2</div>
    <div class="description">説明文2</div>
  </div>
</div>

</div>

---

## サンプル12: グリッドレイアウト（3列）

<div class="company-logo"></div>
<div class="slogan"></div>
<span class="toc-link"><a href="#slide-toc">目次に戻る</a></span>

<div style="margin-top: 0px; line-height: 1.7; text-align: left; max-width: 100%;">

<div class="layout-grid-3">
  <div class="box-card">
    <div class="icon">📊</div>
    <div class="title">項目1</div>
    <div class="description">説明1</div>
  </div>
  <div class="box-card">
    <div class="icon">📈</div>
    <div class="title">項目2</div>
    <div class="description">説明2</div>
  </div>
  <div class="box-card">
    <div class="icon">📉</div>
    <div class="title">項目3</div>
    <div class="description">説明3</div>
  </div>
  <div class="box-card">
    <div class="icon">📉</div>
    <div class="title">項目3</div>
    <div class="description">説明3</div>
  </div>
</div>

</div>

---

## サンプル13: グリッドレイアウト（4列）

<div class="company-logo"></div>
<div class="slogan"></div>
<span class="toc-link"><a href="#slide-toc">目次に戻る</a></span>

<div style="margin-top: 0px; line-height: 1.7; text-align: left; max-width: 100%;">

<div class="layout-grid-4">
  <div class="box-step">
    <div class="step-number">01</div>
    <div class="step-title">Step1</div>
  </div>
  <div class="box-step">
    <div class="step-number">02</div>
    <div class="step-title">Step2</div>
  </div>
  <div class="box-step">
    <div class="step-number">03</div>
    <div class="step-title">Step3</div>
  </div>
  <div class="box-step">
    <div class="step-number">04</div>
    <div class="step-title">Step4</div>
  </div>
  <div class="box-step">
    <div class="step-number">04</div>
    <div class="step-title">Step4</div>
  </div>
</div>

</div>

---

## サンプル14: フレックスレイアウト（gap可変）

<div class="company-logo"></div>
<div class="slogan"></div>
<span class="toc-link"><a href="#slide-toc">目次に戻る</a></span>

<div style="margin-top: 0px; line-height: 1.7; text-align: left; max-width: 100%; margin:">

<div class="layout-flex" style="gap: 20px">
  <div class="box-card">
    <div class="icon">📊</div>
    <div class="title">項目A</div>
  </div>
  <div class="box-card">
    <div class="icon">📈</div>
    <div class="title">項目B</div>
  </div>
  <div class="box-card">
    <div class="icon">📉</div>
    <div class="title">項目C</div>
  </div>
</div>
</div>

---

## サンプル17: フレックスレイアウト（縦並び）

<div class="company-logo"></div>
<div class="slogan"></div>
<span class="toc-link"><a href="#slide-toc">目次に戻る</a></span>

<div style="margin-top: 0px; line-height: 1.7; text-align: left; max-width: 100%; margin: 0 auto;">

<div class="layout-flex-column" style="gap: 20px">
  <div class="box-card">
    <div class="icon">📊</div>
    <div class="title">項目A</div>
  </div>
  <div class="box-card">
    <div class="icon">📈</div>
    <div class="title">項目B</div>
  </div>
  <div class="box-card">
    <div class="icon">📉</div>
    <div class="title">項目C</div>
  </div>
</div>

</div>

---

## サンプル15: グリッドレイアウト（2行）

<div class="company-logo"></div>
<div class="slogan"></div>
<span class="toc-link"><a href="#slide-toc">目次に戻る</a></span>

<div style="margin-top: 0px; line-height: 1.7; text-align: left; max-width: 100%; margin: 0 auto;">

<div class="layout-grid-row-2">
  <div class="box-card">
    <div class="icon">📊</div>
    <div class="title">項目A</div>
  </div>
  <div class="box-card">
    <div class="icon">📈</div>
    <div class="title">項目B</div>
  </div>
  <div class="box-card">
    <div class="icon">📈</div>
    <div class="title">項目B</div>
  </div>
</div>

</div>

---

## サンプル16: グリッドレイアウト（3行）

<div class="company-logo"></div>
<div class="slogan"></div>
<span class="toc-link"><a href="#slide-toc">目次に戻る</a></span>

<div style="margin-top: 0px; line-height: 1.7; text-align: left; max-width: 100%; margin: 0 auto;">

<div class="layout-grid-row-3">
  <div class="box-card">
    <div class="icon">📊</div>
    <div class="title">項目1</div>
    <div class="description">説明1</div>
  </div>
  <div class="box-card">
    <div class="icon">📈</div>
    <div class="title">項目2</div>
    <div class="description">説明2</div>
  </div>
  <div class="box-card">
    <div class="icon">📉</div>
    <div class="title">項目3</div>
    <div class="description">説明3</div>
  </div>
  <div class="box-card">
    <div class="icon">📉</div>
    <div class="title">項目3</div>
    <div class="description">説明3</div>
  </div>
</div>

</div>

---

<!-- クロージングスライド -->
<!-- _class: closing -->
<!-- _paginate: false -->

<a id="slide-closing" style="position: absolute; top: 0"></a>
