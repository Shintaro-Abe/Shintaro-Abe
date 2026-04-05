# 資格表示設計

## 方針

資格レベルを色で即座に判別可能にする。shields.io の `for-the-badge` スタイルで統一する。

## AWS 認定資格の色分けルール

| レベル | 色コード | 色 | 対象資格 |
|--------|----------|------|----------|
| Foundational | `696969` | グレー | Cloud Practitioner, AI Practitioner |
| Associate | `0033FF` | 青 | SA Associate, Developer, SysOps, Data Engineer, ML Engineer |
| Professional | `00CCCC` | シアン | DevOps Professional, SA Professional |
| Specialty | `6600CC` | 紫 | Security, Database, Data Analytics, ML, Networking, SAP |

## バッジ URL の例

```
https://img.shields.io/badge/AWS-Solutions_Architect_Professional-00CCCC?style=for-the-badge
https://img.shields.io/badge/AWS-Cloud_Practitioner-696969?style=for-the-badge
https://img.shields.io/badge/AWS-Security_Specialty-6600CC?style=for-the-badge
```

## セクション構成

資格はカテゴリ別に分ける:

1. **AWS 認定資格** — 15 資格。レベル色分けで視覚的に整理
2. **Google Cloud 認定資格** — Generative AI Leader
3. **Linux 技術者認定試験** — LPIC-1 / LPIC-2 / LPIC-3
4. **Cisco 認定試験** — CCNA

各セクションの見出しにはカテゴリのロゴ画像を使用する（幅 3%〜5%）。

## 証明書リンク

各資格から `certificates/` ディレクトリ内の PDF へリンクする。
パスはフォワードスラッシュ（`/`）で統一する。
