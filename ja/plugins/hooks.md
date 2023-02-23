# フック

フックとは、カスタムコールバックにより、プロセスの動作を補強・変更する方法である。

### フック一覧

### グローバルパイプラインとの相対関係

| 名前 | 説明 | 引数
| ---- | ----------- | --------- |
| `init` | 本をパースした後、出力とページを生成する前に呼び出されます。| なし
| `finish:before` | ページを生成した後に、アセット、カバー、...をコピーする前に呼び出されます。| なし
| `finish` | 他のすべての後に呼び出されます。| なし

### ページパイプラインへの相対パス

> ページ解析を拡張するために[templating](./templating.md)を使用することが推奨されます。

| 名前 | 説明 | 引数
| ---- | ----------- | --------- |
| `page:before` | ページ上でテンプレートエンジンを実行する前に呼び出されます。
| `page` | ページを出力してインデックスを作成する前に呼び出されます。| ページオブジェクト

:memo: インクリメンタルモード(`honkit serve`)のとき、HonKitはこれらのページのフックをスキップすることがあります。

##### ページオブジェクト

```js
{
    // パーサ名
    "type": "markdown "と命名。

    // ブックルートからの相対的なファイルパス
    "パス": "page.md",

    // 絶対的なファイルパス
    "rawpath": "/usr/...",

    // SUMMARY内のページのタイトル
    "title": "",

    // ページの内容
    // "page:before "の中にあるMarkdown/Asciidoc
    // "page "内のHTML
    "content": "<h1>こんにちは</h1>"

    // ページのレベル
    "レベル": "1.5.3.1"

    // ページの深さ
    "depth": "3"

    // その他の属性は.mdの中で、コンテンツの先頭にある2つの「---」の間に表示される。
    // 例えばマークダウンの前では
    // ---
    // 説明。これは説明文です
    // ---
    "説明": "これは説明文です"

    // 前の記事
    "前": 記事オブジェクト

    // Next article
    "next": Article Object
}
```

##### Example to add a title

In the `page:before` hook, `page.content` is the markdown/asciidoc content.

```js
{
    "page:before": function(page) {
        page.content = "# Title\n" +page.content;
        return page;
    }
}
```

##### Example to replace some html

In the `page` hook, `page.content` is the HTML generated from the markdown/asciidoc conversion.

```js
{
    "page": function(page) {
        page.content = page.content.replace("<b>", "<strong>")
            .replace("</b>", "</strong>");
        return page;
    }
}
```


### Asynchronous Operations

Hooks callbacks can be asynchronous and return promises.

Example:

```js
{
    "init": function() {
        return writeSomeFile()
        .then(function() {
            return writeAnotherFile()。
        });
    }
}
```
