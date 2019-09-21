---
layout: post
title:  "图形语法: 图表的一种抽象方式"
---

(这是我在部门内部分享图形语法的文字稿，稍微修改掉了公司内部相关的东西)

## 引子

在 Excel 中如何选择一个图表。

![](https://si.geilicdn.com/img-7dac0000016cecee0f9a0a21924b-unadjust_1066_1224.png)

## 思考

如何抽象，定义最基本的元素，在这之上描述所有的图表（或者尽量接近这个目的)

核心问题：数据 => 图表

## The Grammar of Graphics

Leland Wilkinson 写于 1999 年(第二版: 2011 年)

## 基本思想

基本元素:

![](https://zos.alipayobjects.com/skylark/313254aa-ff97-4396-9192-3c0f8fc16867/attach/2378/da07b27fb885206a/image.png)

## 核心抽象：

```
数据到图形属性的映射
```

图形的属性：位置，颜色，大小，透明度等等

## 映射

通过数据到图形属性的映射的方式构建一个气泡图:

![](https://si.geilicdn.com/img-32d90000016ced2122500a21167e-unadjust_866_854.png)

气泡图的图形属性:
1. 气泡的位置（x 坐标，y 坐标）
2. 气泡的颜色，
3. 气泡的大小， 

## 组合

几何标记的组合

![](https://si.geilicdn.com/img-393e0000016ced4984690a211587-unadjust_978_958.png)

雷达图: 极坐标下的折线图
饼图: 极坐标下的柱状图

![](https://si.geilicdn.com/img-46df0000016ced0fee820a21924b-unadjust_768_552.png)

举例 2: 
![](https://si.geilicdn.com/img-211b0000016ced26da910a21924a-unadjust_916_912.png)

![](https://si.geilicdn.com/img-17900000016ced4ddffe0a21924b-unadjust_1492_910.png)

## 图形语法思想的实现

* R语言最流行的绘图包 [ggplot2](https://ggplot2.tidyverse.org)
* [G2](https://antv.alipay.com/zh-cn/g2/3.x/index.html): 命令式编程，API 类似 ggplot2. 
* [vega/vaga-lite](https://vega.github.io/vega-lite/): JSON 配置生成图表，Python, JS 等多语言实现, [vega-lite 的柱状图示例](https://vega.github.io/editor/#/examples/vega-lite/bar)
* [Tableau](https://www.tableau.com): 可视化的实现，非常强大，无须写代码就可以生成各种图表。

## 思考通用可视化系统
* 映射的交互方式
* 可组合性
* 通用性
* 如何取数
* why not
* ...
