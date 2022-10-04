# カスタマイズ

基本的に既存のプラグインでほとんどのことがカスタマイズできると思います。ただ、バージョンの依存関係の問題なのかうまく動かないものも散見されました。

## プラグイン
[npm - https://www.npmjs.com/](https://www.npmjs.com/)  
基本的には上記のnpmのサイトで`gitbook-plugin`または`honkit-plugin`で検索してVScode(ターミナル)からインストールすることになります。

プラグイン名をbook.jsonのpluginsに登録することで有効になります。  
さらにそのプラグインに設定ができる場合はpluginsConfigに記載します。そのプラグインのnpmのページか製作者のGithubのページに記載されていることが多いです。  
そのプラグインを自分で編集してしまうのも一つの手です。

### 実際にプラグインをインストールしてみる

試しに[bottom-navigation](https://www.npmjs.com/package/gitbook-plugin-bottom-navigation)を入れてみましょう。

まずはVSCodeのターミナルからnpmでインストールします。  

```bash
npm i gitbook-plugin-bottom-navigation --save-dev
```
package.jsonをみると`gitbook-plugin-bottom-navigation`が増えているのがわかるはずです。

次にbook.jsonを開いて`plugins`に下記を追加します。

```
"bottom-navigation",
```

さらに`pluginsConfig`に下記を追加します。  
`null`の所に Hex でお好みのカラーコード(ネームもおｋ)を入れてください。何も入れなければデフォルトカラーになります。  
[おぬぬめツール](https://www.hexcolortool.com/) - ここは他にも便利ツールがあります。

```
"bottom-navigation": {
    "iconColor": "null",
    "titleColor": "null",
    "borderColor": "#3884FE"
}
```
結果的には下記みたいになります。

```
{
    "root": "./source",
    "plugins": [
        "theme-default",
～　中略　～
        "bottom-navigation",
        "insert-logo-link-style",
        "toggle-chapters"
    ],

    "pluginsConfig": {
        "bottom-navigation": {
            "iconColor": "red",
            "titleColor": "777777",
            "borderColor": "#3884FE"
        }
    }
}
```

### ローカルで確認してみる

ここで一度どうなっているか見てみましょう。  
ターミナルで下記を実行してみてください。  
```
npx honkit serve
```
ブラウザから http://localhost:4000 にアクセスして、一番下を見るとプラグインの機能が追加されているはずです。 `Ctrl+C` で停止します。  
ついでにブラウザの右下を見ると `[報告するる]` というボタンがある事を確認しておいてください。

## スタイルシート

ヘッダーなどのデザインを変更したい時にはその方法はいくつかあります。上述のプラグインを利用したり、あるいは自ら作ってしまうのもひとつです。

[HonKitの公式サイト](https://honkit.netlify.app/themes/)によると`「ソースから直接テーマのテンプレートを拡張できる」`とあります。しかし「さくさくっと」いきたいのでココではスタイルシートの拡張についてのみ軽く紹介するだけにします。

{% hint style='info' %}
レイアウトに興味がある方は下記の方々の`_layouts内`を参考にしてみてください。
- [Jsprimer](https://github.com/asciidwango/js-primer/tree/master/source/_layouts/website)
- [akahigeg](https://github.com/akahigeg/honkit-plugin-theme-webheadfoot)
- [Stuyk](https://github.com/stuyk/honkit-plugin-theme-darkening)
{% endhint %}

まずbook.jsonに拡張スタイルシートの指定をします。  
※サンプルをコピペした方はすでに入っています

```
"styles": {
    "website": "styles/website.css",
}
```
次にディレクトリとファイルを作成します。
```
mkdir ./source/styles && type nul > ./source/styles/website.css
```

このwebsite.cssに[別ページのサンプル](scode.md#websitecss)をコピペしてください。  
再度`npx honkit serve`を実行してみてください。

まずタイトルに下線が増えました。  
さらに先ほど確認した `[報告するる]` のデザインが[Jsprimer](https://jsprimer.net/)と同じになりました。  
このようにデザインの変更が可能です。興味がある方は、`project/node_modules/@honkit/honkit-plugin-theme-default/_assets/website/style.css`を見ていじってみてください。

ただスマホで見ると[Jsprimer](https://jsprimer.net/)では非表示になっているのですが、そこまでやるのはめんどいのでぼくは根本的に消しました。下記を実行すれば消せます。
```
npm r gitbook-plugin-github-issue-feedback
```

## プラグインを使わずにfaviconを変更する
結論だけ言うと`project/node_modules/@honkit/honkit-plugin-theme-default/_assets/website/images`の画像を同じ名前にして入れ替えるだけです。

ちなみに、デフォルトの`apple-touch-icon-precomposed-152.png` は 180x180-96dpi  
`favicon.ico` は 48x48-96dpi になっていました。

## そのほかのデザイン変更

正攻法なのかどうかよくわかりませんが、このサイトで実際にやった変更を記載しておきます。

### テーマのデフォルトカラーを変更
Nightカラーが気に入ったのでコレがデフォルトになるように変更しました。  
`project/node_modules/gitbook-plugin-fontsettings/assets/fontsettings.js`の168行目を次のようになるように付け足して変更すればできます。
```
theme:  configTheme || 2
```

### toc-button-backの色を変更
Nightモードの時の色が変だったので変更しました。  
`project/node_modules/@dogatana/honkit-plugin-page-toc-button/assets/plugin.css`
の84行目のrgbの数値を`38, 40, 56, 0.9`に変更しました。

### リンク付きのロゴ画像を追加する

これは[insert-logo-link-style](https://github.com/zeroone/gitbook-plugin-insert-logo-link-style#readme)プラグインを使っています。  
ファルダを作成して、そこにロゴの画像を置きます。
```
mkdir ./source/assets
```
linkにはLINEのオープンチャットやDiscordなど好きなURLを入力してください。不要なら空にすればいいです。
