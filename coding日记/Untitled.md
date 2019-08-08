# node.js宿舍

express框架封装了很多东西，app就相当于http.creatServer的server了，

var express = require('express')

var app = express()

一个路径对应一个方法

app.get('/abc',function(req,res){

​	res.send('你好，我是Express!')

})

公开静态资源或指定的目录,第一个参数是url路径，这样就可以通过/public/xx的方式访问public目录里面的资源

app.use('/public/',express.statc('./public/'))

node.js是异步的，后面的输出可能在前面，很多API比如文件操作的API都是异步的

npm install --save express  == npm i -S express

npm init --yes

