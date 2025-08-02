# TypeScriptエンジニア向けの比較ガイド

TypeScript から Go への旅は、まるで自動変速の車からマニュアル車に乗り換えるようなもの。

最初は戸惑いますが、慣れると「こっちの方がシンプルで気持ちいい！」と感じるはずです。

## 🔄 言語の基本的な違い

### コンパイル方式の根本的な違い

| 特徴 | TypeScript | Go |
|------|------------|-----|
| コンパイル先 | JavaScript（トランスパイル） | ネイティブバイナリ |
| 実行環境 | Node.js/ブラウザが必要 | 単独で実行可能 |
| 配布形式 | ソースコード + node_modules | 単一の実行ファイル |
| クロスコンパイル | 不要（JS はどこでも動く） | 簡単（GOOS/GOARCH 指定） |

```bash
# TypeScript アプリの配布
$ npm install
$ npm run build
$ node dist/index.js

# Go アプリの配布
$ ./myapp  # これだけ！
```

## 🏛️ 型システムの哲学

### TypeScript：「すべてを型で表現」

TypeScript は型の表現力が非常に豊かです。

```typescript
// 複雑な型も自由自在
type DeepPartial<T> = {
  [P in keyof T]?: T[P] extends object ? DeepPartial<T[P]> : T[P]
}

// テンプレートリテラル型
type HTTPMethod = `${'GET' | 'POST'} /api/${string}`
```

### Go：「シンプルに、でも十分に」

Go の型システムは意図的にシンプルです。

```go
// 基本的な型定義のみ
type User struct {
    ID   int
    Name string
}

// 複雑な型操作はない（そして必要ない）
```

### 構造的型付け vs 名前的型付け

実は、両言語とも**構造的型付け**を採用しています！

```typescript
// TypeScript
interface Writable {
  write(data: string): void
}

class File {
  write(data: string): void {
    console.log(data)
  }
}

// File は Writable を満たす（implements 不要）
```

```go
// Go
type Writer interface {
    Write([]byte) (int, error)
}

type File struct{}

func (f File) Write(data []byte) (int, error) {
    return len(data), nil
}

// File は Writer を満たす（宣言不要）
```

## ⚡ 非同期処理の違い

### TypeScript：Promise と async/await

```typescript
// 非同期処理は Promise ベース
async function fetchUsers(): Promise<User[]> {
  const response = await fetch('/api/users')
  return response.json()
}

// 並行処理
const results = await Promise.all([
  fetchUsers(),
  fetchPosts(),
  fetchComments()
])
```

### Go：ゴルーチンとチャネル

```go
// 非同期の概念がない（すべて同期的）
func fetchUsers() ([]User, error) {
    resp, err := http.Get("/api/users")
    if err != nil {
        return nil, err
    }
    // ...
}

// 並行処理はゴルーチンで
go fetchUsers()  // 別のゴルーチンで実行
go fetchPosts()
go fetchComments()
```

### 重要な違い：エラーハンドリング

| TypeScript | Go |
|------------|-----|
| try-catch で例外をキャッチ | エラーは戻り値で返す |
| エラーを無視しがち | エラーを無視できない |
| スタックトレースあり | エラーメッセージのみ |

```typescript
// TypeScript
try {
  const users = await fetchUsers()
  console.log(users)
} catch (error) {
  console.error('Error:', error)
}
```

```go
// Go
users, err := fetchUsers()
if err != nil {
    log.Printf("Error: %v", err)
    return
}
fmt.Println(users)
```

## 📦 パッケージ管理

### npm vs go mod

| 機能 | npm | go mod |
|------|-----|--------|
| 設定ファイル | package.json | go.mod |
| ロックファイル | package-lock.json | go.sum |
| インストール先 | node_modules | $GOPATH/pkg/mod（共有） |
| バージョン指定 | semver（^, ~） | semver（厳密） |
| スクリプト実行 | npm run xxx | なし（Makefile 使用） |

```bash
# TypeScript/npm
$ npm install express
$ npm install -D @types/express

# Go
$ go get github.com/gin-gonic/gin
# 型定義は不要（Go は静的型付け言語）
```

## 🛠️ 開発ツールの違い

### ビルドツール

| TypeScript | Go |
|------------|-----|
| webpack/vite/esbuild | go build（標準） |
| 設定ファイル必須 | 設定不要 |
| プラグインシステム | なし |
| ソースマップ | 不要（ネイティブデバッグ） |

### フォーマッター

```bash
# TypeScript
$ npm install -D prettier
$ npx prettier --write .

# Go（標準装備！）
$ go fmt ./...
```

### リンター

```bash
# TypeScript
$ npm install -D eslint
$ npx eslint .

# Go
$ go vet ./...
$ golangci-lint run  # サードパーティ
```

## 🎯 使い分けのポイント

### TypeScript が向いている場面

1. **フロントエンド開発**
   - ブラウザで動く必要がある
   - React/Vue/Angular との相性

2. **Node.js エコシステム**
   - npm パッケージの豊富さ
   - JavaScript 資産の活用

3. **柔軟な型システムが必要**
   - 複雑な型操作
   - 段階的な型付け

### Go が向いている場面

1. **高パフォーマンスが必要**
   - CPU バウンドなタスク
   - 低レイテンシ要求

2. **デプロイの簡単さ**
   - 単一バイナリ配布
   - Docker イメージの軽量化

3. **並行処理が多い**
   - 大量のコネクション処理
   - マイクロサービス間通信

## 💡 移行時の注意点

### 1. エラーハンドリングの文化の違い

```go
// Go では必ずエラーチェック
file, err := os.Open("file.txt")
if err != nil {
    return err  // early return が基本
}
defer file.Close()  // クリーンアップも忘れずに
```

### 2. nil の扱い

```go
// Go の nil は TypeScript の null/undefined とは違う
var s *string  // nil ポインタ
var m map[string]int  // nil マップ

// nil マップは読み取り可能！
value := m["key"]  // value は 0（ゼロ値）
```

### 3. ゼロ値の活用

```go
// Go では未初期化の変数もゼロ値を持つ
var i int        // 0
var s string     // ""
var b bool       // false
var p *int       // nil

// TypeScript では undefined
```

## 🎪 コラム：両言語の設計思想の違い

**TypeScript**：「JavaScript に型を」
- 既存の JS コードとの互換性重視
- 豊富な型機能で開発体験を向上
- 「何でもできる」柔軟性

**Go**：「シンプル・イズ・ベスト」
- 言語機能は最小限
- 誰が書いても同じようなコード
- 「一つの正しい方法」

## 📝 まとめ

TypeScript から Go への移行で戸惑うポイント：

1. **例外がない** → エラーは戻り値で
2. **Promise がない** → ゴルーチンで並行処理
3. **型の表現力が限定的** → シンプルに設計
4. **npm scripts がない** → Makefile や go generate
5. **undefined がない** → ゼロ値を活用

でも慣れると：

- エラー処理が明示的で安全
- 並行処理が圧倒的に簡単
- ビルドが爆速
- デプロイが超シンプル
- コードが読みやすい

次章では、実際に Go の開発環境をセットアップして、最初のプログラムを書いてみましょう！

---

**参考資料**
- [Go for JavaScript Developers](http://www.pazams.com/Go-for-Javascript-Developers/)
- [TypeScript vs Go: Choosing Your Backend Language](https://blog.logrocket.com/typescript-vs-go-choosing-right-backend-technology/)
- [From TypeScript to Go](https://github.com/golang/go/wiki/FromTypeScriptToGo)