# Chapter 7についての補足

## 目次
- [Chapter 7についての補足](#chapter-7についての補足)
	- [目次](#目次)
	- [Chapter 7-1 DB版ミニ掲示板](#chapter-7-1-db版ミニ掲示板)
		- [Bookshelfのバージョンについて](#bookshelfのバージョンについて)

## Chapter 7-1 DB版ミニ掲示板

### Bookshelfのバージョンについて

書籍では、

```shell
npm install --save bookshelf
```

となっていますが、各種ライブラリとの互換性等で、以下のエラーが発生する場合があります。

```shell
Unhandled rejection CustomError: EmptyResponse
    at Child.<anonymous> (/home/ubuntu/environment/mini_board_2/node_modules/bookshelf/lib/model.js:719:21)
```

その場合は、Bookshelfをアンインストールして、再度、ダウングレードしたものをインストールしてください。

```shell
# アンインストール
npm uninstall bookshelf

# ダウングレードしてインストール
npm install --save bookshelf@0.13.3
```

上記の対応で、一度対応してみてください。



[TOPに戻る](https://ta-private.github.io/nodejs2-docs/)

