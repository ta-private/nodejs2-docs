# Chapter 5についての補足

[TOPに戻る](https://ta-private.github.io/nodejs2-docs/)

## Chapter 5-2 サーバーからデータ取得

### Googleのニュースを表示する

GoogleニュースのRSS取得のためのURLが変更されました。

以下のURLが現在のURLですので、お使いください。

[https://news.google.com/rss?hl=ja&gl=JP&ceid=JP:ja](https://news.google.com/rss?hl=ja&gl=JP&ceid=JP:ja)

また、サーバーから直接、mysqlへのアクセスが制限されている可能性があります。node.jsからmysqlへのアクセスが上手くいかない場合は、mysqlにログインして、新しくmysqlユーザーを作成いただく必要があります。

```javascript
// 新規ユーザー作成
create user '新しいユーザー名'@'localhost' identified with mysql_native_password by '任意のパスワード';


// 権限を与える
GRANT ALL ON データベース名.* TO '新しいユーザー名'@'localhost';
