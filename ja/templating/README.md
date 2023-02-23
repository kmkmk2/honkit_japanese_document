# テンプレーティング

HonKitでは、ページやテーマのテンプレートを処理するために、[Nunjucks templating language](https://mozilla.github.io/nunjucks/)を使用しています。

Nunjucksの構文は、**Jinja2**や**Liquid**に非常によく似ています。この構文では、中括弧 `{ }` を使って、処理する必要のあるコンテンツをマークします。

### 変数

変数は、テンプレートのコンテキストから値を探します。単に変数を表示したい場合は、 `{{ variable }}` という構文を使用します。例えば :

例えば： ``twig
私の名前は {{ 名前 }} です、よろしくお願いします。
```

これは、コンテキストからユーザー名を検索して表示します。変数名には、JavaScriptと同じように、プロパティを検索するドットを入れることができます。また、角括弧を使った構文も使用できます。

``twig
{{ foo.bar }}
{{ foo["bar"] }} となります。
```

値が未定義の場合は、何も表示されません。以下のものはすべて、fooが未定義の場合、何も出力しません。`{{ foo }}`, `{{ foo.bar }}`, `{{ foo.bar.baz }}`.

HonKitでは、コンテキストから[定義済み変数](variables.md)のセットを提供しています。

### フィルター

フィルタは本質的に、変数に適用できる関数です。フィルターはパイプ演算子 (`|`) で呼び出され、引数を取ることができます。

```twig
{{ foo | タイトル }}
{{ foo | join(",") }} です。
{{ foo | replace("foo", "bar") | 大文字 }} となります。
```

3つ目の例は、フィルタを連結する方法を示しています。これは、まず "foo" を "bar" に置き換え、次に大文字にして "Bar" を表示します。

### タグ

##### if

if` は条件をテストし、選択的にコンテンツを表示することができます。JavaScript の `if` と全く同じ動作をします。

```twig
{% if 変数 %}
  それは真です
{% endif %} です。
```

もし変数が定義されていて、評価値がtrueなら、"It is true "と表示されます。そうでなければ、何も表示されません。

elif` と `else` を使って、別の条件を指定することができます。

```twig
{% if hungry %} 私はお腹が空いています。
  私はお腹が空いています。
{elif tired %} 私は疲れています。
  私は疲れている
{他の %}
  私は元気です!
私は元気です！{% endif %}
```

##### for

for` は、配列や辞書を繰り返し処理します。

```twig
# HonKitについての章

{% for article in glossary.terms['gitbook'].articles %} * [{{ article.title }}({{ article.path}})
* [{{ article.title }}]({{ article.path }})
{% endfor %}
```

##### セット

set` では、変数を作成・変更することができます。

```twig
{% set softwareVersion = "1.0.0" %} 現在のバージョンは {{ softwareVersion }} です。

現在のバージョンは {{ softwareVersion }} です。
[ダウンロードする](website.com/download/{{softwareVersion }})
```

##### インクルードとブロック

インクルードと継承については、[Content References](conrefs.md) のセクションで詳しく説明しています。

### エスケープ

もしHonKitに特殊なテンプレートタグを無視させたい場合は、rawを使用すると、その中のものはプレーンテキストとして出力されます。

``` twig
{% raw %}
  これは{{処理されません}}となります。
{% endraw %} です。
```
