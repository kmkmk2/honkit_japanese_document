# コンテキストとAPI

HonKitsはプラグインにさまざまなAPIとコンテキストを提供します。これらのAPIは使用するHonKitのバージョンによって異なる可能性があるので、プラグインはそれに応じて `package.json` の `engines.gitbook` フィールドを指定しなければなりません。

#### Book インスタンス

Book` クラスはHonKitの中心的な存在で、すべてのアクセス・リード・メソッドを集約しています。このクラスは [book.js] (https://github.com/honkit/honkit/blob/master/lib/book.js) で定義されています。

```js
// book.jsonから設定を読み込む
var value = book.config.get('title', 'Default Value');

// ファイル名を絶対パスに解決する
var filepath = book.resolve('README.md')。

// インラインのマークアップ文字列をレンダリングする
book.renderInline('markdown', 'This is **Markdown**')
    .then(function(str) { ... })

// マークアップ文字列をレンダリングする (ブロックモード)
book.renderBlock('markdown', '*これは**Markdown**です')
    .then(function(str) { ... })
```

#### 出力インスタンス

Output` クラスは、出力/書き込み処理を表します。

```js
// 出力のルートフォルダを返す
var root = output.root();

// 出力先フォルダのファイルを解決する
var filepath = output.resolve('myimage.png');

// ファイル名をURLに変換する（htmlファイルへのパスを返す）。
var fileurl = output.toURL('mychapter/README.md');

// 出力フォルダにファイルを書き込む
output.writeFile('hello.txt', 'Hello World')
    .then(function() { .... });

// ファイルを出力フォルダにコピーする
output.copyFile('./myfile.jpg', 'cover.jpg')
    .then(function() { ... });

// ファイルが存在するか確認する
出力.hasFile('hello.txt')
    .then(function(exists)){・・・・・・。});
```

#### ページインスタンス

ページインスタンスは、現在パースされているページを表します。

```js
// ページのタイトル (SUMMARYより)
page.title

// ページの内容 (ステージに応じたMarkdown/Asciidoc/HTML)
page.content

// 本編の相対パス
page.path

// ファイルへの絶対パス
page.rawPath

// このファイルに使用されるパーサの種類
page.type ('markdown' または 'asciidoc')
```

#### ブロックとフィルタのコンテキスト

ブロックとフィルタは同じコンテキストにアクセスすることができます。このコンテキストは、テンプレートエンジンの実行にバインドされています。

```js
{
    // 現在のテンプレート構文
    "ctx": {
        // 例えば、{% set message = "hello" %}の後に
        "メッセージ": "こんにちは"
    },

    // 本のインスタンス
    "book" <Book>,

    // 出力インスタンス
    "出力": <出力
}
```

例えば、フィルタやブロック関数は、次のようにして現在のブックにアクセスすることができます。this.book`.

#### フックのコンテキスト

フックは `this.book` を使って `<Book>` インスタンスにのみアクセスすることができます。
