[English](README.md) | 日本語

# apple-hig-design

Apple の Human Interface Guidelines (HIG) を、Claude が UI 設計の判断に使えるリファレンスにした Claude Code スキルです。

## これは何ですか

Apple の Human Interface Guidelines(HIG、Apple 公式のデザインガイドライン)は、iOS / iPadOS / macOS / tvOS / visionOS / watchOS 向けアプリの見た目や振る舞いについて Apple が定めた公式ルールブックです。ボタンのサイズ、余白、モーダルを使うべき場面、ダークモードの仕様などが書かれています。

Claude Code の「スキル」とは、指示文とリファレンスファイルをまとめたフォルダで、Claude Code がタスクの内容に応じて自動的に読み込むものです。コマンドで起動する必要はありません。インストールされている各スキルの短い説明を Claude があらかじめ把握しておき、依頼の内容が合致したときだけ本体を読み込みます。

このスキルは、HIG の1トピックにつき1ファイル、合計158件のリファレンスを Claude に提供します。各ファイルには Apple の実際の記述と実際の数値がそのまま入っています。「タップ標的はたぶん44ポイントくらい」と記憶で答える代わりに、Claude は該当ファイルを開いて Apple が公開している数値をそのまま引用します。プラットフォームごとの例外(たとえばタップ標的は iOS では44ポイントですが、visionOS では60ポイントです)も含まれています。各トピックには「Web translation」というセクションもあり、これは本プロジェクト独自の解釈で、ネイティブの原則を Web の UI にどう当てはめられるかを書いたものです。Apple は Web 向けの指針を書いていないため、このセクションは Apple の記述ではなく派生物であると明示してあります。

## どんな人向けですか

Apple のネイティブプラットフォーム向けであれ Web アプリであれ、Claude Code に UI の設計・実装・レビューを依頼し、Claude の記憶ではなく Apple の実際の文書に基づいた回答を求める人向けです。

このスキルがあることで Claude が正確に答えられる質問の例です。

- 「この iOS のシート表示、HIG 的に正しいですか?」
- 「この Web のモーダル、Apple の考え方に沿って設計するとどうなりますか?」
- 「visionOS のタップ標的の最小サイズはいくつですか?」
- 「シートとアラート、どちらを使うべきですか?」
- 「サイドバーの階層はどこまで深くしてよいですか?」
- 「これはアクセシビリティ的に十分ですか?」

## 何が入っているか

```
apple-hig-design/
├── README.md                     # この文書（英語版）
├── SKILL.md                      # ルーターファイル。Claude はまずこれを読みます
├── NOTICE.md                     # 権利関係。フォークや再配布の前に読んでください
├── LICENSE
├── README.ja.md / SKILL.ja.md / NOTICE.ja.md   # 日本語版
└── references/
    ├── INDEX.md                # 全158トピックの索引
    ├── getting-started/        #   9件  プラットフォーム別の設計入門
    ├── foundations/            #  18件  タイポグラフィ、カラー、レイアウト、アクセシビリティ等
    ├── patterns/               #  25件  モーダル、検索、オンボーディング等の設計パターン
    ├── inputs/                 #  13件  ジェスチャ、キーボード、Digital Crown 等の入力
    ├── technologies/           #  29件  Apple Pay、HealthKit、SharePlay 等の技術連携
    └── components/             #  64件  UI 部品。8つのサブフォルダに分かれています
        ├── content/                       #  4件
        ├── layout-and-organization/       # 10件
        ├── menus-and-actions/             # 12件
        ├── navigation-and-search/         #  5件
        ├── presentation/                  #  8件
        ├── selection-and-input/           # 11件
        ├── status/                        #  4件
        └── system-experiences/            # 10件
```

合計は 9 + 18 + 25 + 13 + 29 + 64 = 158 トピックです。

各リファレンスファイルは同じ構成になっています。

| セクション | 内容 |
|---|---|
| `Core guidance` | Apple の指示文と、その理由。数値は丸めず省略せずそのまま記載しています |
| `Platform considerations` | iOS / iPadOS / macOS / tvOS / visionOS / watchOS 間の違い |
| `Specifications` | 仕様表。Apple の原文に表がある場合のみ収録しています |
| `Native implementation` | SwiftUI / UIKit / AppKit の API 名と、Apple 公式ドキュメントへのリンク |
| `Web translation *(derived — not from Apple)*` | ネイティブの原則を本プロジェクトが独自に Web の UI に読み替えたもの。Apple の記述ではありません |
| `Do / Don't` | 対比表 |

言語についての注意です。`references/` 配下のリファレンスは、Apple の用語や API 名と一致させるため英語で書かれています。この README、NOTICE、SKILL、索引ファイルには日本語版（`*.ja.md`）もあります。

## 必要な環境

- Claude Code がインストールされ、動作していること。
- `git`。クローンでインストールする場合に必要です。別の方法でファイルを取得する場合は不要です。

## 導入手順

1. リポジトリを手元にクローンします。

   ```bash
   git clone https://github.com/y-128/apple-hig-design.git
   cd apple-hig-design
   mkdir -p ~/.claude/skills
   ```

   このコマンドで `apple-hig-design` という名前のフォルダが作られ、その中にもう1つ `apple-hig-design` という名前のフォルダがあります。`SKILL.md` を直接含んでいるのは内側のフォルダです。`cd` で外側のフォルダに移動し、`mkdir -p` でスキル用のフォルダがまだなければ作成します。

