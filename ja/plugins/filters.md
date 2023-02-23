# フィルタの拡張

フィルタは基本的に変数に適用することができる関数です。パイプ演算子 (`|`) を使って呼び出され、引数を取ることができます。

```
{{ foo | タイトル }}
{{ foo | join(",") }} は、以下のようになります。
{{ foo | replace("foo", "bar") | capitalize }} {{ foo | title }} {{ foo | replace("foo", "bar") | capitalize }}
```

### 新しいフィルタを定義する

プラグインは、カスタム関数を `filters` スコープのエントリポイントに定義することで、フィルタを拡張することができます。

フィルター関数は、フィルターするコンテンツを最初の引数として受け取り、新しいコンテンツを返します。
this` と HonKit API の詳細については、 [Context and APIs] (./api.md) を参照してください。

```js
module.exports = {
    フィルター {
        hello: function(name) {
            return 'こんにちは '+name;
        }
    }
};
```

すると、`hello`というフィルタが本の中で使えるようになります。

```
{{ "Aaron"|hello }}, How are you?
```

### ブロック引数の処理

引数はフィルターに渡すことができます。

```
こんにちは {{ "Samy"|fullName("Pesse", man=true}}} 。}}
```

引数は関数に渡すことができます。名前付き引数は、最後の引数（オブジェクト）として渡されます。

```js
module.exports = {
    フィルター {
        fullName: function(firstName, lastName, kwargs) {
            var name = firstName + ' ' + lastName;

            if (kwargs.man) name = "Mr" + name;
            else name = "Mrs" + name;

            名前を返します。
        }
    }
};
```
