# 開発環境セットアップガイド

いよいよ Go の世界に足を踏み入れる時が来ました！

TypeScript 開発で Node.js のバージョン管理に悩まされた経験があるなら、Go のセットアップの簡単さに驚くはずです。

## 🎯 このガイドで行うこと

1. mise を使った Go のインストール
2. VS Code の設定
3. Hello World プログラムの作成と実行
4. 開発効率を上げる Tips

## 📦 Go のインストール（mise 使用）

### なぜ mise？

TypeScript 開発では `nvm` や `volta` を使って Node.js のバージョンを管理しますよね。Go でも同様に、プロジェクトごとに異なるバージョンを使い分けたい場面があります。

このプロジェクトでは `mise`（旧 rtx）を使用しています。

### mise のインストール

```bash
# macOS (Homebrew)
$ brew install mise

# または、インストールスクリプト
$ curl https://mise.run | sh
```

### Go のインストール

プロジェクトのルートディレクトリで：

```bash
# mise.toml がすでに存在するので、以下を実行するだけ
$ mise install

# インストールされたことを確認
$ go version
# go version go1.23.11 darwin/arm64
```

### 🎪 コラム：Go のバージョン管理

Go は後方互換性を非常に重視しているため、Node.js ほど頻繁にバージョンを切り替える必要はありません。それでも：

- **Go 1.18**：ジェネリクス導入
- **Go 1.21**：ビルトイン関数の追加
- **Go 1.22**：ループ変数のスコープ変更

など、重要な変更があるため、バージョン管理ツールは有用です。

## 🛠️ VS Code の設定

### Go 拡張機能のインストール

1. VS Code を開く
2. 拡張機能マーケットプレイス（Cmd+Shift+X / Ctrl+Shift+X）を開く
3. "Go" で検索
4. Google が提供する公式の Go 拡張機能をインストール

### Go ツールのインストール

Go 拡張機能をインストール後：

1. コマンドパレット（Cmd+Shift+P / Ctrl+Shift+P）を開く
2. "Go: Install/Update Tools" を実行
3. すべてのツールを選択してインストール

インストールされる主要なツール：

- **gopls**：Language Server（自動補完、定義へのジャンプなど）
- **dlv**：デバッガー
- **staticcheck**：静的解析ツール
- **goimports**：import 文の自動整理

### おすすめの VS Code 設定

`.vscode/settings.json` を作成：

```json
{
  // 保存時に自動フォーマット
  "editor.formatOnSave": true,
  "[go]": {
    "editor.defaultFormatter": "golang.go"
  },
  
  // 保存時に import を整理
  "go.formatTool": "goimports",
  
  // リンターの設定
  "go.lintOnSave": "package",
  "go.lintTool": "staticcheck",
  
  // テストの設定
  "go.testEnvVars": {
    "GO_ENV": "test"
  },
  
  // 構造体のタグ補完
  "go.addTags": {
    "tags": "json",
    "options": "json=omitempty",
    "promptForTags": false,
    "transform": "snakecase"
  }
}
```

## 👋 Hello World プログラムの作成

### 1. プロジェクトの初期化

```bash
# 新しいディレクトリを作成
$ mkdir hello-go && cd hello-go

# Go モジュールの初期化（npm init に相当）
$ go mod init hello-go
```

### 2. main.go の作成

```go
package main

import "fmt"

func main() {
    fmt.Println("Hello, Go!")
    fmt.Println("TypeScript エンジニアから Go エンジニアへの第一歩！🎉")
}
```

### 3. プログラムの実行

```bash
# 実行（npm start に相当）
$ go run main.go
Hello, Go!
TypeScript エンジニアから Go エンジニアへの第一歩！🎉

# ビルド（npm run build に相当）
$ go build -o hello main.go

# ビルドされたバイナリを実行
$ ./hello
```

### TypeScript との比較

```typescript
// TypeScript (Node.js)
console.log("Hello, TypeScript!")

// 実行には Node.js が必要
// $ node index.js
```

```go
// Go
fmt.Println("Hello, Go!")

// 単独で実行可能なバイナリを生成
// $ ./hello
```

## 🚀 開発効率を上げる Tips

### 1. エディタの活用

- **定義へのジャンプ**：F12 または Cmd+クリック
- **すべての参照を検索**：Shift+F12
- **リネーム**：F2
- **クイックフィックス**：Cmd+. / Ctrl+.

### 2. よく使うコマンド

```bash
# フォーマット（prettier に相当）
$ go fmt ./...

# リント（eslint に相当）
$ go vet ./...

# テスト実行（jest に相当）
$ go test ./...

# 依存関係の整理（npm prune に相当）
$ go mod tidy

# ドキュメントをブラウザで見る
$ go doc -http=:6060
```

### 3. デバッグの設定

`.vscode/launch.json` を作成：

```json
{
  "version": "0.2.0",
  "configurations": [
    {
      "name": "Launch Package",
      "type": "go",
      "request": "launch",
      "mode": "auto",
      "program": "${fileDirname}",
      "env": {},
      "args": []
    }
  ]
}
```

これで F5 キーでデバッグ実行ができます！

## 📝 環境構築チェックリスト

- [ ] mise をインストールした
- [ ] `mise install` で Go 1.23.11 をインストールした
- [ ] VS Code に Go 拡張機能をインストールした
- [ ] Go ツールをすべてインストールした
- [ ] Hello World プログラムが実行できた
- [ ] `go fmt` でコードがフォーマットされた

## 🎪 コラム：Go の開発体験

TypeScript 開発に慣れていると、最初は以下の点で戸惑うかもしれません：

**ないもの**
- `package.json` → `go.mod`
- `node_modules` → モジュールは `$GOPATH/pkg/mod` に集約
- `.prettierrc` → `go fmt` で統一（設定不要！）
- `tsconfig.json` → コンパイラオプションは最小限

**あるもの**
- 高速なコンパイル
- 統一されたフォーマット
- 優れた標準ツール群
- シンプルな依存関係管理

## 🎯 次のステップ

環境構築が完了したら、次は Go の基本文法を学んでいきましょう！

第1章では、変数宣言、型、演算子など、Go プログラミングの基礎を TypeScript との比較を交えながら学習します。

---

**トラブルシューティング**

もし問題が発生したら：

1. `go version` で Go が正しくインストールされているか確認
2. VS Code を再起動
3. `Go: Install/Update Tools` を再実行
4. それでも解決しない場合は、[Go の公式ドキュメント](https://go.dev/doc/install) を参照

準備はできましたか？さあ、Go の世界へ飛び込みましょう！ 🚀