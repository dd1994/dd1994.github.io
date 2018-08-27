---
layout: post
title:  "应用ECMAScript 规范"
---

Types: <http://www.ecma-international.org/ecma-262/6.0/#sec-ecmascript-language-types>

> A function object is an object that supports the [[Call]] internal methods. 

<http://ecma-international.org/ecma-262/8.0/>
typeof operator <http://www.ecma-international.org/ecma-262/6.0/#sec-typeof-operator>

`typeof` Undeclared

```javascript
Function.prototype.apply.length // 2
Function.prototype.call.length // 1
Function.prototype.bind.length // 1
```

`Object.is`, `===` 和 `==`

`window.isNaN` `Number.isNaN`

`Object.prototype.toString()` http://www.ecma-international.org/ecma-262/6.0/#sec-object.prototype.tostring
