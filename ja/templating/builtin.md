# 組み込みのテンプレートヘルパー

HonKit は、テンプレートを書くのに役立つ一連の組み込みフィルタとブロックを提供します。

### フィルタ

`value|default(default, [boolean])`value が厳密に未定義の場合は default を返し、そうでない場合は value を返す。booleanがtrueの場合、JavaScriptのfalsyな値はすべてdefaultを返す（false, "", etc)

arr|sort(reverse、caseSens、attr)`。
arr を JavaScript の arr.sort 関数でソートします。reverseがtrueの場合、結果は逆順になります。デフォルトでは大文字と小文字を区別しませんが、caseSensをtrueに設定すると大文字と小文字を区別するようになります。attr が渡された場合、各項目の attr を比較します。

### ブロック

マークダウンの文字列`{% endmarkdown %}`を表示します。
インラインマークダウンをレンダリングします。

`{% asciidoc %}AsciiDoc string{% endasciidoc %}` インラインのAsciidocをレンダリングします。
asciidoc をインラインでレンダリング
