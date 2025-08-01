# 第2章: 制御構文 - カリキュラムプラン

## 学習目標

- Go の条件分岐（if、switch）を習得する
- for ループの様々なパターンを理解する
- TypeScript との制御構文の違いを把握する
- Go 特有の制御フローを活用できる

## 学習内容の概要

### 1. if文
- 基本的な if-else
- 初期化付き if 文
- 条件の連鎖
- エラーハンドリングパターン

### 2. switch文
- 基本的な switch
- 複数の case 値
- 条件なし switch
- 型 switch（interface{} の章で詳細）
- fallthrough の使用

### 3. forループ
- 標準的な for ループ
- while 風の for ループ
- 無限ループ
- range を使った反復（配列・スライスの章で詳細）
- break と continue

### 4. その他の制御
- goto 文（非推奨だが存在する）
- defer 文の基礎（関数の章で詳細）

## TypeScriptとの比較ポイント

- while ループが存在しない（for で代用）
- foreach が range になる
- switch の break が不要（自動的に break）
- 初期化付き if 文という独特な構文

## 作成予定のコンテンツ

### 説明記事
- `if-statement.md`: if 文の詳細と活用パターン
- `switch-statement.md`: switch 文の様々な使い方
- `for-loop.md`: for ループの全パターン
- `control-flow-patterns.md`: Go らしい制御フローの書き方

### サンプルコード
- `conditionals/`: if と switch の実例
- `loops/`: 様々な for ループパターン
- `early-return/`: 早期リターンパターン
- `typescript-comparison/`: TypeScript との比較例

### 練習問題
- FizzBuzz の実装
- 簡単な数当てゲーム
- 条件分岐を使った成績判定
- ループを使った数列生成

## 学習時間の目安

- 全体: 3-4時間
- if と switch の理解: 1.5時間
- for ループの習得: 1時間
- 練習問題: 1-1.5時間