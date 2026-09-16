# apple-hig-design

Apple Human Interface Guidelines を Claude が設計判断に使える形にした Claude Code スキル。

UI を設計・実装・レビューするとき、Claude に「visionOS のボタンは最小何ポイントか」「モーダルをいつ使うべきか」を**記憶ではなく Apple の実際の記述から**答えさせるためのもの。ネイティブアプリだけでなく Web 実装でも使えるよう、各トピックに「ネイティブ原則を Web に読み替える指針」を併記している。

## 何が入っているか

HIG の全157トピックについて、英語のリファレンスと日本語全訳を1対1で収録している。

```
apple-hig-design/
├── SKILL.md                  # ルーター。Claude はまずこれを読む
├── LICENSE
├── NOTICE.md                 # 権利関係。再配布前に必ず読む
└── references/
    ├── INDEX.md              # 全157件の索引
    ├── getting-started/      #   8件  プラットフォーム別の設計入門
    ├── foundations/          #  18件  タイポグラフィ、カラー、レイアウト、アクセシビリティ等
    ├── patterns/             #  25件  モーダル、検索、オンボーディング等の設計パターン
    ├── inputs/               #  13件  ジェスチャ、キーボード、Digital Crown 等の入力
    ├── technologies/         #  29件  Apple Pay、HealthKit、SharePlay 等の技術連携
    └── components/           #  64件  ボタン、シート、タブバー等の UI 部品（7分類）
```

各リファレンスの構成:

| セクション | 内容 |
|---|---|
| `Core guidance` | Apple の指示文と、その理由。数値は一切省略しない |
| `Platform considerations` | iOS / iPadOS / macOS / tvOS / visionOS / watchOS の差分 |
| `Specifications` | 仕様表（原典に表がある場合のみ） |
| `Native implementation` | SwiftUI / UIKit / AppKit の API 名と公式ドキュメントへの導線 |
| `Web translation` | ネイティブ原則の Web への読み替え。**Apple 原文ではなく本プロジェクトの派生物** |
| `Do / Don't` | 対比表 |

日本語版は `<topic>.ja.md` として併置してある。内容確認用であり、**実作業では英語版を正とする**（Apple の用語は英語が一次表記のため）。

## 導入

Claude Code のスキルディレクトリに配置する。

```bash
git clone https://github.com/y-128/apple-hig-design.git
ln -s "$(pwd)/apple-hig-design" ~/.claude/skills/apple-hig-design
```

`~/.claude/skills/` 配下に置けば、Claude Code が自動的に認識する。個別の設定は不要。

配置後の確認:

```bash
ls -l ~/.claude/skills/apple-hig-design/SKILL.md
```

## 使い方

明示的に呼び出す必要はない。UI 設計・実装の文脈で Claude が自動的に参照する。

意図的に使わせたい場合は、依頼に文脈を添える。

- 「iOS アプリのシート表示、HIG 的に正しいか見て」
- 「この Web のモーダル、Apple の考え方だとどう設計すべき?」
- 「visionOS のタップ標的の最小サイズは?」

Claude は `references/INDEX.md` で該当トピックを引き、必要なファイルだけを読む。157件すべてを読み込むことはない。

## 既知の制約

リファレンスは PDF から抽出したテキストを基に生成しているため、原典の一部が取得できていない。該当箇所には `Source limitation` として明記してあり、**欠落を推測で埋めることはしていない**。

| 制約 | 具体例 |
|---|---|
| JavaScript タブの2番目以降が未取得 | Typography の Dynamic Type サイズ表。既定サイズ（Large）の表が存在しない |
| Change log が原典にない | 157件中44件。`last_updated: unknown` としている |
| 画像・図版が抽出不可 | Icons の Standard icons 表はラベルと SF Symbol 名のみ |
| 対話ウィジェットの中身が消失 | Spatial layout の before/after 実演 |

`last_updated` が古い、あるいは `unknown` のトピックについては、frontmatter の `url` から Apple の一次情報を確認すること。**このスキルは Apple の更新に自動追随しない。**

## 再生成

手元に HIG の PDF がある場合、リファレンスを作り直せる。`scripts/` の手順に従う。生成には Claude Code のサブエージェントを使う。

## ライセンス

原著作物（スキル構造、`Web translation` セクション、スクリプト）は MIT。

**Apple HIG に由来する記述は MIT の対象外**であり、`Human Interface Guidelines © Apple Inc. All rights reserved.` に従う。再配布する前に [NOTICE.md](NOTICE.md) を必ず読むこと。権利関係と、公開範囲を決めるための選択肢を整理してある。

本プロジェクトは Apple Inc. と関係を持たず、Apple による承認・後援を受けていない。
