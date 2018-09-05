---
draft: true
showonlyimage: true
writer: "eliden"
image: "headerimg/1.jpg"
date: "2018-09-05"
categories: [ "H5C3"]
weight: 1
title: "css常用代码块"
---

<!--more-->

## 清除浮动

```
.clear:after{
content:'.';
display:block;
height:0;
overflow:hidden;
clear:both;
visibility:hidden;
}

```

##多行超出省略

```
.text-ellipsis{
overflow: hidden;
white-space: nowrap;
text-overflow: ellipsis;
}
```
## 单行文字结尾省略号 要用复合属性

```
width:
white-space： nowrap
text-overflow ：ellipsis
overfow： hidden
```

## google html5 shiv

```
<!--[if IE]>
<script src=”http://html5shiv.googlecode.com/svn/trunk/html5.js”></script>;;
< ![endif]-->
```

## 音频最好的 HTML 解决方法

```
<audio controls>
<source src="horse.mp3" type="audio/mpeg">
<source src="horse.ogg" type="audio/ogg">
<embed height="50" width="100" src="horse.mp3">
</audio>
```

## 视频最好的 HTML 解决方法
```
<video width="320" height="240" controls autoplay>
<source src="movie.ogg" type="video/ogg">
<source src="movie.mp4" type="video/mp4">
<source src="movie.webm" type="video/webm">
<object data="movie.mp4" width="320" height="240">
<embed width="320" height="240" src="movie.swf">
</object>
</video>
```

## 优酷解决方案

>在 HTML 中显示视频的最简单的方法是使用优酷等视频网站。
如果您希望在网页中播放视频，那么您可以把视频上传到优酷等视频网站，然后在您的网页中插入 HTML 代码即可播放视频：
```
<embed src="http://player.youku.com/player.php/sid/XMzI2NTc4NTMy/v.swf";; width="480" height="400" type="application/x-shockwave-flash"> </embed>
```

##  插入背景音乐

```
<embed src="背景音乐网址" hidden="true" autostart="true" loop="true">
```

>--------hidden="true"表示隐藏播放，即不显示播放器的外观，若要想显示，把"true" 替换为"false"即可，这样为默认是最小化播放，若还想具体显示播放器的大小，另加上height="高度值" width="宽度值" 就可以了。
>-------autostart="true"表示当前页一载入则自动播放，若不希望播放改为autostart="false"
>------ loop="true"表示无限次循环播放音乐直到当前页关闭为止，不想循环播放替换为 loop="false"就OK了


