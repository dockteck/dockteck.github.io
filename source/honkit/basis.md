# 基本的なこと

- HonKitの設定はbook.jsonで行います。
- [Font Awesome](https://fontawesome.com/v4/)はv4までです。
- Gitbookのプラグインも使えます。
- テーマやプラグインは割と簡単につくれます。
- ビルドするとmdファイルがhtmlになります。
- CSSやJavaScriptも使えます。
- 全ての答えは[公式サイト](https://honkit.netlify.app/)にある！(((はず

四の五の言わずさっそく作ってみましょう。  
デスクトップで右クリックからVSCodeを開いてください。  
VSCodeのターミナルを開いたら下記を順番に実行してください。

```bash
mkdir project && cd project && mkdir source
```

```bash
npm init --y
```

```bash
npm install honkit --save-dev
```

```bash
npx honkit init ./source
```

特に説明は不要かと思いますが、ポイントとしてはprojectフォルダに設定を置いたり成果物が入り、sourceフォルダに作りたいサイトの中身をぶち込んでいきます。  
initによって作成されたREADMEはトップページにあたりSUMMRYが画面左にある目次にあたります。

## book.json
```
type nul > book.json
```

book.jsonファイルを作成したら[別ページにサンプル](scode.md)を置いてあるのでbook.jsonにコピペしてください。重要なのは root、plugins、pluginsConfigの３つだけです。  
npmでインストールしたプラグインはpackage.jsonに登録され、その中からhonkitで使いたいプラグインをbook.jsonで指定および有効化します。そして指定したプラグイン自体の設定をpluginsConfigによって行います。

## package.json

これも[別ページにサンプル](scode.md#packagejson)を置いてあるのでpackage.jsonにコピペしてください。  
先ほどnpmでインストールしたプラグインはpackage.jsonに登録されると言いましたが、逆に予めpackage.jsonに登録しておいてまとめてインストールすることもできます。下記を実行してみてください。

```
npm install --save-dev
```

## SUMMARY.md

まだ空の状態だと思いますので、試したい場合は下記をSUMMARY.mdに予めコピペしてください。
```
* [Part I](part1/README.md)
    * [Writing is nice](part1/writing.md)
    * [HonKit is nice](part1/honkit.md)
* [Part II](part2/README.md)
    * [We love feedback](part2/feedback_please.md)
    * [Better tools for authors](part2/better_tools.md)
```

フォルダやファイルがまだない状態で先ほどの`npx honkit init ./source`を実行すると自動的に生成してくれます。

## ローカルでの確認とビルド

ローカルサーバーの起動
```
npx honkit serve
```
アクセスしたら見れる　http://localhost:4000

ビルド

```
npx honkit build
```

どちらも`_book`が生成されるようになっています。  
docsに出力したい場合は「なにをなにに」の順番なので、下記を実行すればProject内にdocsが生成されます。

```
npx honkit build . docs
```

ちなみに、VSCodeだと右上のボタンや Ctrl+K を押して V を押したりすると横にプレビューを出せます。
