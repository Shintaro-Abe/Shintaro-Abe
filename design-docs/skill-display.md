# 技術スタック表示設計

## 方針

テキストバッジではなく、アイコングリッドで技術スタックを一目で伝える。

## Skill Icons（主要手段）

[skillicons.dev](https://skillicons.dev) を使用。48x48 のアイコングリッドを一発で生成できる。

```html
<p align="center">
  <a href="https://skillicons.dev">
    <img src="https://skillicons.dev/icons?i=aws,gcp,terraform,ansible,docker,linux,bash,py,git,githubactions&perline=5" />
  </a>
</p>
```

### パラメータ

| パラメータ | 説明 |
|-----------|------|
| `i=` | カンマ区切りのアイコン ID |
| `&perline=N` | 1行あたりのアイコン数（1〜50、デフォルト 15） |
| `&theme=` | `light` or `dark`（デフォルト: dark） |

### 利用するアイコン ID

| カテゴリ | アイコン ID |
|----------|-----------|
| Cloud | `aws`, `gcp` |
| IaC / 構成管理 | `terraform`, `ansible` |
| コンテナ / CI/CD | `docker`, `githubactions` |
| 言語 / シェル | `py`, `bash` |
| OS / インフラ | `linux` |
| ツール | `git` |

## shields.io バッジ（補助手段）

Skill Icons でカバーできない技術（Serverless Framework 等）は shields.io バッジで補完する。

### URL 形式

```
https://img.shields.io/badge/{テキスト}-{色コード}?logo={slug}&logoColor=white&style=for-the-badge
```

### 検証済み Simple Icons スラッグと色

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

### AWS に関する注意

AWS は Simple Icons から削除されている。`amazonwebservices`, `aws` 等のスラッグは存在しない。
AWS バッジを作る場合はロゴなしでテキストと色のみで表現するか、Skill Icons (`aws`) を使う。
