# 電子ブックやPDFを生成する

HonKitはウェブサイトを生成することができますが、電子書籍（ePub, Mobi, PDF）としてコンテンツを出力することも可能です。

```
# PDFファイルを生成する
$ honkit pdf ./ ./mybook.pdf

# ePubファイルの生成
$ honkit epub ./ ./mybook.epub

# Mobiファイルの生成
$ honkit mobi ./ ./mybook.mobi
```

### ebook-convertのインストール

電子書籍(epub, mobi, pdf)を生成するためには、`ebook-convert`が必要です。

##### OS X

Calibre アプリケーション](https://calibre-ebook.com/download)をダウンロードします。Calibre.app` をアプリケーションフォルダに移動した後、ebook-convert ツールへのシンボリックリンクを作成します。

```
$ sudo ln -s /Applications/calibre.app/Contents/MacOS/ebook-convert /usr/local/bin
```

usr/bin` は、$PATH にある任意のディレクトリに置き換えることができます。

### 表紙

すべての電子書籍フォーマットで表紙が使用されます。

表紙を用意するには、本のルートディレクトリに **`cover.jpg`** ファイルを配置します。**cover_small.jpg`**を追加すると、カバーの縮小版を指定することができます。表紙は**JPEG**ファイルである必要があります。

良いカバーは、以下のガイドラインを尊重する必要があります。

* サイズは `cover.jpg` が1800x2360ピクセル、`cover_small.jpg` が200x262ピクセルです。
* ボーダーなし
* 本のタイトルがはっきりと見えること
* 重要なテキストは、小さいバージョンでも見えるようにしてください。
