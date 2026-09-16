# NOTICE — 第三者コンテンツと権利について

このリポジトリを GitHub などで再配布する前に読んでください。

## このリポジトリには2種類のコンテンツが混在している

**1. 原著作物（MIT ライセンス）**

- `SKILL.md`、`references/INDEX.md`、各フォルダの `_index.md`
- 各リファレンスの `## Web translation *(derived — not from Apple)*` セクション全文
- ディレクトリ構造、frontmatter スキーマ、生成・検証スクリプト

これらは本リポジトリの著者が書いたもので、[LICENSE](LICENSE) の MIT ライセンスに従う。

**2. Apple Human Interface Guidelines に由来する記述（MIT ライセンスの対象外）**

各リファレンスの `Core guidance` / `Platform considerations` / `Specifications` / `Native implementation` / `Do / Don't` の各セクションは、Apple Inc. が公開する Human Interface Guidelines を要約・再構成したものである。

> Human Interface Guidelines © Apple Inc. All rights reserved.

Apple は HIG の再配布を許諾していない。**本リポジトリは Apple から HIG の再配布ライセンスを受けておらず、MIT ライセンスによって Apple のコンテンツの利用を許諾することもできない。**

## 承知しておくべきリスク

要約であっても、Apple の指示文（bold で書かれたルール文）や仕様表を原文に近い形で保持している箇所がある。事実データ（ポイントサイズ、コントラスト比などの数値）は一般に著作権保護が弱いが、**指示文の言い回しは Apple の表現であり、保護され得る**。

157件という網羅的な規模は、この点でリスクを上げる方向に働く。一部を引用する行為と、ガイドライン全体の代替物を作る行為は、法的な評価が異なる。

公開リポジトリとして配布する場合、これは理論上の懸念ではなく、Apple から削除要請（DMCA takedown）を受け得る現実的な可能性である。判断は利用者に委ねられる。

## リスクを下げたい場合の選択肢

| 方針 | 内容 |
|---|---|
| プライベートリポジトリ | 個人・チーム内利用に限定する。最も安全 |
| 生成スクリプトのみ公開 | リファレンス本体は配布せず、利用者が手元の PDF から生成する形にする |
| Web セクションのみ公開 | 原著作物だけを配布し、Apple 由来部分は除く |
| そのまま公開 | 教育目的・出典明示・非商用を明記したうえで、削除要請には速やかに応じる |

## 免責と帰属

- 本プロジェクトは Apple Inc. と一切の関係を持たず、Apple による承認・後援・提携を受けていない。
- Apple、iOS、iPadOS、macOS、tvOS、visionOS、watchOS、SwiftUI、UIKit、AppKit、SF Symbols、Liquid Glass、Dynamic Type ほか本文中の名称は Apple Inc. の商標である。
- 各リファレンスの frontmatter に記載した `url` が一次情報であり、**常にそちらが正となる**。本リポジトリの記述は取得時点のスナップショットであり、Apple による更新に追随しない。
- リファレンスは PDF から機械的に抽出したテキストを基に生成しており、原典の一部（JavaScript タブの2番目以降、画像、対話ウィジェット）は取得できていない。該当箇所には `Source limitation` として明記してある。

## 削除要請について

Apple Inc. またはその代理人から連絡があった場合、該当コンテンツを速やかに削除する。連絡先はリポジトリの Issues を参照。
