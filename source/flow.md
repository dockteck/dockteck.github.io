# 全体の流れ

まず先に断っておくと基本的に、基本的なことしか書かないつもりなのであしからず。  
それと今回はWindowsを使いますが、ぼくは普段MacOSを使っていてWindowsは初心者なので間違いがあれば指摘してくださるとありがたいです。

---

## 環境構築

1, HonKitはNodeが必要なので先にバージョン管理ツールを導入します。  
WindowsはVolta、UNIX系はasdfかanyenvを入れます。

2, エディターはVSCodeを使います。

3, Gitがまだなら下記を参考にインストールしてください。  
※タイトルは主観で勝手につけてます

- [windowsにGitをインスコ](https://prog-8.com/docs/git-env-win)
- [初心者必見！VSCodeでGit・GitHubを使う方法をイチからやさしく解説](https://miya-system-works.com/blog/detail/vscode-github/)
- [図解でマスター！ゼロから始めるVScode＋Githubの使い方](https://pengi-n.co.jp/blog/vscode-github/)

## HonKitの導入と基本

1. インストールからプラグインの導入
2. book.jsonとpackage.jsonについて
3. ビルドやローカルでの確認について
4. デザインについて少々

## Github Pagesに公開

npmプラグインのgh-pagesを使います。

---
今のところここまで

---

## Github Actionsについて

## 記事の投稿について

---

## コピペムーブ
そんな欲張りの貴方でもリポジトリは先に作っておいてくださいね♪

下ごしらえ
```
//１行づつどぞ

mkdir project && cd project && mkdir source
npm init --y
npm install honkit --save-dev
npx honkit init ./source
type nul > book.json
```
book.jsonにコピペ  
※edit link のURLは自分のに変えてください。
```
{
    "root": "./source",
    "title": "",
    "description": "",
    "author": "Name",
    "language": "ja",
    "plugins": [
        "theme-default",
        "@dogatana/search-plus", "-lunr", "-search",
        "@dogatana/page-toc-button",
        "@dogatana/back-to-top-button",
        "anchors",
        "bottom-navigation",
        "copy-code-button",
        "edit-link",
        "hide-published-with",
        "hints",
        "insert-logo-link-style",
        "toggle-chapters"
    ],

    "pluginsConfig": {
        "toggle-chapters":{},
        "page-toc-button": {
            "maxTocDepth": 2,
            "minTocSize": 2
        },
        "insert-logo-link-style": {
            "src": "/assets/logo.png",
            "style": "background: none;",
            "link": "/",
            "target": "_blank"
        },
        "bottom-navigation": {
            "iconColor": "888888",
            "titleColor": "888888",
            "borderColor": "#3884FE"
          },
        "edit-link": {
            "base": "https://github.com/user/user.github.io/edit/master/source/",
            "label": "このページを編集してあげる"
        },
        "hints": {
            "info": "fa fa-bullhorn",
            "tip": "fa fa-coffee",
            "danger": "fa fa-check",
            "working": "fa fa-question-circle"
        }
    },

    "styles": {
        "website": "styles/website.css",
        "pdf": "styles/pdf.css"
    }

}
```
package.jsonにコピペ  
※homepage のURLは自分のに変えてください。
```
{
  "homepage": "https://user.github.io/",
  "scripts": {
    "init": "npx honkit init ./source",
    "build": "npx honkit build . docs",
    "serve": "npx honkit serve",
    "deploy": "npx honkit build . docs && gh-pages -d docs"
  },
  "devDependencies": {
    "@dogatana/honkit-plugin-back-to-top-button": "^1.0.0",
    "@dogatana/honkit-plugin-page-toc-button": "^1.0.0",
    "@dogatana/honkit-plugin-search-plus": "^1.0.1",
    "gh-pages": "^4.0.0",
    "gitbook-plugin-anchors": "^0.7.1",
    "gitbook-plugin-bottom-navigation": "^0.2.2",
    "gitbook-plugin-copy-code-button": "^0.0.2",
    "gitbook-plugin-edit-link": "^2.0.2",
    "gitbook-plugin-hide-published-with": "^0.0.1",
    "gitbook-plugin-hints": "^1.0.2",
    "gitbook-plugin-insert-logo-link-style": "^1.0.3",
    "honkit": "^4.0.0",
    "honkit-plugin-toggle-chapters": "^0.0.1"
  }
}
```
SUMMARY.mdにフォルダやファイルなどを記述したら

```
npx honkit init ./source
```
必要なフォルダとファイル作成
```
mkdir ./source/assets && type nul > ./source/404.html

mkdir ./source/styles && type nul > ./source/styles/website.css
```
テーマの色を入れ替え
```
project/node_modules/gitbook-plugin-fontsettings/assets/fontsettings.js

//上記の168行目を下記のように変更

theme:  configTheme || 2
```
ファビコンの変更 - 
```
project/node_modules/@honkit/honkit-plugin-theme-default/_assets/website/images

//上記内の画像を入れ替えるだけ

apple-touch-icon-precomposed-152.png = 180x180-96dpi  
favicon.ico = 48x48-96dpi
```
toc-button-backの色を変更
```
project/node_modules/@dogatana/honkit-plugin-page-toc-button/assets/plugin.css

//84行目のrgbを

38, 40, 56, 0.9
```
docsにビルド
```
npx honkit build . docs
```
ローカルで確認 - http://localhost:4000 
```
npx honkit serve
```
gitignore追加
```
type nul > .gitignore

echo node_modules/ _book >> .gitignore
```
push
※ URLは自分のに変更
```
git init
git add --all
git commit -m "first commit"
git remote add origin https://github.com/(user name)/(repository name).git
git branch -M master
git push -u origin master
```
デプロイ
```
git remote add origin https://github.com/(user name)/(repository name).git

npm run deploy
```

[最後にGithubで設定](github/pages.md#最後に-github-で設定)したら完了！