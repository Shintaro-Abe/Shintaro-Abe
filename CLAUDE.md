# CLAUDE.md

## 目的

**スキルと資格の視認性に優れたGitHubプロフィールページを構築する。**

このリポジトリ（`Shintaro-Abe/Shintaro-Abe`）の `README.md` がGitHubプロフィールページとして描画される。
訪問者が「最初の3秒」で技術領域と資格レベルを把握できるページを目指す。

---

## リポジトリ構成

```
Shintaro-Abe/
├── README.md                           # プロフィールページ本体
├── certificates/                       # 資格認定証明書PDF
├── images/                             # プロフィール画像・ロゴ
├── docs/                               # 職務経歴書（Jekyll + GitHub Pages）
├── pdf-configs/                        # PDF生成設定
└── .github/workflows/                  # Zennブログ記事の自動取得（毎時）
```

---

## GitHub README 描画エンジンの制約

README.mdを編集する前に、GitHubの描画仕様を正確に理解すること。

### 使用可能なHTMLタグ（主要なもの）

`div`, `table`, `thead`, `tbody`, `tr`, `td`, `th`, `img`, `a`, `p`, `h1`〜`h6`,
`details`, `summary`, `picture`, `source`, `br`, `hr`, `sup`, `sub`, `strong`, `em`, `code`, `pre`

### 使用可能な属性

- `align` — `center`, `left`, `right`（`<div>`, `<td>`, `<p>`, `<h1>`等で有効）
- `width`, `height` — `<img>` のサイズ指定
- `colspan`, `rowspan` — テーブルセルの結合
- `media` — `<source>` でダークモード対応に使用
- `srcset` — `<source>` で画像切替に使用

### 使用不可（ストリップされる）

- **`style` 属性** — 完全に除去される。インラインCSSは一切効かない
- **`class` 属性** — 除去される
- `<style>`, `<script>`, `<iframe>` タグ

### 描画領域

- 最大幅: **830px**（リポジトリ/プロフィールビュー）
- レスポンシブ: モバイルではさらに狭くなる。横に並べすぎると折り返しが崩れる

### ダークモード対応

`<picture>` + `<source>` で対応可能:
```html
<picture>
  <source media="(prefers-color-scheme: dark)" srcset="dark-image.png">
  <source media="(prefers-color-scheme: light)" srcset="light-image.png">
  <img alt="fallback" src="light-image.png">
</picture>
```

### 折りたたみセクション

`<details>` + `<summary>` が使用可能。情報量が多いセクションの整理に有効:
```html
<details>
  <summary>詳細を表示</summary>
  折りたたまれた内容
</details>
```

---

## セクション構成（上から順に配置）

情報の優先度順に配置する。Above the Fold（スクロールなしで見える領域）にスキルと資格の要約を置く。

### 1. ヘッダー
- プロフィールバナー画像（`<div align="center">`で中央配置）

### 2. 基本情報
- 名前・居住地・学歴・技術記事リンク
- 簡潔に。テーブル形式で整理

### 3. 技術スタック（最重要セクション）
- **Skill Icons（skillicons.dev）を使用** してアイコングリッドで表示
- テキストバッジよりもアイコングリッドのほうが圧倒的に視認性が高い
- カテゴリごとに行を分けて配置

### 4. 資格一覧
- カテゴリ別（AWS / Google Cloud / Linux / Cisco）にセクション分け
- `for-the-badge` スタイルのshields.ioバッジで資格レベルを色分け表示
- 詳細（取得日・証明書リンク）は `<details>` で折りたたみ可能にする選択肢もある

### 5. GitHub Stats
- GitHub Readme Stats カードで活動状況を可視化

### 6. ブログ記事
- GitHub Actionsで自動更新

### 7. SNSリンク
- アイコン行で簡潔に

---

## 技術スタックの表示方法

### Skill Icons（推奨）

