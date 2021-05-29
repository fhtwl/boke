--- 
title: nodejs学习 -- 中间件概念理解
date: 2020-07-02
categories: 
 - backEnd
tags: 
 - nodejs
 - 中间件
---

## 中间件是什么
    nodejs中，中间件主要指封装所有http请求处理细节的方法<br/>
    前端发送http请求，中间件可以对请求进行处理<br>

## 语法
中间件是一个方法（函数），并需要使用use方法注册，可以注册多个中间件，koa默认执行第一个中间件，其它的中间件需要手动执行
```javascript
app.use(async (ctx,next=>{
    ...
    await next()
})

const text = async (ctx,next => {
    ...
    await next()
}
app.use(text)

```
其中，中间件默认有两个返回值，ctx表示上下文，next表示下一个中间件函数。一般会在中间件函数里执行next()，表示继续执行下一个中间件函数


