---
layout: post
title:  "构建可扩展的数据可视化系统的一种思路"
---

这里的数据可视化系统是指类似于 [Tableau](https://www.tableau.com/) 和 [Metabase](https://metabase.com/) 这种可以让用户通过简单拖拽生成图表的系统。这类系统要在易用性和功能上维持一种微妙的平衡：既要用起来简单，又要功能强大；既要对小白友好，又要让专业人士满意。这篇文章不会讨论交互问题，主要提供一种构建这类系统的思路。



核心流程可以分成以下几步：

1. 用户交互生成 sql dsl 和 图表 ui dsl
2. sql dsl 生成 sql
3. 执行 sql 得到 查询结果, 合并到 ui dsl 中
4. 渲染 ui dsl 得到



#### A  JSON to SQL Translator

首先这只是一个 JSON 到 SQL 的翻译器，它有点类似于 SQL 的语法树，跟 GraphQL 之类不是同一个概念。

大概是这种形式：

```json
{                                                                                      
  table: "users",
 	condition: [{name: 'id', op: '>', value: 10}]
	fields: [
  	{name: "id", source: "users"},
		{ name: "zoneName", source: "users", alias: "zone"}
	]
}
```

生成的 sql 大概这样：

```sql
SELECT id, zoneName AS zone FROM users WHERE id > 10
```

实际比这个例子要复杂得多， `group by`, `join`, `order` , 子查询等 SQL 对应的语法基本都有。

为什么需要这种转换 ?

1. 方便从用户交互生成查询。比如用户拖入一个过滤条件，直接在这个 condition push 一个过滤条件就好了。但是如果直接操作 SQL 字符串就很麻烦，必须先 parse SQL, `WHERE` 里增加一个 `AND` 再生成 SQL 字符串
2. 抹平数据库方言间的差异。比如有的用 MySQL，有的用 Presto, 不需要总为那些方言细节操心。

#### A Visualization Grammar

数据可视化本质上是数据到图形属性的映射。*The Grammar of Graphics* 提供了刚刚好的抽象。

```json
{
  "$schema": "https://vega.github.io/schema/vega-lite/v3.json",
  "description": "A simple bar chart with embedded data.",
  "data": {
    "values": [
      {"a": "A","b": 28}, {"a": "B","b": 55}, {"a": "C","b": 43},
      {"a": "D","b": 91}, {"a": "E","b": 81}, {"a": "F","b": 53},
      {"a": "G","b": 19}, {"a": "H","b": 87}, {"a": "I","b": 52}
    ]
  },
  "mark": "bar",
  "encoding": {
    "x": {"field": "a", "type": "ordinal"},
    "y": {"field": "b", "type": "quantitative"}
  }
}
```

即可得到最简单的柱状图：

![柱状图](https://wx1.sinaimg.cn/mw690/006Ve2YMly1g3hhy7pnh9j30ec0eqwey.jpg)