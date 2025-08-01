# 第11章: 標準ライブラリ - カリキュラムプラン

## 学習目標

- Go の豊富な標準ライブラリを活用できるようになる
- よく使うパッケージの使い方を習得する
- 標準ライブラリのドキュメントを読めるようになる
- Node.js の標準モジュールとの対応を理解する

## 学習内容の概要

### 1. 入出力（I/O）
- fmt パッケージ（フォーマット付き I/O）
- io パッケージ（基本的な I/O インターフェース）
- ioutil/os パッケージ（ファイル操作）
- bufio パッケージ（バッファ付き I/O）

### 2. データ処理
- encoding/json（JSON の処理）
- encoding/csv（CSV の処理）
- encoding/xml（XML の処理）
- regexp パッケージ（正規表現）

### 3. ネットワーク
- net/http（HTTP クライアント/サーバー）
- net パッケージ（低レベルネットワーク）
- url パッケージ（URL の解析）

### 4. 時間とコンテキスト
- time パッケージ（時間の操作）
- context パッケージ（キャンセレーションとタイムアウト）

### 5. その他の重要なパッケージ
- strings パッケージ（文字列操作）
- strconv パッケージ（文字列変換）
- sort パッケージ（ソート）
- crypto パッケージ（暗号化）

## TypeScriptとの比較ポイント

- Node.js 標準モジュール vs Go 標準ライブラリ
- 外部依存の必要性の違い
- API の設計哲学の違い
- エラーハンドリングの一貫性
- インターフェースベースの設計

## 作成予定のコンテンツ

### 説明記事
- `io-operations.md`: I/O 操作の基本
- `data-encoding.md`: データエンコーディング
- `http-basics.md`: HTTP 通信の基本
- `time-context.md`: 時間とコンテキスト管理
- `common-packages.md`: よく使うパッケージ一覧

### サンプルコード
- `file-operations/`: ファイル操作の例
- `json-handling/`: JSON 処理の実装
- `http-client-server/`: HTTP 通信の例
- `string-manipulation/`: 文字列処理
- `typescript-comparison/`: Node.js との比較

### 練習問題
- ログファイルの解析ツール
- REST API クライアントの作成
- CSV データの処理
- 簡単な Web サーバーの実装

## 学習時間の目安

- 全体: 5-6時間
- I/O とファイル操作: 1.5時間
- データ処理: 1.5時間
- ネットワーク: 1.5時間
- 練習問題: 1.5時間