2. スキルを Claude Code のスキルディレクトリにリンクします。2つの方法があります。

   **方法A: シンボリックリンク**(`git pull` で更新した際にも反映されます)

   ```bash
   ln -s "$(pwd)/apple-hig-design" ~/.claude/skills/apple-hig-design
   ```

   **方法B: コピー**(シンボリックリンクを使いたくない場合。ただし更新は自動反映されません)

   ```bash
   cp -R "$(pwd)/apple-hig-design" ~/.claude/skills/apple-hig-design
   ```

   グローバルではなくプロジェクト単位で導入したい場合は、`~/.claude/skills/apple-hig-design` の代わりに、プロジェクト内の `.claude/skills/apple-hig-design` を使ってください。

3. リンク先が正しいか確認します。

   ```bash
   ls ~/.claude/skills/apple-hig-design/SKILL.md
   ```

   「No such file or directory」と表示された場合、リンクの階層が1段階ずれています。`~/.claude/skills/apple-hig-design` 自体に `SKILL.md` があるか、それとも中にもう1つ `apple-hig-design` フォルダがあってその中に `SKILL.md` があるかを確認してください。

4. Claude Code を再起動するか、新しいセッションを開始してください。スキルはセッション開始時に読み込まれるため、起動中のセッションでは今インストールしたスキルは認識されません。

## 使い方

明示的に呼び出す必要はありません。Claude Code はインストールされている各スキルの短い説明を読んでおり、タスクが UI 設計に関連すると自ら判断したときに、通常の会話の中で自動的にこのスキルの内容を読み込みます。

自動的にトリガーされる依頼の例です。

- 「この iOS のシート表示を HIG に照らしてレビューして」
- 「visionOS のタップ標的の最小サイズは?」
- 「この画面のダークモードはどう実装すべき?」

意図的に使わせたい場合は、スキル名を直接指定してください。「apple-hig-design スキルを使ってこれを確認して」のように依頼します。トリガーされると、Claude はまず `references/INDEX.md` を読んで該当トピックを探し、その後は必要なファイルだけを開きます。1つの質問のために158件すべてを読み込むことはありません。

## 既知の制約

リファレンスファイルは、Apple の HIG ページから抽出したテキストを基に生成しています。原典の一部は抽出できていません。該当箇所には `Source limitation` として明記してあり、欠落を推測で埋めることはしていません。

| 制約 | 具体例 |
|---|---|
| 複数タブを持つ JavaScript ウィジェットは最初のタブしか取得できていない | Dynamic Type のサイズ表。最初のサイズグループしか収録されておらず、Large から AX5 までの全段階はありません |
| 一部のトピックには Apple が公開する Change log がない | 158件中43件は frontmatter の `last_updated` が `unknown` になっています |
| 画像・図版は抽出できていない | Icons の Standard icons 表には、ラベルと SF Symbol 名のみが載っており、画像自体はありません |
| 対話型の before/after ウィジェットは中身が失われている | Spatial layout トピックの before/after 実演部分 |

158件中65件のファイルに、少なくとも1つの `Source limitation` の注記があります。

## 更新と鮮度について

このスキルは Apple のサイトと自動的に同期しているわけではありません。内容は2026年7月時点のスナップショットで、2026年9月9日の改訂分(「Designing for iPhone Duo」の新設、Layout・Branding・SharePlay の更新)のみ追加で反映しています。

ファイルの frontmatter にある `last_updated` が古い場合や `unknown` になっている場合、あるいは重要な判断をする場合は、そのファイルの frontmatter の `url` を確認し、Apple の最新ページと照合してから利用してください。

## 用語集

- **HIG(Human Interface Guidelines)**: Apple 各プラットフォーム向けの公式デザインガイドラインです。
- **スキル(skill)**: Claude Code がタスクに応じて自動的に読み込む、指示文とリファレンス素材をまとめたフォルダです。
- **SwiftUI / UIKit / AppKit**: Apple の UI フレームワークです。SwiftUI は現行のクロスプラットフォームフレームワーク、UIKit は iOS / iPadOS / tvOS 向けの旧来のフレームワーク、AppKit は macOS 向けの旧来のフレームワークです。
- **ポイント(pt)**: Apple の UI 測定単位です。論理的な単位であり、画面の密度によって実際のピクセル数への対応が変わります。固定のピクセル数とは異なります。
- **Dynamic Type**: ユーザーがアプリ内の文字サイズをまとめて拡大・縮小できる、Apple の仕組みです。読みやすさとアクセシビリティのためのものです。
- **SF Symbols**: Apple がシステムフォントに合わせて用意しているアイコンライブラリで、Dynamic Type に合わせて拡大縮小します。
- **Liquid Glass**: 半透明で光を屈折させる、Apple の現行のマテリアルデザイン言語です。システム UI 全体で使われています。
- **Frontmatter**: 各リファレンスファイルの先頭にある、YAML 形式のメタデータ(title、url、platforms、last_updated など)のブロックです。

## ライセンス

本プロジェクトの原著作物(スキル構造、`Web translation` セクション、この文書)は MIT ライセンスです。詳細は [LICENSE](LICENSE) を参照してください。

**Apple の HIG に由来する記述は MIT ライセンスの対象外です。** これらは引き続き `Human Interface Guidelines © Apple Inc. All rights reserved.` の対象です。このリポジトリをフォークまたは再配布する前に [NOTICE.ja.md](NOTICE.ja.md) を読んでください。MIT ライセンスの対象範囲と、Apple の権利の扱いを説明しています。

本プロジェクトは Apple Inc. と一切の関係を持たず、Apple による承認・後援を受けていません。
