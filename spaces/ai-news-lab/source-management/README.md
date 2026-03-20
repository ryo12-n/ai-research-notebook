# ソース管理 (Source Management)

情報ソースの探索・評価・管理を継続的に回すための基盤。
「何を見に行くか」を体系的に管理し、ソースの質を定期的に評価する。

## ディレクトリ構成

| ディレクトリ/ファイル | 用途 |
|---------------------|------|
| `source-list.md` | マスターソースリスト（全ソースの一覧・ステータス管理） |
| `evaluation-criteria.md` | AI評価軸の定義（Perplexity がスコアリングに参照） |
| `discovery-log/` | 新ソース発見の記録 |
| `evaluation-log/` | 個別ソースの評価結果の蓄積 |
| `review-log/` | 四半期レビューの記録 |
| `templates/` | 各種テンプレート |

## ワークフロー（3層サイクル）

### 随時: ソース発見

新しい情報ソースを発見したら記録し、候補として登録する。

1. `templates/source-discovery-template.md` をコピーして `discovery-log/YYYY-MM-DD-*.md` を作成
2. 発見経路・ソース情報・初期印象を記入
3. candidate として追加するソースを `source-list.md` に登録（ステータス: `candidate`）

### 隔週: ソース評価

trial ステータスのソースを評価する。人間のフィードバックを AI がスコアリングする2層構造。

1. `templates/source-evaluation-template.md` をコピーして `evaluation-log/YYYY-MM-DD-S-XXX.md` を作成
2. **人間**: 「人間フィードバック」セクションに自由記述でフィードバックを記入
3. **Perplexity**: `evaluation-criteria.md` を参照し、フィードバックから各軸のスコアを判定して「AIスコアリング結果」セクションに記入
4. 総合スコアに基づいてステータス変更を提案
5. 決定したステータス変更を `source-list.md` に反映

### 四半期: 全ソースレビュー

全ソースを横断的にレビューし、カバレッジの評価と次の探索テーマを決定する。

1. `templates/quarterly-review-template.md` をコピーして `review-log/YYYY-MM-DD-quarterly-review.md` を作成
2. 全 active/trial ソースのスコア推移をまとめる
3. カテゴリ別カバレッジを評価し、ギャップを特定
4. 次四半期の探索テーマを提案
5. ステータス変更を決定し、`source-list.md` に反映

## ステータス遷移

```
candidate → trial → active
                  ↘ inactive ← active
                  ↘ removed  ← inactive
                               ← trial
```

| ステータス | 説明 |
|-----------|------|
| `candidate` | 新規発見。未評価 |
| `trial` | 試用中（2週間〜1ヶ月） |
| `active` | 定常的に参照するソース |
| `inactive` | 一時的に参照停止 |
| `removed` | 完全除外 |

遷移の詳細は `source-list.md` のステータス定義セクションを参照。

## 既存タスクとの接続点

| 既存タスク | 接続 |
|-----------|------|
| daily-source-pickup | pickup 結果から新ソースを発見 → discovery-log に記録 |
| daily-curation | キュレーション品質がソース評価の入力になる |
| weekly-trend-review | トレンド振り返り時にソースの速報性・カバレッジを確認 |
| monthly-analysis | 月次分析の「情報源の追加・削除案」セクションと連動 |

## テンプレート一覧

| テンプレート | 用途 | 使用頻度 |
|-------------|------|---------|
| `source-discovery-template.md` | 新ソース発見記録 | 随時 |
| `source-evaluation-template.md` | 個別ソース評価（人間FB + AIスコアリング） | 隔週 |
| `quarterly-review-template.md` | 四半期全ソースレビュー | 四半期 |
