# プラグインを作成し公開する

HonKitプラグインは、NPMで公開されているノードパッケージで、定義された規約に従ったものです。

## 構造

#### パッケージ.json

パッケージ.json`は、**Node.jsモジュール**を記述するためのマニフェスト形式です。HonKitプラグインは、Nodeモジュールの上に構築されます。これは、依存関係、バージョン、所有権、およびHonKitでプラグインを実行するために必要なその他の情報を宣言します。このドキュメントでは、スキーマの詳細を説明します。

プラグインマニフェスト `package.json` には、必要な設定についての詳細を含めることもできます。設定スキーマは `package.json` の `honkit` フィールドで定義されます（このフィールドは [JSON-Schema](http://json-schema.org) ガイドラインに準拠しています）。

```js
{
    "name": "honkit-plugin-mytest",
    "バージョン": "0.0.1",
    "説明": "これは私の最初のHonKitプラグインです",
    "エンジン"。{
        "honkit": ">1.x.x"
    },
    "honkit "です。{
        "プロパティ": {
            "myConfigKey "です。{
                "タイプ": "文字列",
                "デフォルト": "デフォルト値です",
                "説明": "私の素晴らしいコンフィグを定義します！"
            }
        }
    }
}
```

package.json`については、[NPM documentation](https://docs.npmjs.com/files/package.json)で詳しく説明されています。

パッケージ名**は、以下のパターンで始まる必要があります。

- <スコープ>/honkit-plugin-` で始まるパッケージ名である必要があります。
- honkit-plugin-`（ホンキット-プラグイン-）。
- パッケージ名**は以下のパターンで始まる必要があります： `@<scope>/gitbook-plugin-`
- gitbook-plugin-` となります。

また、**パッケージエンジン** には `honkit` または `gitbook` が含まれている必要があります。

#### index.js

index.js`はプラグインランタイムのメインエントリポイントです。

```js
module.exports = {
    // フックのマップ
    フック。{},

    // 新しいブロックのマップ
    ブロック {},

    // 新しいフィルタのマップ
    フィルター {}
};
```

## プラグインを公開する

HonKitのプラグインは、[NPM](https://www.npmjs.com)で公開することができます。

新しいプラグインを公開するには、[npmjs.com](https://www.npmjs.com)にアカウントを作成し、コマンドラインから公開する必要があります。

```
$ npm publish
```

## プライベートプラグイン

プライベートプラグインは GitHub 上でホストすることができ、 `git` URL を使用してインクルードすることができます。

```
{
    "plugins": [
        "myplugin@git+https://github.com/MyCompany/myhonkitplugin.git#1.0.0"
    ]
}
```
