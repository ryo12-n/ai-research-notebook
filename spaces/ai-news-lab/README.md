# AI News Lab

AI分野の最新動向を追跡・分析するためのリサーチノートスペースです。

## ディレクトリ構成

| ディレクトリ | 用途 |
|-------------|------|
| `weekly-trend-review/` | Perplexity 週間トレンド振り返りの出力格納（毎週金曜） |
| `daily-source-pickup/` | Perplexity 情報源別ニュースピックアップの出力格納（毎日） |
| `daily-curation/` | Perplexity AIニュースキュレーションの出力格納（毎日） |
| `daily-clips/` | 日々のAIニュースクリッピング（手動） |
| `deep-dives/` | 特定テーマの深堀り調査プロジェクト |
| `resources/` | ツール・論文・データセットのリファレンス |
| `templates/` | ノート作成用テンプレート |

## タグ運用ルール

| タグ | 用途 |
|------|------|
| `#LLM` | 大規模言語モデル関連 |
| `#CV` | コンピュータビジョン |
| `#RL` | 強化学習 |
| `#MLOps` | ML運用・インフラ |
| `#Research` | 学術研究 |
| `#Product` | 製品・サービス |
| `#Industry` | 業界動向 |

## ワークフロー

### Perplexity 定期実行タスクの出力格納

Perplexity の定期実行タスクが生成した md ファイルを、対応するディレクトリに手動アップロードする。

1. Perplexity の出力を md ファイルとしてダウンロード
2. 対応するテンプレート（`templates/` 配下）を参考にファイル名を `YYYY-MM-DD-*.md` 形式にする
3. 対応するディレクトリに格納する
   - 週間トレンド振り返り → `weekly-trend-review/`
   - 情報源別ピックアップ → `daily-source-pickup/`
   - AIニュースキュレーション → `daily-curation/`

### 分析サイクル

蓄積した Perplexity 出力をもとに、定期的な振り返り・分析を行う。

1. **毎週**: `templates/weekly-analysis-template.md` を使って週次振り返りを作成
2. **毎月**: `templates/monthly-analysis-template.md` を使って月次振り返りを作成
3. 分析テンプレートの「次回の調査に向けて」セクションで、次の調査サイクルへの改善点を記録する

### 手動ワークフロー

1. **毎日**: `daily-clips/` に新しいクリップを追加
2. **深堀り**: テーマが見つかったら `deep-dives/` にプロジェクトフォルダを作成
3. **リソース蓄積**: 有用なリソースを発見したら `resources/` の該当ファイルに追記

## テンプレート一覧

| テンプレート | 用途 |
|-------------|------|
| `weekly-trend-review-template.md` | 週間トレンド振り返り出力用 |
| `daily-source-pickup-template.md` | 情報源別ニュースピックアップ出力用 |
| `daily-curation-template.md` | AIニュースキュレーション出力用 |
| `weekly-analysis-template.md` | 週次分析・振り返り用 |
| `monthly-analysis-template.md` | 月次分析・振り返り用 |
| `daily-clip-template.md` | 日次ニュースクリッピング用 |
| `deep-dive-template.md` | 深堀り調査用 |

## 検索のヒント

- ファイル名は `YYYY-MM-DD-トピック名.md` 形式で統一
- YAML frontmatter でメタデータ管理
- タグで横断的にテーマ検索が可能