[skillicons.dev](https://skillicons.dev) を使用。48x48のアイコングリッドを一発で生成できる。

```html
<p align="center">
  <a href="https://skillicons.dev">
    <img src="https://skillicons.dev/icons?i=aws,gcp,terraform,ansible,docker,linux,bash,py,git,githubactions&perline=5" />
  </a>
</p>
```

**主要パラメータ:**
- `i=` — カンマ区切りのアイコンID
- `&perline=N` — 1行あたりのアイコン数（1〜50、デフォルト15）
- `&theme=light` or `dark`（デフォルト: dark）

**利用可能なアイコンID（このプロフィールで使用するもの）:**

| カテゴリ | アイコンID |
|----------|-----------|
| Cloud | `aws`, `gcp` |
| IaC / 構成管理 | `terraform`, `ansible` |
| コンテナ / CI/CD | `docker`, `githubactions` |
| 言語 / シェル | `py`, `bash` |
| OS / インフラ | `linux` |
| ツール | `git` |

### shields.io バッジ（補助的に使用）

Skill Iconsでカバーできない技術（Serverless Framework等）はshields.ioバッジで補完する。

**URL形式:**
```
https://img.shields.io/badge/{テキスト}-{色コード}?logo={slug}&logoColor=white&style=for-the-badge
```

**検証済みの Simple Icons スラッグと色:**

| 技術 | slug | 色 | 備考 |
|------|------|----|------|
| Google Cloud | `googlecloud` | `4285F4` | |
| Terraform | `terraform` | `844FBA` | |
| Ansible | `ansible` | `EE0000` | |
| Serverless | `serverless` | `FD5750` | |
| Python | `python` | `3776AB` | |
| Linux | `linux` | `FCC624` | `logoColor=black`（背景が黄色のため） |
| Docker | `docker` | `2496ED` | |
| Git | `git` | `F05032` | |
| GitHub Actions | `githubactions` | `2088FF` | |
| GNU Bash | `gnubash` | `4EAA25` | |

**重要: AWS は Simple Icons から削除されている。** `amazonwebservices`, `aws` 等のスラッグは存在しない。
AWSバッジを作る場合はロゴなしでテキストと色のみで表現するか、Skill Icons (`aws`) を使う。

---

## 資格バッジの色分けルール

shields.io の `for-the-badge` スタイルで統一。レベルを色で即座に判別可能にする。

| レベル | 色コード | 色 | 対象資格 |
|--------|----------|------|----------|
| Foundational | `696969` | グレー | Cloud Practitioner, AI Practitioner |
| Associate | `0033FF` | 青 | SA Associate, Developer, SysOps, Data Engineer, ML Engineer |
| Professional | `00CCCC` | シアン | DevOps Professional, SA Professional |
| Specialty | `6600CC` | 紫 | Security, Database, Data Analytics, ML, Networking, SAP |

**バッジの例:**
```
https://img.shields.io/badge/AWS-Solutions_Architect_Professional-00CCCC?style=for-the-badge
https://img.shields.io/badge/AWS-Cloud_Practitioner-696969?style=for-the-badge
https://img.shields.io/badge/AWS-Security_Specialty-6600CC?style=for-the-badge
```

---

## GitHub Stats カード

### GitHub Readme Stats（anuraghazra/github-readme-stats）

```html
<div align="center">
  <img src="https://github-readme-stats.vercel.app/api?username=Shintaro-Abe&show_icons=true&theme=tokyonight&hide_border=true&locale=ja" height="180" />
  <img src="https://github-readme-stats.vercel.app/api/top-langs/?username=Shintaro-Abe&layout=compact&theme=tokyonight&hide_border=true&locale=ja" height="180" />
</div>
```

**主要パラメータ:**
- `&theme=` — `tokyonight`, `radical`, `dark`, `transparent` 等（全カードで統一すること）
- `&hide_border=true` — 枠線非表示
- `&locale=ja` — 日本語表示
- `&show_icons=true` — アイコン表示

### GitHub Streak Stats（DenverCoder1/github-readme-streak-stats）

```html
<img src="https://streak-stats.demolab.com/?user=Shintaro-Abe&theme=tokyonight&hide_border=true&locale=ja" />
```

**注意:** Vercel の公開インスタンスはレート制限を受ける場合がある。画像が表示されなくなった場合はセルフホストを検討する。

---

## レイアウトパターン

### 中央配置

```html
<div align="center">
  <img src="..." />
</div>
```

### 2カラム横並び（Stats カード等）

```html
<div align="center">
  <img src="card1" height="180" />
  <img src="card2" height="180" />
</div>
```

`height` を揃えることで高さが統一される。830px幅で2枚並ぶには各カードを400px以下にする。

### カテゴリ別セクション見出し

```markdown
## <img src="images/AWS-Dark.svg" width="4%"> AWS認定資格
```

ロゴ画像の `width` は `3%`〜`5%` で統一する。

---

## README.md 編集ルール

### 記法
- 本文は日本語で記述
- HTMLタグでレイアウトを構成（`style` 属性は使えないため `align`, `width`, `height` で制御）
- リンクパスは **フォワードスラッシュ（`/`）に統一**（`\` は使わない）
- ファイル名にスペースを含むものはそのまま記述可（例: `"Shintaro Abe.png"`）

### 自動更新エリア（編集禁止）

```html
<!-- BLOG-POST-LIST:START -->
...（GitHub Actions が毎時自動更新）
<!-- BLOG-POST-LIST:END -->
```

### コミットメッセージ
- 英語で記述

---

## 現状の課題

| 課題 | 影響 | 対応方針 |
|------|------|----------|
| 技術スタックがテキストバッジのみ | スキルの全体像が一目で把握できない | Skill Icons のアイコングリッドに置換 |
| 資格テーブルが `flat-square` バッジ | 小さくて目立たない | `for-the-badge` スタイルに変更 |
| 一部パスがバックスラッシュ | Linux/macOS で証明書リンク切れの可能性 | フォワードスラッシュに統一 |
| GitHub Stats なし | 活動状況が見えない | Stats + Top Languages カードを追加 |
| SNSが中段に配置 | 技術情報の前に個人情報が来ている | フッターに移動 |
| ワークフローファイル名に末尾スペース | 潜在的な問題 | リネーム推奨 |
| ASCII アートが大きい | ページが冗長に見える | 削除（確認済み） |
