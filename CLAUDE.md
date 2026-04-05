# CLAUDE.md

## 目的

スキルと資格の視認性に優れた GitHub プロフィールページを構築する。
訪問者が最初の 3 秒で技術領域と資格レベルを把握できるページを目指す。

## リポジトリ構成

```
Shintaro-Abe/
├── README.md                           # プロフィールページ本体
├── certificates/                       # 資格認定証明書 PDF
├── images/                             # プロフィール画像・ロゴ
├── design-docs/                        # 設計書（永続的ドキュメント）
│   ├── rendering-constraints.md        # GitHub 描画エンジンの制約
│   ├── skill-display.md                # 技術スタック表示設計
│   ├── certification-display.md        # 資格表示設計
│   ├── layout.md                       # レイアウト・GitHub Stats 設計
│   └── issues.md                       # 現状の課題と対応方針
├── docs/                               # 職務経歴書
│   ├── README.md                       # 職務経歴書
│   └── _config.yml                     # Jekyll 設定（GitHub Pages）
├── pdf-configs/                        # PDF 生成設定
└── .github/workflows/                  # Zenn ブログ記事の自動取得（毎時）
```

## 方針

### セクション構成（優先度順）

README.md のセクションは以下の順序で配置する。Above the Fold にスキルと資格の要約を置く。

1. **ヘッダー** — プロフィールバナー画像
2. **基本情報** — 名前・居住地・学歴・技術記事リンク
3. **技術スタック** — Skill Icons のアイコングリッドで一覧表示
4. **資格一覧** — カテゴリ別、レベル色分けバッジで表示
5. **GitHub Stats** — 活動状況の可視化
6. **ブログ記事** — GitHub Actions で自動更新
7. **SNS リンク** — フッターにアイコン行で配置

### 視認性の原則

- スキルはテキストではなくアイコングリッドで表現する
- 資格レベルはバッジの色で即座に判別可能にする
- セクション間に十分な余白を確保し、情報の塊を明確に区別する
- 見出しにはカテゴリのロゴ画像を付与する

### 編集ルール

- README.md 本文は日本語で記述する
- コミットメッセージは英語で記述する
- リンクパスはフォワードスラッシュ（`/`）に統一する
- `<!-- BLOG-POST-LIST:START -->` 〜 `<!-- BLOG-POST-LIST:END -->` 間は GitHub Actions が自動更新するため手動編集しない

## 設計書

`design-docs/` 配下の設計書は永続的ドキュメントとする。
アプリケーション全体の「**何を作るか**」「**どう作るか**」を定義する恒久的なドキュメント。
アプリケーションの基本設計や方針が変わらない限り更新されません。

| 設計書 | 内容 |
|--------|------|
| [rendering-constraints.md](design-docs/rendering-constraints.md) | GitHub が許可する HTML タグ・属性・描画幅の制約 |
| [skill-display.md](design-docs/skill-display.md) | Skill Icons・shields.io による技術スタック表示 |
| [certification-display.md](design-docs/certification-display.md) | 資格バッジの色分けルール・セクション構成 |
| [layout.md](design-docs/layout.md) | レイアウトパターン・GitHub Stats カード |
| [issues.md](design-docs/issues.md) | 現状の課題と対応方針 |
