# プラグインをテストする

### ローカルでプラグインをテストする

プラグインを公開する前に、自分の本でテストするには、[npm link](https://docs.npmjs.com/cli/link)を使用することができます。

プラグインのフォルダで、以下を実行します。

```
$ npm link
```

次に、あなたの本のフォルダで

```
$ npm link honkit-plugin-＜プラグイン名＞...
```

### Travisでのユニットテスト

[gitbook-tester](https://github.com/todvora/gitbook-tester)を使うと、プラグインの **Node.js/Mocha** ユニットテストが簡単に書けるようになります。Travis.org](https://travis.org) を使うと、コミットやタグごとにテストを実行することができます。

[honkit-tester](https://github.com/vowstar/honkit-tester) 時間の経過とともに、最新バージョンの nodejs では gitbook-tester が正常に動作しなくなる場合があります。これは gitbook-tester の移植版で、LTS 版の nodejs v14.x v16.x v18.x で動作し、gitbook の代わりに honkit エンジンを使ってテストを実行することができます。
