---
layout: post
title:  Popmotion
---


## 1. transformers

这个 `pipe` 函数，写得很漂亮

~~~javascript
const combineFunctions = (a: Function, b: Function) => (v: any) => b(a(v));

export const pipe = (...transformers: Function[]) => transformers.reduce(combineFunctions);
~~~

发现一个小错误：<https://github.com/Popmotion/popmotion/pull/254>
