# Chapter 2についての補足

[TOPに戻る](https://ta-private.github.io/nodejs2-docs/)

## Chapter2

### Section2-3 テンプレートエンジンを使おう

#### テンプレートを表示させよう

ejsをインストールして、ファイル内容を修正後、サーバーを起動したところ、下記の画像のようなエラーが表示されることがあります。

```shell
$ node app.js
```

![ejsが見つからない](https://i.gyazo.com/f7f7c2387b41413c013836bbd012b77c.png)

このようなエラーが出た場合は、npmのモジュールを読み込むためのglobalモジュールの保存先のパスが正しく指定されていない可能性があります。その場合は、以下の対応を行っていただくと良いかと思います。

まずはnodeコマンドを実行

```shell
$ node
```

nodeにログインできましたら、

```shell
> global.module.paths.push('追加したいパス名');
```

![](https://i.gyazo.com/805afe149d05eb281de28cf1ee45d310.png)

上記の画像のような感じで指定いただければと思います。
パス名は、terminal上でcdコマンドを使って、

```shell
$ cd /home/ubuntu/.nvm/versions/node/
```
に移動してから、お使いのnodeのversionに合わせたパスを見つけてみてください。

新しいパスが追加できましたら、

```shell
$ echo "export NODE_PATH=`npm root -g`" >> /home/ubuntu/.bashrc
```

上記コマンドを実行してみてください。これで、先ほど追加した保存先のパスを読み込むことができるようになります。

設定ファイルである `.bashrcファイル` を変更しましたので、設定が反映されるように

```shell
exec bash -l
```

を実行してください。

設定が反映されましたので、それでは改めて、

```shell
node app.js
```

を実行してみてください。ちゃんとサーバーが正しく起動できましたでしょうか？
