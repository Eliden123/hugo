---
draft: true
showonlyimage: true
writer: "eliden"
image: "headerimg/2.jpg"
date: "2018-09-05"
categories: [ "H5C3"]
weight: 5
title: "关于margin上下重叠的问题"
---

<!--more-->

[搬运于：CSDN](https://blog.csdn.net/icesschen/article/details/52443364)

>有两种情况：

1、兄弟级的块之间，margin这个属性上下边距，经常会发生重叠的情况，以数值大的为准，而不会相加。

2、父子级的块之间，子级的上下margin会与父级上下margin重叠，以数值大的为准，而不会相加。

>如何解决？


第一种情况：
1、float浮动  或者  2、inline-block


第二种情况：
父级加
1、overflow:hidden
或者
 2、加padding


3、加border
或者
子级加position:absolute


若本身设计稿样式有所限制，无法用以上的属性。那么根据实际情况来调整，可以使用padding来代替margin。^_^