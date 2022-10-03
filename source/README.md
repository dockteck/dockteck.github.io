# はじめに

## HonKitとは

[オフィシャル](https://honkit.netlify.app/)にはこう記載されている。
>honkitは、GitHub/GitとMarkdown(または Ascii Doc)を使用して、美しい本を作成するためのコマンドラインツール(およびNode.jsライブラリ)です。  
>honkitは、コンテンツをWebサイト(カスタマイズ可能および拡張可能)または電子ブック(PDF、ePubまたはMobi)として出力できます。  
>honkitはGitBook(Legacy)のフォークです。

引用：https://honkit.netlify.app/

簡単に言えば、『Github PagesにMDを使ったドキュメント形式のサイトを簡単につくれちゃうよー。しかも全部無料で！』ってぼくは認識しました(((PDFのことは知らん🙄

旧GitBookを現HonKitに改良した中心人物がazuさんです。
- https://github.com/azu
- https://efcl.info/

JavaScriptの勉強できる [jsprimer](https://jsprimer.net/) も azuさんを中心にHonKitで作られています。ちなみに、[https://efcl.info/](https://efcl.info/) ここは Jekyll を使って作られています。

***
## 目的と所感

目的としては、[公式サイト](https://honkit.netlify.app/)を見てもどうしたらいいのかよくわからかった事が多かったから単に導入から使い方までをまとめる。  
想定しているユーザーは、「複数人で無料でコンテンツをさくさくと公開する」をしたい管理担当者になる。  
ただし、自分ひとりだけの場合は [現Gitbook](https://www.gitbook.com/) や [HackMD](https://hackmd.io/) などを使ったほうが良い。

また、デザインへのこだわりがあったり技術的に問題がないのなら、[Hugo](https://themes.gohugo.io/tags/docs/)やGatsbyのほうがいい。個人的にはReactの[Docusaurus](https://docusaurus.io/)が一番いいんじゃないかと思う。
あと、Jekyllにも[Gitbookのテーマ](https://sighingnow.github.io/jekyll-gitbook/)があった。

絶対に無料でクレカ登録なしという前提でこれら全部を試してみたところ、身内向けにストック型の情報共有としてHonKitは打って付けだと思う。  
イメージとしては高校や大学などのサークルや教授などまたは同人やサバゲーやオンラインサロンや野球チームなどで、限定管理者もメンバーも入れ替わりが想定されるミニマルな組織やチームにあってるような気がした。

技術担当ではないメンバーが、記事を投稿する際の学習コストがMarkdownの記述構法だけというのは安い。ましてやDiscodeやメモアプリなどで触れている人も少なくはないだろう。

WEBエンジニアを志したもののJSやPHPで挫折してしまった人や、フロントエンドに携わらないのに「パソコン詳しいっしょ！」と理不尽な扱いを受けてしまう諸兄にもHonKitの利用を一考してほしい。

---

※リスペクトしているだけで回し者ではありますん