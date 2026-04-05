# GitHub README 描画エンジンの制約

README.md を編集する前に、GitHub の描画仕様を正確に理解すること。

## 使用可能な HTML タグ（主要なもの）

`div`, `table`, `thead`, `tbody`, `tr`, `td`, `th`, `img`, `a`, `p`, `h1`〜`h6`,
`details`, `summary`, `picture`, `source`, `br`, `hr`, `sup`, `sub`, `strong`, `em`, `code`, `pre`

## 使用可能な属性

- `align` — `center`, `left`, `right`（`<div>`, `<td>`, `<p>`, `<h1>` 等で有効）
- `width`, `height` — `<img>` のサイズ指定
- `colspan`, `rowspan` — テーブルセルの結合
- `media` — `<source>` でダークモード対応に使用
- `srcset` — `<source>` で画像切替に使用

## 使用不可（ストリップされる）

- **`style` 属性** — 完全に除去される。インライン CSS は一切効かない
- **`class` 属性** — 除去される
- `<style>`, `<script>`, `<iframe>` タグ

## 描画領域

- 最大幅: **830px**（リポジトリ/プロフィールビュー）
- レスポンシブ: モバイルではさらに狭くなる。横に並べすぎると折り返しが崩れる

## ダークモード対応

`<picture>` + `<source>` で対応可能:

```html
<picture>
  <source media="(prefers-color-scheme: dark)" srcset="dark-image.png">
  <source media="(prefers-color-scheme: light)" srcset="light-image.png">
  <img alt="fallback" src="light-image.png">
</picture>
```

## 折りたたみセクション

`<details>` + `<summary>` が使用可能。情報量が多いセクションの整理に有効:

```html
<details>
  <summary>詳細を表示</summary>
  折りたたまれた内容
</details>
```
