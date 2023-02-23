# 設定

HonKitでは、柔軟に設定を行ってブックをカスタマイズすることができます。これらのオプションは`book.json`ファイルで指定します。JSONの構文に不慣れな執筆者のために、[JSONlint](http://jsonlint.com)などのツールを使って構文のチェックを行うことができます。

### 全般的な設定

{{honkit.version}}

| 変数名 | 説明 |
| -------- | ----------- |
| `root` | ルートディレクトリのパスです。`book.json` 以外の、ブックのすべてのファイルを格納しているパスを設定します。|
| `structure` | Readme(リードミー)、Summary(サマリー)、Glossary(注釈)などの名前を指定します。[ブックの構成ファイル](#ブックの構成ファイル)を参照してください。|
| `title` | ブックのタイトルです。デフォルト値は `HonKit` です。  |
| `description` | ブックの説明文です。 default value is extracted from the README. |
| `author` | オーサー(執筆者・著者)の名前です。複数のオーサーを指定する場合は、アンパサンド(&)で区切ってください。 |
| `authorSort` | オーサーでソートするときに使用する文字列です。|
| `producer` | プロデューサー(製作者)の名前です。|
| `publisher` |パブリッシャー(出版社)の名前です。|
| `series` | このブックが属するシリーズの名前です。|
| `seriesIndex` | シリーズに属するブックのインデックスです。|
| `pubdate` | ブックの出版日です。YYYY-MM-DDTHH:MM:SSのようなフォーマットで表示されます。|
| `isbn` | ブックのISBNコードです。 |
| `language` | [ISOコード](https://en.wikipedia.org/wiki/List_of_ISO_639-1_codes)で表すブックの言語です。デフォルト値は `en` です。 |
| `direction` | テキストの方向です。rtl` または `ltr` で、デフォルト値は `language` の値に依存します。 |
| `gitbook` | ビルド時に指定するHonKitのバージョンです。[セマンティック バージョニング仕様書 (SemVer)](https://semver.org/lang/ja/) を採用しているので、例えば`">= 3.0.0"`といった指定も可能です。 |
| `honkit` | ビルド時に指定するHonKitのバージョンです。[セマンティック バージョニング仕様書 (SemVer)](https://semver.org/lang/ja/) を採用しているので、例えば`">= 3.0.0"`といった指定も可能です。|

### プラグイン

ロードするプラグインとその設定は `book.json` で指定します。詳しくは[プラグイン](plugins/README.md)を参照してください。

バージョン3.0.0以降、HonKitはテーマを使用することができます。詳しくは[テーマ](themes/README.md)を参照してください。

| 変数名 | 説明
| -------- | ----------- |
| `plugins` | ロードするプラグインのリストです。 |
| `pluginsConfig` | プラグインの設定値です。 |

### ブックの構成ファイル

ルートディレクトリのパスに加えて、Readme, Summary, Glossary, Languages のファイル名を指定することができます（デフォルトの `README.md` のような名前を使用することはできません）。
これらのファイルは、ブックのルートディレクトリ(または各言語のルートディレクトリ)にある必要があります。`dir/MY_README.md`のようなパスは受け付けません。

| 変数名 | 説明 |
| -------- | ----------- |
| `structure.readme` | Readme(リードミー)のファイル名 (デフォルトは `README.md`) |
| `structure.summary` | Summary(サマリー)のファイル名 (デフォルトは `SUMMARY.md`) |
| `structure.glossary` | Glossary(注釈)のファイル名 (デフォルトは `GLOSSARY.md`) |
| `structure.languages` | Languages(多言語)のファイル名 (デフォルトは `LANGS.md`)|

### PDFオプション

PDF出力は、`book.json`にある一連のオプションを使ってカスタマイズすることができます。

| 変数名 | 説明
| -------- | ----------- |
| `pdf.pageNumbers` | 各ページの一番下に配置するページ番号の有無です。 (デフォルトは `true`) |
| `pdf.fontSize` | ベースとなるフォントサイズです。  (デフォルトは `12`)|
| `pdf.fontFamily` | ベースとなるフォントファミリーです。 (デフォルトは `Arial`) |
| `pdf.paperSize` | 用紙サイズです。 `'a0', 'a1', 'a2', 'a3', 'a4', 'a5', 'a6', 'b0', 'b1', 'b2', 'b3', 'b4', 'b5', 'b6', 'legal', 'letter'`から選択します。 (デフォルトは `a4`) |
| `pdf.margin.top` | 上側の余白です。 (デフォルトは  `56`) |
| `pdf.margin.bottom` | 下側の余白です。(デフォルトは  `56`) |
| `pdf.margin.right` | 右側の余白です。 (デフォルトは  `62`) |
| `pdf.margin.left` | 左側の余白です。 (デフォルトは  `62`) |
| `pdf.embedFonts` | PDFへの埋め込みフォントの有無です。 (デフォルトは  `false`) |
