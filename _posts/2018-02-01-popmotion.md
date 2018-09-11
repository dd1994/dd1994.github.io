---
layout: post
title:  Popmotion
---


## Transformers

[transformers](https://popmotion.io/api/transformers/) 是一些高阶工具函数，与其它部分没有耦合，很容易看懂。

这个 `pipe` 函数，写得很漂亮

~~~javascript
const combineFunctions = (a: Function, b: Function) => (v: any) => b(a(v));

export const pipe = (...transformers: Function[]) => transformers.reduce(combineFunctions);
~~~

发现一个小错误：<https://github.com/Popmotion/popmotion/pull/254>

## Calculators

[Calculators](https://popmotion.io/api/calc/) 大部分是一些距离和角度的计算，没啥好看的

## Easing

[Easing](https://popmotion.io/api/easing/) 都是一些贝塞尔曲线，没啥好看的