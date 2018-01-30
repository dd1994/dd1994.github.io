---
layout: post
title:  Popmotion
---


## transformers

~~~javascript
const combineFunctions = (a: Function, b: Function) => (v: any) => b(a(v));

export const pipe = (...transformers: Function[]) => transformers.reduce(combineFunctions);
~~~
