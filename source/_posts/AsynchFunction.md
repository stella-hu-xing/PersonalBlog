---
title: Async functions - making promises friendly
date: 2017-08-01 11:12:10
tags: JavaScript
---
## What is asynchronized function?

Async functions allow you to write promise-based code as if it were synchronous, but without blocking the main thread. They make your asynchronous code less "clever" and more readable.

__Async functions always return a promise, whether you use await or not.__ That promise resolves with whatever the async function returns, or rejects with whatever the async function throws.

### 异步过程
异步函数实际上很快就调用完成了。但是后面还有工作线程执行异步任务、通知主线程、主线程调用回调函数等很多步骤。我们把整个过程叫做异步过程。异步函数的调用在整个异步过程中，只是一小部分。

一个异步过程通常是这样的：
主线程发起一个异步请求，相应的工作线程接收请求并告知主线程已收到(异步函数返回)；主线程可以继续执行后面的代码，同时工作线程执行异步任务；工作线程完成工作后，通知主线程；主线程收到通知后，执行一定的动作(调用回调函数)。

异步函数通常具有以下的形式：
```
A(args..., callbackFn)
```
从主线程的角度看，一个异步过程包括下面两个要素：
* 发起函数(或叫注册函数)A
* 回调函数callbackFn
它们都是在主线程上调用的，其中注册函数用来发起异步过程，回调函数用来处理结果。

// 注意：前面说的形式A(args..., callbackFn)只是一种抽象的表示，并不代表回调函数一定要作为发起函数的参数，例如：
```
var xhr = new XMLHttpRequest();
xhr.onreadystatechange = xxx; // 添加回调函数
xhr.open('GET', url);
xhr.send(); // 发起函数
发起函数和回调函数就是分离的。
```