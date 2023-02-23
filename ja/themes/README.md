# テーマ設定

バージョン3.0.0以降、HonKitは簡単にテーマを設定することができるようになりました。書籍では、デフォルトで [theme-default](https://github.com/honkit/honkit/tree/master/packages/%40honkit/theme-default) のテーマが使用されています。

> **Caution**: 注意**: テーマをカスタマイズすると、一部のプラグインが正しく動作しなくなることがあります。

### テーマの構造

テーマとは、テンプレートとアセットを含むプラグインです。テーマは常にデフォルトテーマを拡張するため、個々のテンプレートの上書きは任意です。

| フォルダ名 | 説明 |
| -------- | ----------- |
| `_layouts` | すべてのテンプレートを含むメインフォルダです。
| `_layouts/website/page.html` | 通常ページのテンプレート
| `_layouts/ebook/page.html` | 電子書籍生成時の通常ページのテンプレート (PDF< ePub, Mobi) ｜ Developers.IO


### 書籍のテーマの拡張/カスタマイズ

著者は本のソースから直接テーマのテンプレートを拡張することができます（外部テーマを作成することなく）。テンプレートはまず本の `_layouts` フォルダで解決され、次にインストールされたプラグイン/テーマで解決されます。

### Forkingの代わりにExtend

テーマの変更を複数のブックで利用できるようにしたい場合、デフォルトのテーマをフォークする代わりに、[templating syntax](../templating/README.md) を使って拡張することが可能です。

```html
{テンプレート.selfを拡張 %}

{% ブロックボディ %}
    {スーパー()
    ... これは、"body "ブロックに追加されます。
{% endblock %} ...
```

より完全な例として、[API](https://github.com/GitbookIO/theme-api) テーマを見てみましょう。

### テーマを公開する

テーマはプラグイン ([関連ドキュメント](../plugins/README.md)) として、プレフィックスに `theme-` を付けて公開されます。例えば、テーマ `awesome` は `theme-awesome` プラグインから読み込まれ、NPM パッケージの `honkit-plugin-theme-awesome` から読み込まれます。
