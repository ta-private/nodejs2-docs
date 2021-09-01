# Chapter 6についての補足

## 目次
- [Chapter 6についての補足](#chapter-6についての補足)
	- [目次](#目次)
	- [Chapter 6-1 バリデーション](#chapter-6-1-バリデーション)

## Chapter 6-1 バリデーション

`express-validator` の使用方法に変更がありましたので、以下の記述方法を参照してください。

```javascript
var express = require('express');
var router = express.Router();
var mysql = require('mysql');
const { check, validationResult } = require('express-validator/check');

var mysql_setting = {
    host : 'localhost',
    user : '任意のユーザー名',
    password : '任意のパスワード',
    database : 'my_nodeapp_db'
};

/***********
中略
************/


//新規作成フォーム送信の処理
router.post('/add', [
    check('name', 'NAMEは必ず入力してください。').isLength({ min: 5 }),
    check('mail', 'MAILはメールアドレスを記入してください').isLength({ min: 5 }).isEmail(),
    check('age', 'AGEは年齢（整数）を入力ください').not().isEmpty(),
    ],

    (req, res, next) => {

        // バリデーションの結果にエラーがあるかのチェック
        const errors = validationResult(req);
        // エラーがなかったら以降の処理が続く
        if (!errors.isEmpty()) {

            var re = '<ul class="error">';
            var result_arr = errors.array();
            for (var n in result_arr) {
                re += '<li>' + result_arr[n].msg + '</li>'
            }
            re += '</ul>';
            var data = {
                title: 'Hello/Add',
                content: re,
                form: req.body
            }
            res.render('hello/add', data);

        } else {

            var nm = req.body.name;
            var ml = req.body.mail;
            var ag = req.body.age;
            var data = {
                'name':nm,
                'mail':ml,
                'age':ag
            };

            var connection = mysql.createConnection(mysql_setting);
            connection.connect();
            connection.query('insert into mydata set ?', data,
            function(error, results, fields) {
                res.redirect('/hello');
            });
            connection.end();

        }
});


/***********
中略
************/

module.exports = router;
```




[TOPに戻る](https://ta-private.github.io/nodejs2-docs/)



