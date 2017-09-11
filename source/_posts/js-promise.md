---
title: What is Promise in JavaScript
date: 2017-08-01 10:36:39
tags: JavaScript
---
## What is a Promise?
__A promise is an object that may produce a single value some time in the future__: either a resolved value, or a reason that it’s not resolved (e.g., a network error occurred). 

A promise may be in one of 3 possible states: _fulfilled(resolved), rejected, or pending_.

A promise is an object which can be returned synchronously from an asynchronous function. 有了 Promise 对象，就可以将异步操作以同步操作的流程表达出来，避免了层层嵌套的回调函数。此外，Promise 对象提供统一的接口，使得控制异步操作更加容易。 

A promise is settled if it’s not pending (it has been resolved or rejected). Sometimes people use resolved and settled to mean the same thing: not pending.

Once settled, a promise can not be resettled. Calling resolve() or reject() again will have no effect. The immutability of a settled promise is an important feature.

## Usage

All spec-compatible promises define a _.then()_ method which you use to pass handlers which can take the resolved or rejected value.
.then() must return a new promise, promise2.
```
promise.then(
  onFulfilled?: Function,
  onRejected?: Function
) => Promise
```
 Example:
```
// wait(3000) call will wait 3000ms (3 seconds), and then log 'Hello!'
const wait = time => new Promise((resolve) => setTimeout(resolve, time));

wait(3000).then(() => console.log('Hello!')); // 'Hello!'
```

## Important Promise Rules
A standard for promises was defined by the Promises/A+ specification community. There are many implementations which conform to the standard, including the JavaScript standard ECMAScript promises.

Promises following the spec must follow a specific set of rules:

* A promise or “thenable” is an object that supplies a standard-compliant .then() method.
* A pending promise may transition into a fulfilled or rejected state.
* A fulfilled or rejected promise is settled, and must not transition into any other state.
* Once a promise is settled, it must have a value (which may be undefined). That value must not change.

Change in this context refers to identity (===) comparison. An object may be used as the fulfilled value, and object properties may mutate.
