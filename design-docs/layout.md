# レイアウト・GitHub Stats 設計

## レイアウトパターン

### 中央配置

```html
<div align="center">
  <img src="..." />
</div>
```

### 2 カラム横並び（Stats カード等）

```html
<div align="center">
  <img src="card1" height="180" />
  <img src="card2" height="180" />
</div>
```

`height` を揃えることで高さが統一される。830px 幅で 2 枚並ぶには各カードを 400px 以下にする。

### カテゴリ別セクション見出し

```markdown
## <img src="images/AWS-Dark.svg" width="4%"> AWS認定資格
```

ロゴ画像の `width` は `3%`〜`5%` で統一する。

## GitHub Stats カード

### GitHub Readme Stats（anuraghazra/github-readme-stats）

```html
<div align="center">
  <img src="https://github-readme-stats.vercel.app/api?username=Shintaro-Abe&show_icons=true&theme=tokyonight&hide_border=true&locale=ja" height="180" />
  <img src="https://github-readme-stats.vercel.app/api/top-langs/?username=Shintaro-Abe&layout=compact&theme=tokyonight&hide_border=true&locale=ja" height="180" />
</div>
```

### 主要パラメータ

| パラメータ | 説明 |
|-----------|------|
| `&theme=` | `tokyonight`, `radical`, `dark`, `transparent` 等。全カードで統一する |
| `&hide_border=true` | 枠線非表示 |
| `&locale=ja` | 日本語表示 |
| `&show_icons=true` | アイコン表示 |

### GitHub Streak Stats（DenverCoder1/github-readme-streak-stats）

```html
<img src="https://streak-stats.demolab.com/?user=Shintaro-Abe&theme=tokyonight&hide_border=true&locale=ja" />
```

**注意:** Vercel の公開インスタンスはレート制限を受ける場合がある。画像が表示されなくなった場合はセルフホストを検討する。
