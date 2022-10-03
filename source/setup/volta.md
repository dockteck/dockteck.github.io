# Volta

HonkitにはNodeが必要です。  
今回はWindowsを使うので [Volta](https://volta.sh/) を導入します。  
<https://volta.sh/>

公式ではJavaScriptツールマネージャーと言っていますが実質Nodeのパッケージ管理ツールです。プロジェクト毎に勝手に良しなにしてくれるいいやつです。  
env系より楽だと思いました。

詳細は下記のサイトに譲りさっそくインストールします。

---

先にWindowsの開発者モードを有効にしてください。  
Windowsの設定から `プライバシーとセキュリティ > 開発者向け`と進むと`開発者モード`が出てくるのでトグルボタンをオンにするだけです。

次にWindows用にインストーラーがあるので公式からダウンロードして指示に従います。pathなどは勝手にやってくれるのでらくちんです。  
ターミナルを開いて```volta -v```と入力してバージョンが表示されれば成功です。2022-10/03時点では1.0.8でした。

次にNodeをインストールします。入れたいバージョンが特になければLTSの最新を入れます。今日だと16.17.1です。

```bash
volta install node
```

試しにnpm-check-updatesを入れてみましょう。2行ありますがどちらを実行しても同じ結果です。yarnも使えます。

```bash
volta install npm-check-updates
```

```bash
npm i -g npm-check-updates
```

確認したいときは`volta list all`で詳細を確認できます。  
ちなみにnpm-check-updatesは`ncu -u`で実行できるのですが、NVIDIAのCUDAなどが入っているとコマンドが被ります。その時は`npm-check-updates -u`で実行すればおｋです。

---

VSCodeでの使用にあたっては、バージョンの指定や共有がなければ特になにもしなくても勝手にグローバルと切り分けてくれます。  
めちゃ楽です♪

おすすめの参考先
- https://zenn.dev/taichifukumoto/articles/how-to-use-volta
- https://zenn.dev/yumemi_inc/articles/2021-11-09-volta?redirected=1