## 利用css 属性border制作各种三角形
@(http://www.qdfuns.com/notes/38552/fec24ec339f14938b5259bb7eda4f778.html)

```
<style>
.t2{
margin: 40px auto;
width: 0px;
height: 0px;
/*background-color: #f0ac6b;*/
border-bottom: 40px solid transparent;
border-right: 40px solid red;
/*border-left: 20px solid transparent;*/
}
</style>
```

### 内容垂直居中
```
.container { min-height: 6.5em; display: table-cell; vertical-align: middle; }
```
##  垂直居中

方法一：
```
<div>
<img src="" alt="">
<span></span>
</div>

<style>
div {
text-align: center;
}
img {
vertical-align: middle;
}
div span {
display: inline-block;
width: 0;
height:100%;
vertical-align: middle;
}
</style>
```
方法二：

>外盒子相对 或 绝对定位
>内盒子 position: absolute;top:0; bottom:0; left:0; right:0;margin:auto;


```
.box {
height:300px;
width: 300px;
border:1px solid blue;
position: relative;
}
.box div {
height: 30px;
width:30px;
background-color: red;
position: absolute;
top:0;
bottom:0;
left:0;
right:0;
margin:auto;
}
```

方法三 定位50% 然后负边距


## 不定宽度居中方法

加入 table 标签
设置 display: inline 方法：与第一种类似，显示类型设为 行内元素，进行不定宽元素的属性设置
设置 position:relative 和 left:50%：利用 相对定位 的方式，将元素向左偏移 50% ，即达到居中的目的

为什么选择方法一加入table标签? 是利用table标签的长度自适应性---即不定义其长度也不默认父元素body的长度（table其长度根据其内文本长度决定），因此可以看做一个定宽度块元素，然后再利用定宽度块状居中的margin的方法，使其水平居中。
第一步：为需要设置的居中的元素外面加入一个 table 标签 ( 包括 <tbody>、<tr>、<td> )。
第二步：为这个 table 设置“左右 margin 居中”（这个和定宽块状元素的方法一样）。
举例如下：
```
<div>
<table>
<tbody>
<tr><td>
<ul>
<li>我是第一行文本</li>
<li>我是第二行文本</li>
<li>我是第三行文本</li>
</ul>
</td></tr>
</tbody>
</table>
</div>
css代码：
<style>
table{ border:1px solid; margin:0 auto; }
</style>
```

## 通用媒体查询
```
/* Smartphones (portrait and landscape) ----------- */
@media only screen and (min-device-width : 320px) and (max-device-width : 480px) { /* Styles */ }
/* Smartphones (landscape) ----------- */
@media only screen and (min-width : 321px) { /* Styles */ }
/* Smartphones (portrait) ----------- */
@media only screen and (max-width : 320px) { /* Styles */ }
/* iPads (portrait and landscape) ----------- */
@media only screen and (min-device-width : 768px) and (max-device-width : 1024px) { /* Styles */ }
/* iPads (landscape) ----------- */
@media only screen and (min-device-width : 768px) and (max-device-width : 1024px) and (orientation : landscape) { /* Styles */ }
/* iPads (portrait) ----------- */
@media only screen and (min-device-width : 768px) and (max-device-width : 1024px) and (orientation : portrait) { /* Styles */ }
/* Desktops and laptops ----------- */
  @media only screen and (min-width : 1224px) { /* Styles */ }

/*Large screens ----------- */
@media only screen and (min-width : 1824px) { /* Styles */ }

/* iPhone 4 ----------- */
  @media only screen and (-webkit-min-device-pixel-ratio:1.5), only screen and (min-device-pixel-ratio:1.5) { /* Styles */ }
```

## 制作小竖线

```
.spacer{
            overflow: hidden;
            margin: 11px 5px 0;
            width: 1px;
            height: 10px;
            background-color: #ccc;
        }
```

## 实用的60个CSS代码片段
http://www.jianshu.com/p/e878122a92a3

### 垂直对齐
如果你用CSS，则你会有困惑：我该怎么垂直对齐容器中的元素？现在，利用CSS3的Transform，可以很优雅的解决这个困惑：
.verticalcenter{ position: relative; top: 50%; -webkit-transform: translateY(-50%); -o-transform: translateY(-50%); transform: translateY(-50%); }
使用这个技巧，从单行文本、段落到box，都会垂直对齐。目前浏览器对Transform的支持是需要关注的，
Chrome 4, Opera 10, Safari 3, Firefox 3, and Internet Explorer 9均支持该属性



### 伸展一个元素到窗口高度
在具体场景中，你可能想要将一个元素伸展到窗口高度，基本元素的调整只能调整容器的大小,因此要使一个元素伸展到窗口高度，
我们需要伸展顶层元素：html和body:
html, body { height: 100%; }
然后将100%应用到任何元素的高
div { height: 100%; }

### 基于文件格式使用不同的样式
为了更容易知道链接的目标，有时你想让一些链接看起来和其它的不同。下面的片段在文本链接前添加一个图标，对不同的资源使用不同的图标或图片：
```
a[href^="http://";;]{ padding-right: 20px; background: url(external.gif) no-repeat center right; }
/* emails */ a[href^="mailto:"]{ padding-right: 20px; background: url(email.png) no-repeat center right; }
/* pdfs */ a[href$=".pdf"]{ padding-right: 20px; background: url(pdf.png) no-repeat center right; }
```

### 创建跨浏览器的图像灰度
灰度有时看起来简约和优雅，能为网站呈现更深层次的色调。在示例中，我们将对一个SVG图像添加灰度过滤：
```
<svg xmlns="http://www.w3.org/2000/svg";>; <filter id="grayscale"> <feColorMatrix type="matrix" values="0.3333 0.3333 0.3333 0 0 0.3333 0.3333 0.3333 0 0 0.3333 0.3333 0.3333 0 0 0 0 0 1 0"/> </filter> </svg>
```
为了跨浏览器，会用到filter属性：
```
img { filter: url(filters.svg#grayscale); /* Firefox 3.5+ */ filter: gray; /* IE6-9 */ -webkit-filter: grayscale(1); /* Google Chrome, Safari 6+ & Opera 15+ */ }
```
###背景渐变动画
CSS中最具诱惑的一个功能是能添加动画效果，除了渐变，你可以给背景色、透明度、元素大小添加动画。目前，你不能为渐变添加动画，但下面的代码可能有帮助。它通过改变背景位置，让它看起来有动画效果。
```
button {
background-image: linear-gradient(#5187c4, #1c2f45);
background-size: auto 200%;
background-position: 0 100%; transition:
background-position 0.5s;
}

button:hover { background-position: 0 0; }
```

### CSS：表格列宽自适用
对于表格，当谈到调整列宽时，是比较痛苦的。然后，这里有一个可以使用的技巧：给td元素添加white-space: nowrap;能让文本正确的换行
```
td { white-space: nowrap; }
```

### 只在一边或两边显示盒子阴影
如果你要一个盒阴影，试试这个技巧，能为任一边添加阴影。为了实现这个，首先定义一个有具体宽高的盒子，然后正确定位:after伪类。实现底边阴影的代码如下
```
.box-shadow {
background-color:
#FF8020; width: 160px;
height: 90px;
margin-top: -45px;
margin-left: -80px;
position: absolute;
top: 50%;
left: 50%;
}
.box-shadow:after {
content: "";
width: 150px;
height: 1px;
margin-top: 88px;
margin-left: -75px;
display: block;
position: absolute;
left: 50%; z-index: -1;
-webkit-box-shadow: 0px 0px 8px 2px #000000;
-moz-box-shadow: 0px 0px 8px 2px #000000;
box-shadow: 0px 0px 8px 2px #000000;
}
```

### 包裹长文本
如果你碰到一个比自身容器长的文本，这个技巧对你很有用。
在这个示例中，默认时，不管容器的宽度，文本都将水平填充。

简单的CSS代码就能在容器中调整文本：
```
pre { white-space: pre-line; word-wrap: break-word; }
```

### 制造模糊文本
想要让文本模糊？可以使用color透明和text-shadow实现
```
.blurry-text { color: transparent; text-shadow: 0 0 5px rgba(0,0,0,0.5); }
```

### 用CSS动画实现省略号动画
这个片段将帮助你制造一个ellipsis的动画，对于简单的加载状态是很有用的，而不用去使用gif图像。
```
.loading:after {
overflow: hidden;
display: inline-block;
vertical-align: bottom;
animation: ellipsis 2s infinite;
content: "\2026"; /* ascii code for the ellipsis character */
}
  @keyframes ellipsis { from { width: 2px; } to { width: 15px; } }
```

### 跨浏览器的透明
```
.transparent {

filter: alpha(opacity=50);   /* internet explorer */

-khtml-opacity: 0.5;   /* khtml, old safari */

-moz-opacity: 0.5;   /* mozilla, netscape */

opacity: 0.5; /* fx, safari, opera */ }
```
### CSS引用模板
```
blockquote { background: #f9f9f9; border-left: 10px solid #ccc; margin: 1.5em 10px; padding: .5em 10px; quotes: "\201C""\201D""\2018""\2019"; } blockquote:before { color: #ccc; content: open-quote; font-size: 4em; line-height: .1em; margin-right: .25em; vertical-align: -.4em; } blockquote p { display: inline; }
```

### 个性圆角
```
#container { -webkit-border-radius: 4px 3px 6px 10px; -moz-border-radius: 4px 3px 6px 10px; -o-border-radius: 4px 3px 6px 10px; border-radius: 4px 3px 6px 10px; } /* alternative syntax broken into each line */ #container { -webkit-border-top-left-radius: 4px; -webkit-border-top-right-radius: 3px; -webkit-border-bottom-right-radius: 6px; -webkit-border-bottom-left-radius: 10px; -moz-border-radius-topleft: 4px; -moz-border-radius-topright: 3px; -moz-border-radius-bottomright: 6px; -moz-border-radius-bottomleft: 10px; }
```
### 现代字体栈
```
/* Times New Roman-based serif */ font-family: Cambria, "Hoefler Text", Utopia, "Liberation Serif", "Nimbus Roman No9 L Regular", Times, "Times New Roman", serif; /* A modern Georgia-based serif */ font-family: Constantia, "Lucida Bright", Lucidabright, "Lucida Serif", Lucida, "DejaVu Serif," "Bitstream Vera Serif", "Liberation Serif", Georgia, serif; /*A more traditional Garamond-based serif */ font-family: "Palatino Linotype", Palatino, Palladio, "URW Palladio L", "Book Antiqua", Baskerville, "Bookman Old Style", "Bitstream Charter", "Nimbus Roman No9 L", Garamond, "Apple Garamond", "ITC Garamond Narrow", "New Century Schoolbook", "Century Schoolbook", "Century Schoolbook L", Georgia, serif; /*The Helvetica/Arial-based sans serif */ font-family: Frutiger, "Frutiger Linotype", Univers, Calibri, "Gill Sans", "Gill Sans MT", "Myriad Pro", Myriad, "DejaVu Sans Condensed", "Liberation Sans", "Nimbus Sans L", Tahoma, Geneva, "Helvetica Neue", Helvetica, Arial, sans-serif; /*The Verdana-based sans serif */ font-family: Corbel, "Lucida Grande", "Lucida Sans Unicode", "Lucida Sans", "DejaVu Sans", "Bitstream Vera Sans", "Liberation Sans", Verdana, "Verdana Ref", sans-serif; /*The Trebuchet-based sans serif */ font-family: "Segoe UI", Candara, "Bitstream Vera Sans", "DejaVu Sans", "Bitstream Vera Sans", "Trebuchet MS", Verdana, "Verdana Ref", sans-serif; /*The heavier "Impact" sans serif */ font-family: Impact, Haettenschweiler, "Franklin Gothic Bold", Charcoal, "Helvetica Inserat", "Bitstream Vera Sans Bold", "Arial Black", sans-serif; /*The monospace */ font-family: Consolas, "Andale Mono WT", "Andale Mono", "Lucida Console", "Lucida Sans Typewriter", "DejaVu Sans Mono", "Bitstream Vera Sans Mono", "Liberation Mono", "Nimbus Mono L", Monaco, "Courier New", Courier, monospace;
```
### 自定义文本选择
```
::selection { background: #e2eae2; } ::-moz-selection { background: #e2eae2; } ::-webkit-selection { background: #e2eae2; }
```

### 为logo隐藏H1
```
h1 { text-indent: -9999px;width: 320px; height: 85px; background: transparent url("images/logo.png") no-repeat scroll; }
```

### 锚链接伪类
```
a:link { color: blue; } a:visited { color: purple; } a:hover { color: red; } a:active { color: yellow; }
```

### CSS3：全屏背景
```
html { background: url('images/bg.jpg') no-repeat center center fixed; -webkit-background-size: cover; -moz-background-size: cover; -o-background-size: cover; background-size: cover; }
```

### 大字段落
```
p:first-letter{ display: block; margin: 5px 0 0 5px; float: left; color: #ff3366; font-size: 5.4em; font-family: Georgia, Times New Roman, serif; }
```
###内部CSS3 盒阴影
```
#mydiv { -moz-box-shadow: inset 2px 0 4px #000; -webkit-box-shadow: inset 2px 0 4px #000; box-shadow: inset 2px 0 4px #000; }
```
### 外部CSS3 盒阴影
```
#mydiv { -webkit-box-shadow: 0 2px 2px -2px rgba(0, 0, 0, 0.52); -moz-box-shadow: 0 2px 2px -2px rgba(0, 0, 0, 0.52); box-shadow: 0 2px 2px -2px rgba(0, 0, 0, 0.52); }
```


### CSS固定页脚
```
#footer { position: fixed; left: 0px; bottom: 0px; height: 30px; width: 100%; background: #444; } /* IE 6 */ * html #footer { position: absolute; top: expression((0-(footer.offsetHeight)+(document.documentElement.clientHeight ? document.documentElement.clientHeight : document.body.clientHeight)+(ignoreMe = document.documentElement.scrollTop ? document.documentElement.scrollTop : document.body.scrollTop))+'px'); }
```

###IE6的PNG透明修复
```
.bg { width:200px; height:100px; background: url(/folder/yourimage.png) no-repeat; _background:none; _filter:progid:DXImageTransform.Microsoft.AlphaImageLoader(src='/folder/yourimage.png',sizingMethod='crop'); } /* 1px gif method */ img, .png { position: relative; behavior: expression((this.runtimeStyle.behavior="none")&&(this.pngSet?this.pngSet=true:(this.nodeName == "IMG" && this.src.toLowerCase().indexOf('.png')>-1?(this.runtimeStyle.backgroundImage = "none", this.runtimeStyle.filter = "progid:DXImageTransform.Microsoft.AlphaImageLoader(src='" + this.src + "', sizingMethod='image')", this.src = "images/transparent.gif"):(this.origBg = this.origBg? this.origBg :this.currentStyle.backgroundImage.toString().replace('url("','').replace('")',''), this.runtimeStyle.filter = "progid:DXImageTransform.Microsoft.AlphaImageLoader(src='" + this.origBg + "', sizingMethod='crop')", this.runtimeStyle.backgroundImage = "none")),this.pngSet=true)); }
```

### 强制换行
```
pre { white-space: pre-wrap; /* css-3 */ white-space: -moz-pre-wrap; /* Mozilla, since 1999 */ white-space: -pre-wrap; /* Opera 4-6 */ white-space: -o-pre-wrap; /* Opera 7 */ word-wrap: break-word; /* Internet Explorer 5.5+ */ }
```

### H1-H5默认样式
```
h1,h2,h3,h4,h5{ color: #005a9c; } h1{ font-size: 2.6em; line-height: 2.45em; } h2{ font-size: 2.1em; line-height: 1.9em; } h3{ font-size: 1.8em; line-height: 1.65em; } h4{ font-size: 1.65em; line-height: 1.4em; } h5{ font-size: 1.4em; line-height: 1.25em; }
```

### CSS悬浮提示文本
```
a { border-bottom:1px solid #bbb; color:#666; display:inline-block; position:relative; text-decoration:none; } a:hover, a:focus { color:#36c; } a:active { top:1px; } /* Tooltip styling */ a[data-tooltip]:after { border-top: 8px solid #222; border-top: 8px solid hsla(0,0%,0%,.85); border-left: 8px solid transparent; border-right: 8px solid transparent; content: ""; display: none; height: 0; width: 0; left: 25%; position: absolute; } a[data-tooltip]:before { background: #222; background: hsla(0,0%,0%,.85); color: #f6f6f6; content: attr(data-tooltip); display: none; font-family: sans-serif; font-size: 14px; height: 32px; left: 0; line-height: 32px; padding: 0 15px; position: absolute; text-shadow: 0 1px 1px hsla(0,0%,0%,1); white-space: nowrap; -webkit-border-radius: 5px; -moz-border-radius: 5px; -o-border-radius: 5px; border-radius: 5px; } a[data-tooltip]:hover:after { display: block; top: -9px; } a[data-tooltip]:hover:before { display: block; top: -41px; } a[data-tooltip]:active:after { top: -10px; } a[data-tooltip]:active:before { top: -42px; }
```


### 论文页面的卷曲效果
```
ul.box { position: relative; z-index: 1; /* prevent shadows falling behind containers with backgrounds */ overflow: hidden; list-style: none; margin: 0; padding: 0; } ul.box li { position: relative; float: left; width: 250px; height: 150px; padding: 0; border: 1px solid #efefef; margin: 0 30px 30px 0; background: #fff; -webkit-box-shadow: 0 1px 4px rgba(0, 0, 0, 0.27), 0 0 40px rgba(0, 0, 0, 0.06) inset; -moz-box-shadow: 0 1px 4px rgba(0, 0, 0, 0.27), 0 0 40px rgba(0, 0, 0, 0.06) inset; box-shadow: 0 1px 4px rgba(0, 0, 0, 0.27), 0 0 40px rgba(0, 0, 0, 0.06) inset; } ul.box li:before, ul.box li:after { content: ''; z-index: -1; position: absolute; left: 10px; bottom: 10px; width: 70%; max-width: 300px; /* avoid rotation causing ugly appearance at large container widths */ max-height: 100px; height: 55%; -webkit-box-shadow: 0 8px 16px rgba(0, 0, 0, 0.3); -moz-box-shadow: 0 8px 16px rgba(0, 0, 0, 0.3); box-shadow: 0 8px 16px rgba(0, 0, 0, 0.3); -webkit-transform: skew(-15deg) rotate(-6deg); -moz-transform: skew(-15deg) rotate(-6deg); -ms-transform: skew(-15deg) rotate(-6deg); -o-transform: skew(-15deg) rotate(-6deg); transform: skew(-15deg) rotate(-6deg); } ul.box li:after { left: auto; right: 10px; -webkit-transform: skew(15deg) rotate(6deg); -moz-transform: skew(15deg) rotate(6deg); -ms-transform: skew(15deg) rotate(6deg); -o-transform: skew(15deg) rotate(6deg); transform: skew(15deg) rotate(6deg); }
```

### 带CSS3特色的横幅显示  可以哟
```
.featureBanner { position: relative; margin: 20px } .featureBanner:before { content: "Featured"; position: absolute; top: 5px; left: -8px; padding-right: 10px; color: #232323; font-weight: bold; height: 0px; border: 15px solid #ffa200; border-right-color: transparent; line-height: 0px; box-shadow: -0px 5px 5px -5px #000; z-index: 1; } .featureBanner:after { content: ""; position: absolute; top: 35px; left: -8px; border: 4px solid #89540c; border-left-color: transparent; border-bottom-color: transparent; }
```


