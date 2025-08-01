# 第9章: パッケージとモジュール - カリキュラムプラン

## 学習目標

- Go のパッケージシステムを理解する
- モジュールによる依存関係管理を習得する
- パッケージの公開・非公開ルールを把握する
- import の仕組みと使い方を学ぶ
- npm/yarn との違いを理解する

## 学習内容の概要

### 1. パッケージの基本
- パッケージの定義と命名規則
- main パッケージの特別な役割
- パッケージの初期化（init 関数）
- 同一パッケージ内でのファイル分割

### 2. インポートと公開性
- import 文の書き方
- エイリアスインポート
- ブランクインポート
- 大文字始まり = 公開、小文字始まり = 非公開

### 3. Go Modules
- go.mod ファイルの役割
- モジュールの初期化
- 依存関係の追加と更新
- バージョン管理
- go.sum ファイルの意味

### 4. パッケージの作成と公開
- 再利用可能なパッケージの設計
- ドキュメントコメントの書き方
- テスト可能な設計
- GitHub での公開方法

### 5. 標準的なプロジェクト構造
- cmd/ ディレクトリ
- internal/ パッケージ
- pkg/ vs internal/
- ベンダリング

## TypeScriptとの比較ポイント

- npm/yarn vs Go Modules
- package.json vs go.mod
- node_modules vs モジュールキャッシュ
- export/import vs 大文字ルール
- スコープとアクセス制御の違い

## 作成予定のコンテンツ

### 説明記事
- `packages.md`: パッケージの基本概念
- `imports.md`: import の詳細
- `go-modules.md`: Go Modules の使い方
- `project-structure.md`: プロジェクト構造のベストプラクティス
- `publishing.md`: パッケージの公開方法

### サンプルコード
- `basic-package/`: 基本的なパッケージ構造
- `multi-file-package/`: 複数ファイルのパッケージ
- `internal-package/`: internal パッケージの使用
- `module-example/`: モジュールの実例
- `typescript-comparison/`: TypeScript との比較

### 練習問題
- ユーティリティパッケージの作成
- 既存コードのパッケージ分割
- 外部パッケージの利用
- CLI ツールの作成

## 学習時間の目安

- 全体: 4-5時間
- パッケージの基本: 1.5時間
- Go Modules: 1.5時間
- プロジェクト構造: 1時間
- 練習問題: 1-1.5時間