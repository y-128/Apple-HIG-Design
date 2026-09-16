---
name: apple-hig-design
description: Apple Human Interface Guidelines の全157トピックを、Apple の実際の記述と具体的な数値ごと参照できるリファレンス集。UI を設計・実装・レビューするとき、コンポーネントを選ぶとき、タイポグラフィ・カラー・レイアウト・モーション・アクセシビリティを判断するときに必ず使う。iOS / iPadOS / macOS / tvOS / visionOS / watchOS のアプリ開発、SwiftUI・UIKit・AppKit のコンポーネント選定はもちろん、Web の UI でも使う。ネイティブ原則を Web に読み替える指針を全トピックに併記してあるため、「Apple」「HIG」と明示されない依頼でも参照すること。たとえば「このモーダルの出し方どうするのが自然?」「ボタンのタップ領域どれくらい必要?」「ダークモード対応したい」「シートとアラートどっち?」「サイドバーの階層どこまで深くしていい?」「アクセシビリティ的にこれで大丈夫?」といった問いは、すべてこのスキルが答えを持っている。記憶に頼って数値を答える前に、必ずここを引く。
---

# Apple HIG リファレンス

Apple Human Interface Guidelines を、設計判断に使える形にした157トピックのリファレンス集。

このスキルの目的は、**記憶で答えないこと**にある。「タップ標的は44ポイント」のような数値は覚えていても、visionOS では60ポイントであること、Dynamic Type の各段階でどう変わるか、macOS には Dynamic Type がないことまでは正確に思い出せない。ここには Apple が実際に書いている値がそのまま入っている。

## 使い方

1. **`references/INDEX.md` を読む。** 全157トピックの一覧と1行要約がある。
2. **該当するトピックの `.md` だけを読む。** 157件すべてを読み込む必要はないし、読んではいけない。
3. 数値を引用するときは、そのファイルに書かれている値をそのまま使う。丸めたり近似したりしない。

`.ja.md` は日本語版で、内容確認用に併置してある。**作業では英語版を正とする。** Apple の用語（Dynamic Type、SF Symbols、Liquid Glass など）は英語が一次表記であり、API 名やドキュメントと一致させる必要があるため。

## 分類

| フォルダ | 件数 | 何が入っているか |
|---|---|---|
| `getting-started/` | 8 | 各プラットフォームの性格と、設計の出発点になる原則 |
| `foundations/` | 18 | タイポグラフィ、カラー、レイアウト、マテリアル、モーション、アクセシビリティ |
| `patterns/` | 25 | モーダル、検索、オンボーディング、ローディング等の設計パターン |
| `components/` | 64 | UI 部品。7分類（下記） |
| `inputs/` | 13 | ジェスチャ、キーボード、ポインタ、Digital Crown、視線 |
| `technologies/` | 29 | Apple Pay、HealthKit、SharePlay 等の技術連携 |

`components/` の内訳: `content` / `layout-and-organization` / `menus-and-actions` / `navigation-and-search` / `presentation` / `selection-and-input` / `status` / `system-experiences`

## よく引くトピック

| 判断したいこと | 見るファイル |
|---|---|
| タップ標的の最小サイズ | `components/menus-and-actions/buttons.md` |
| 文字サイズ、Dynamic Type、行送り | `foundations/typography.md` |
| 色の使い方、システムカラー | `foundations/color.md` |
| ダークモード | `foundations/dark-mode.md` |
| 余白、セーフエリア、適応レイアウト | `foundations/layout.md` |
| Liquid Glass、すりガラス、半透明 | `foundations/materials.md` |
| アニメーションの是非と時間 | `foundations/motion.md` |
| コントラスト比、支援技術 | `foundations/accessibility.md` |
| モーダルにすべきか | `patterns/modality.md` |
| シート / アラート / ポップオーバーの選択 | `components/presentation/` の各ファイル |
| タブバーとサイドバーの使い分け | `components/navigation-and-search/` |
| フォーム、入力欄、トグル | `components/selection-and-input/` |
| 読み込み中の見せ方 | `patterns/loading.md`, `components/status/progress-indicators.md` |
| UI 文言の書き方 | `foundations/writing.md` |
| 右横書き言語への対応 | `foundations/right-to-left.md` |

## 各リファレンスの構成

| セクション | 中身 |
|---|---|
| `Core guidance` | Apple の指示文とその理由。数値は原文どおり |
| `Platform considerations` | プラットフォーム間の差分 |
| `Specifications` | 仕様表（原典に表がある場合のみ） |
| `Native implementation` | SwiftUI / UIKit / AppKit の API 名と公式ドキュメント |
| `Web translation` | Web への読み替え。**下記の注意を読むこと** |
| `Do / Don't` | 対比表 |

## Web 案件で使うときの注意

`Web translation` セクションは **Apple 由来ではない**。HIG に Web の指針は一切含まれていないため、ネイティブ原則から読み替えた派生物である。見出しに `*(derived — not from Apple)*` と明示してある。

このセクションを引くときは、Apple の規定として提示しないこと。「Apple はこう考えている、それを Web に当てはめるとこうなる」という二段構えで扱う。

読み替えが成立しないトピックも多い。visionOS の空間レイアウト、watchOS のコンプリケーション、Apple Pay の決済ハードウェアなどは、正直に「Web に対応物がない」と書いてある。**そう書いてあるトピックについて、無理に Web の実装を提案しない。**

## 原典の限界

リファレンスは PDF から抽出したテキストを基にしており、原典の一部が取得できていない。該当箇所には `Source limitation` と明記してある。**推測で埋めていない。**

主な欠落:

- **Dynamic Type のサイズ表** — Apple のページはタブ切り替えで7段階＋AX1〜AX5を出し分けるが、PDF には各グループの先頭タブしか印刷されていない。既定サイズ（Large）の表が存在しない
- **システムカラーの色値** — 色はスウォッチ画像で描画されており、16進数・RGB値が抽出できない。色名と API 識別子のみ
- **Change log** — 157件中44件には Apple 自身が改訂履歴を公開していない。`last_updated: unknown` としている

`Source limitation` が書かれているトピックについて具体値を求められたら、**その値は手元にないと伝え、frontmatter の `url` から Apple の一次情報を確認するよう案内する。** もっともらしい数値を作らない。

## このスキルが古くなる条件

各ファイルの `last_updated` は Apple の Change log の最終エントリであり、収録は2026年7月時点のスナップショットである。Apple は HIG を随時更新するため、**このスキルは自動追随しない。**

`last_updated` が古い、あるいは `unknown` のトピックで重要な判断をするときは、`url` から現行版を確認すること。特に Liquid Glass 関連は改訂が続いている領域である。
