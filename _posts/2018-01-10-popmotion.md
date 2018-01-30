---
layout: post
title:  Popmotion
---


## 1. transformers

[transformers](https://popmotion.io/api/transformers/) 是一些高阶工具函数，与其它部分没有耦合，很容易看懂。

这个 `pipe` 函数，写得很漂亮

~~~javascript
const combineFunctions = (a: Function, b: Function) => (v: any) => b(a(v));

export const pipe = (...transformers: Function[]) => transformers.reduce(combineFunctions);
~~~

发现一个小错误：<https://github.com/Popmotion/popmotion/pull/254>
