# HonKitのセットアップとインストール

HonKitをインストールして、すぐ使えるようにしましょう。

### ローカルインストール

##### システム要件

HonKitのインストールは簡単で単純です。以下のたった2つのシステム要件を満たすだけです。

* NodeJS (v10.0.0以降を推奨)
* Windows、Linux、Unix、またはMac OS X

##### NPMでインストールする

HonKitのインストールは、**NPM**または**Yarn**経由が最良の方法です。ターミナルプロンプトで、以下のコマンドを実行するだけでHonKitがインストールされます。

```
$ npm install honkit --save-dev
# または
$ yarn add honkit --dev
```

⚠️警告

- `honkit`をグローバルインストール(`--global`)している場合は、各プラグインもグローバルインストール(`--global`)する必要があります。
- `honkit`をローカルインストールした場合は、各プラグインもローカルインストールする必要があります。

`honkit`はローカルインストールをお勧めします。

##### ブックの作成

HonKitでは、ブックの作成時に次のコマンドでセットアップします。

```
$ npx honkit init
```

ブックを新しいディレクトリ内で作成したい場合は、`npx honkit init ./directory` を実行します。

ブックのプレビューサーバー起動時は次のコマンドを使います。

```
$ npx honkit serve
```

また、静的なウェブサイトをビルドするには、次のようにします。

```
$ npx honkit build
```

また、`package.json`に[npm-run-scripts](https://docs.npmjs.com/cli/run-script) として`build`と`serve`コマンドを設定することができます。

```diff
  "scripts": {
    "build": "honkit build",
    "serve": "honkit serve"
  },
```

この設定後、`npm run`コマンドを使用することができます。

```
# ビルド 
npm run build
# プレビューサーバーの起動
npm run serve
```

##### デバッグ

`--log=debug`オプションを使用すると、詳細なエラーメッセージ(スタックトレース付き)を確認できます。コマンドは以下の通りです。

```
$ honkit build ./ --log=debug
```

