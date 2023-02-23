# 変数

本のパースやテーマ生成の際に利用できるデータの参考は以下の通りです。

### グローバル変数

| 変数名 | 説明
| -------- | ----------- |
| `book` | 本全体の情報 + `book.json` からの構成設定。詳細は以下を参照。|
| `honkit` | 本キットに固有の情報 | `gitbook` | 本キットに固有の情報
| `gitbook` | HonKit固有の情報。honkit`のエイリアスです。
| `page` | 現在のページに関する情報。
| `file` | 現在のページ固有の情報に関連付けられたファイル。
| `readme` | Readmeに関する情報｜...
| `glossary` | グロサリに関する情報｜index.index.index.index.com
| `summary` | 目次に関する情報｜...
| `languages` | マルチリンガル書籍のための言語リスト |...
| `output` | 出力ジェネレータについての情報｜...
| `config` | `book.json` のダンプ。

### 本の変数

| 変数名 | 説明
| -------- | ----------- |
| `book.[CONFIGURATION_DATA]` | `book.json` によって設定されたすべての `variables` は book 変数を通して利用することができます。|
| `book.language` | 多言語版書籍の現在の使用言語｜BOOK

### HonKitの変数

| 変数 | 説明
| -------- | ----------- |
| `honkit.time` | 現在の時刻（`honkit`コマンドを実行した時） . |
| `gitbook.time` | 現在の時刻（`honkit`コマンドを実行した時） . |
| `honkit.version` | ブックの生成に使用されたHonKitのバージョンです。
| `gitbook.version` | ブックを生成するために使用されたHonKitのバージョン | .

### ファイル変数

| 変数名 | 説明
| -------- | ----------- |
| `file.path` | 生のページへのパス。
| `file.mtime` | 修正時刻。ファイルが最後に変更された時間 |
| `file.type` | このファイルをコンパイルするために使用したパーサーの名前 (ex: `markdown`, `asciidoc`, etc.) | | `file.type` の値を指定します。

#### ページ変数

| 変数名｜説明
| -------- | ----------- |
| `page.title` | ページタイトル
| `page.previous` | 目次の前のページ (`null` を指定することもできます)|。
| `page.next` | 目次の次のページ (`null`も可)
| `page.dir` | 設定に基づいたテキストの方向、またはコンテンツから検出された方向 (`rtl` または `ltr`) | | 。

#### 目次の変数

| 変数名 | 説明
| -------- | ----------- |
| `summary.parts` | 目次に含まれるセクションのリスト｜。

目次全体(`SUMMARY.md`)にアクセスすることができる。

`summary.parts[0].articles[0].title` は、最初の記事のタイトルを返します。

#### 多言語の本 Variable

| 変数名
| -------- | ----------- |
| `languages.list` | このブックの言語のリスト｜。

言語は `{ id: 'en', title: 'English' }` で定義されます。

### 出力変数

| 変数名 | 説明
| -------- | ----------- |
| `output.name` | 出力ジェネレータの名前、利用可能な値は `website`, `json`, `ebook` | です。
| `output.format` | `output.name == "ebook"` の場合、 `format` は生成される電子書籍の形式を定義します、可能な値は `pdf`、`epub` または `mobi` です。

### Readme 変数

| 変数名 | 説明
| -------- | ----------- |
| `readme.path`