# AsciiDoc

バージョン `2.0.0` 以降、HonKit は入力フォーマットとして AsciiDoc を受け入れることができます。

このフォーマットについて詳しくは [AsciiDoc Syntax Quick Reference](http://asciidoctor.org/docs/asciidoc-syntax-quick-reference/) を参照してください。

マークダウンと同様、HonKitは構造を抽出するためにいくつかの特別なファイルを使用します。README.adoc`、`SUMMARY.adoc`、`LANGS.adoc`、`GLOSSARY.adoc`です。

### README.adoc

このファイルは、あなたの本のメインエントリである「はじめに」です。このファイルは ** 必須** です。

### SUMMARY.adoc

このファイルは章とサブチャプターのリストを定義します。Markdownのように、`SUMMARY.adoc`のフォーマットは単純にリンクのリストで、リンクの名前は章の名前として使われ、ターゲットはその章のファイルへのパスとなります。

サブチャプターは、親チャプターにネストしたリストを追加するだけで定義できます。

```asciidoc
= 概要

. link:chapter-1/README.adoc [第1章] .
... link:chapter-1/ARTICLE1.adoc [記事1].
... link:chapter-1/ARTICLE2.adoc[記事2] ...
... link:chapter-1/ARTICLE-1-2-1.adoc[Article 1.2.1] ...
. link:chapter-2/README.adoc [第2章] ...
link:章-3/README.adoc[3章] .
. link:章-4/README.adoc[章-4] .
.. 未完成の記事
. 未完成の章
```

### LANGS.adoc

多言語版](./languages.md)ブックでは、このファイルを使って、サポートされるさまざまな言語と翻訳を定義することができます。

このファイルは `SUMMARY.adoc` と同じシンタックスです。

```asciidoc
= 言語

. link:en/[英語] .
. link:fr/[フランス語] .
```

### GLOSSARY.adoc

このファイルは、用語を定義するために使用されます。[用語集のセクションを参照](./lexicon.md)。

``asciidoc
= 用語集

== マジック

観測者の理解を超えた、十分に高度な技術。
観測者の理解を超えた高度な技術であり、不思議な感覚を生み出す。

== PHP

Facebookなどの大規模サイトで使用されている、人気のWebプログラミング言語。
Facebookなど多くの大規模サイトで使用されている。1994年にRasmus Lerdorf氏が個人ホームページを作成するために開発した。
ラスマス・レンドルフが個人的なホームページを作成するために1994年に開発した。
現在では「PHP: 現在では「PHP: Hypertext Preprocessor」と呼ばれています）。```


