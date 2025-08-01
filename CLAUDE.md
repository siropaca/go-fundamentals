# Go Fundamentals - 学習プロジェクト

## プロジェクト概要

このリポジトリは TypeScript 中級者の Web アプリケーションエンジニアが、1ヶ月で Go 言語のジュニアエンジニアレベルを目指すための学習プロジェクトです。

## 対象者

- TypeScript/JavaScript/Node.js の実務経験がある
- Go 言語は未経験
- Web アプリケーション開発の基礎知識がある

## 学習アプローチ

1. **TypeScript との比較を重視**: 既存の知識を活かしながら Go の特徴を理解
2. **実践的な学習**: 記事での解説と実際に動くコードをセットで学習
3. **段階的な習得**: 基礎から応用まで順番に積み上げ

## カリキュラム構成

### 基礎編（第0章〜第6章）
- **00-introduction**: Go 言語の概要と歴史
- **01-basics**: 基本文法（変数、型、演算子）
- **02-control-flow**: 制御構文（if、switch、for）
- **03-functions**: 関数（基本、複数戻り値、可変長引数）
- **04-data-structures**: データ構造（配列、スライス、マップ、構造体）
- **05-methods-interfaces**: メソッドとインターフェース
- **06-pointers**: ポインタ

### 実践編（第7章〜第11章）
- **07-error-handling**: エラーハンドリング
- **08-concurrency**: 並行処理（ゴルーチン、チャネル）
- **09-packages-modules**: パッケージとモジュール管理
- **10-testing**: テスト（ユニットテスト、ベンチマーク）
- **11-standard-library**: 標準ライブラリの活用

## 学習の進め方

1. 各章の README.md で概要を把握
2. サンプルコードを実際に動かして理解を深める
3. TypeScript との違いを意識しながら学習
4. 練習問題で知識を定着させる

## 学習時間の目安

- 1章あたり: 2-3日
- 全体: 約1ヶ月（週5日、1日1-2時間の学習を想定）

## 技術環境

- Go: 1.23.11（mise で管理）
- エディタ: 任意（VS Code 推奨）

## 今後の拡張予定

基礎編と実践編の学習が完了したら、以下の応用編を追加予定：
- Web フレームワーク（Echo、Gin など）
- データベース連携
- REST API 開発
- gRPC

## 記事作成のガイドライン

各章の README.md を作成する際は、以下のルールに従ってください：

### 重要：章別の指示を確認
**各章のディレクトリに @CLAUDE.md ファイルが配置されているので、必ずその内容を参照してから作業を開始してください。**
章別の @CLAUDE.md には、その章のカリキュラム、指示や注意事項が記載されています。

### 執筆者と読者の設定
- **あなたは Go のシニアエンジニアです**
- TypeScript エンジニアに Go の魅力と実用性を伝える立場で執筆
- **読者は TypeScript 中級者の Web アプリケーションエンジニア**

### 文章のトーン
- **オライリーの技術書ような品質で**：たまにはユーモアを交えつつ、技術的な正確性を重視
- **親しみやすい口調**：堅苦しくなりすカジュアルすぎず、技術的な正確性は保つ

### 記事の構成
- **TypeScript との比較**：既存の知識と関連付けて説明
- **実践的なコード例**：動かしてすぐ理解できるサンプル
- **よくあるミスや落とし穴**：初学者がハマりやすいポイント
- **コラムなどの挿入**：Go のユニークな特徴や歴史的背景を紹介
- **まとめ**：その章で学んだことの振り返り

### 情報の正確性
- **憶測や推測を避ける**：記事や技術的な説明を書く際は、憶測の情報を使用しない
- **最新情報の取得**：Web 検索や公式ドキュメント、信頼できるソースから最新の情報を取得して記載する
- **公式ドキュメント**：https://go.dev/doc/ を参照して正確な情報を提供する
- **バージョン情報の明記**：Go のバージョンに依存する機能については、対象バージョンを明確に記載する
