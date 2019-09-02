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

###### 回调函数：获取异步操作结果，上层定义，下层调用

function dyy(callback){    //定义一个函数，参数也是函数

​	setTimeout(function(){

​	var data = 'hello'

​	callback(data)

​	},1000)

}

dyy(function(data){        //调用这个函数，把这个匿名函数传进去

​	console.log(data)    **//这里面就是自己想要写的代码**

})

这个匿名函数是

for(var key in student){

​	stu[key] = student[key]  //key就是一个student的属性或下标

}

exports.find = function(callback){

​	fs.readFile(dbPath,'utf8',function(err,data){

​		if(err){

​			return callback(err)

​		}

​		callback(null,JSON.parse(data).students)

​	})

}