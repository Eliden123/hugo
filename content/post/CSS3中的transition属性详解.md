---
draft: true
showonlyimage: true
writer: "eliden"
image: "headerimg/1.jpg"
date: "2018-09-05"
categories: [ "H5C3"]
weight: 20
title: "CSS3中的transition属性详解"
---

<!--more-->

[搬运于：博客园](https://www.cnblogs.com/afighter/p/5731293.html)

一、语法

transition: property duration timing-function delay

transition属性是个复合属性，她包括以下几个子属性：

transition-property ：规定设置过渡效果的css属性名称
transition-duration ：规定完成过渡效果需要多少秒或毫秒
transition-timing-function ：指定过渡函数，规定速度效果的速度曲线
transition-delay ：指定开始出现的延迟时间
默认值分别为：all 0 ease 0

注：transition-duration 时长为0，不会产生过渡效果

改变多个css属性的过渡效果时：

a{ transition: background 0.8s ease-in 0.3s,color 0.6s ease-out 0.3s;}



二、子属性

transition-property
transition-property: none |all |property;

值为none时，没有属性会获得过渡效果，值为all时，所有属性都将获得过渡效果，值为指定的css属性应用过渡效果，多个属性用逗号隔开

transition-duration
transition-duration：time;

该属性主要用来设置一个属性过渡到另一个属性所需的时间，也就是从旧属性过渡到新属性花费的时间长度，俗称持续时间

transition-timing-function
transition-timing-function：linear| ease| ease-in| ease-out| ease-in-out| cubic-bezier(n,n,n,n);

该属性指的是过渡的“缓动函数”。主要用来指定浏览器的过渡速度，以及过渡期间的操作进展情况，解释下：

注意：值cubic-bezier(n,n,n,n)可以中定义自己的值，如 cubic-bezier(0.42,0,0.58,1)



复制代码
div {
  width: 100px;
  height: 100px;
  background-color: orange;
  margin: 20px auto;
  border-radius: 100%;
  -webkit-transition-property: -webkit-border-radius;
  transition-property: border-radius;
  -webkit-transition-duration: 3s;
  transition-duration: 3s;
  -webkit-transition-timing-function：ease;
 transition-timing-function：ease;

div:hover {
  border-radius: 0px;
}
复制代码
我试着换不同的值看看区别，但并不是很明显，把持续时间弄长点估计更能看出，但是因为gif太大怕传不上来所以就弄了3秒的时间。

ease:由快到慢到更慢



linear:恒速



ease-in:越来越快



ease-out:越来越慢



ease-in-out:先加速后减速





transition-delay
这个属性没什么说的了，就是过渡效果开始前的延迟时间，单位秒或者毫秒



再来个栗子：

复制代码
div {
  width: 200px;
  height: 200px;
  background: red;
  margin: 20px auto;
  -webkit-transition-property: background;
  transition-property:background;
  -webkit-transition-duration:.5s;
  transition-duration:.5s;
  -webkit-transition-timing-function: ease-in;
  transition-timing-function: ease-in;
  -webkit-transition-delay: .18s;
      transition-delay:.18s;
}
div:hover {
  background: #000;
}
复制代码








