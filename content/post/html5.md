---
draft: false
showonlyimage: true
writer: "eliden"
image: "headerimg/1.jpg"
date: "2018-09-05"
categories: [ "H5C3"]
weight: 3
title: "HTML5笔记"
---

<!--more-->

### 操作类的方法

>1. jquery操作类的方法：addClass() removeClass() toggleClass() hasClass()

>2. h5也有类似的api 基于一个对象classList的方法 add() remove() toggle() contains()

```
var dom = document.querySelector('li:nth-child(2)');

/*1.获取类*/
console.log(dom.classList);
/* DOM.classList 获取的是这个DOM元素上的所有class */

/*2.操作类*/
dom.classList.add('blue');
dom.classList.remove('red');
```

### 自定义属性

>1.自定义属性 data-* 自定义属性

>2.获取元素的自定义属性 jquery获取方式 $('div').data('自定义属性的名称)

>3.自定义属性的名称是什么？ data-user==>user data-user-name==>userName

>4.命名规则 遵循驼峰命名法

>5.获取元素的自定义属性 h5的方式 dataset 自定义属性的集合

```
<div data-user="wl" data-user-age="18"></div>
```

- jquery

>/*获取所有 $('div').data() */

>/*获取单个自定义属性 $('div').data('user')*/

>/*设置单个属性 $('div').data('user','gg')*/


- h5原生api

>获取所有  var set = div.dataset;

>获取单个自定义属性 var user = set.user;var user = set['user'];

>设置单个属性 set.user = 'gg';


### h5 全屏api
>通过添加私有前缀来兼容
```
video.webkitRequestFullScreen();
document.webkitCancelFullScreen();
```

```
document.querySelector('.btn1').onclick = function () {
/*全屏操作*/
/*每一个元素都有全屏方法*/
/*H5的api存在兼容问题*/
/*在IE9以下不支持 加也没有用*/
/*但是在高级浏览器新版本支持，但是需要加上私有前缀*/
/*私有前缀：css (-webkit-,-moz-,-ms-,-o-) */
/*在js当中也有私有前缀 在方法属性之前加上就可以 首字母大小*/
//document.querySelector('video').webkitRequestFullScreen();
```

```
/*页面文档全屏*/
//document.querySelector('body').webkitRequestFullScreen();
document.documentElement.webkitRequestFullScreen();
//document.querySelector('.box').webkitRequestFullScreen();
}
document.querySelector('.btn2').onclick = function () {
/*取消全屏 跟元素没有关系*/
document.webkitCancelFullScreen();
}
```

```
    /*全屏操作后 自带的控制栏会显示 在显示的时候隐藏*/
    video::-webkit-media-controls {
        display: none !important;
    }

    .controls {
        width: 700px;
        height: 40px;
        background-color: rgba(255, 255, 255, 0.2);
        border-radius: 4px;
        position: absolute;
        left: 50%;
        margin-left: -350px;
        bottom: 5px;
        /*比全屏的状态下的视频元素高*/
        z-index: 100000000000;
        opacity: 1;
    }

    .player:hover .controls {
        opacity: 1;
    }
```


### 案例

```
<!DOCTYPE html>
<html>
<head lang="en">
    <meta charset="UTF-8">
    <title>视频播放</title>
    <!--字体图标库-->
    <link rel="stylesheet" href="css/font-awesome.css"/>
    <link rel="stylesheet" href="css/player.css"/>
</head>
<body>
<figure>
    <figcaption>视频播放器</figcaption>
    <div class="player">
        <video src="./video/fun.mp4"></video>
        <div class="controls">
            <!--播放/暂停-->
            <a href="javascript:;" class="switch fa fa-play"></a>
            <!--播放进度-->
            <div class="progress">
                <div class="line"></div>
                <div class="bar"></div>
            </div>
            <!--当前播放时间/播放总时长-->
            <div class="timer">
                <span class="current">00:00:00</span> / <span class="total">00:00:00</span>
            </div>
            <!--全屏/取消全屏-->
            <a href="javascript:;" class="expand fa fa-arrows-alt"></a>
        </div>
    </div>
</figure>
<script src="./js/jquery.min.js"></script>
<script>
    $(function () {
        /*获取需要操作的dom元素*/
        /*多媒体相关的api都是dom元素提供的*/
        var $video = $('video');

        var video = $video.get(0);

        var $total = $('.total');

        var $switch = $('.switch');

        var $line = $('.line');

        var $current = $('.current');

        var $expand = $('.expand');

        var $bar = $('.bar');

        var formatTime = function (time) {
            /* 01:02:20 格式 */
            /*time 3666 => 01:01:06 */
            var h = Math.floor(time / 3600);
            var m = Math.floor(time % 3600 / 60);
            var s = Math.floor(time % 60);
            return (h >= 10 ? h : '0' + h) + ':' + (m >= 10 ? m : '0' + m) + ':' + (s >= 10 ? s : '0' + s);
        };


        /*1.加载效果 总时长显示*/
        video.oncanplay = function () {
            $video.show();
            /*总时长获取 video.duration*/
            $total.html(formatTime(video.duration));
        }

        /*2.播放功能 / 暂停功能*/
        $switch.on('click', function () {
            /*判断当前的播放状态*/
            if ($switch.hasClass('fa-play')) {
                /*播放*/
                video.play();
                /*暂停按钮*/
                $switch.removeClass('fa-play').addClass('fa-pause');
            } else {
                /*暂停*/
                video.pause();
                /*播放按钮*/
                $switch.addClass('fa-play').removeClass('fa-pause');
            }
        });

        /*3.播放中进度条显示 当前播放时间的显示*/
        video.ontimeupdate = function () {
            /* 当前播放时间 console.log(video.currentTime);*/
            $current.html(formatTime(video.currentTime));
            /*进度显示 通过长度 百分比*/
            var ratio = video.currentTime / video.duration;
            var p = ratio * 100 + '%';
            $line.css('width', p);
        };

        /*4.全屏/取消全屏*/
        $expand.on('click', function () {
            if ($expand.hasClass('fa-arrows-alt')) {
                /*全屏操作*/
                video.webkitRequestFullScreen();
                /*改按钮 收起全屏按钮*/
                $expand.removeClass('fa-arrows-alt').addClass('fa-compress');
            } else {
                /*取消全屏*/
                document.webkitCancelFullScreen();
                /*改按钮 全屏按钮*/
                $expand.addClass('fa-arrows-alt').removeClass('fa-compress');
            }
        });

        /*5.跃进功能*/
        $bar.on('click', function (e) {
            /*获取点击的位置和进度条宽度的比例*/
            /*通过比例去计算播放时间*/
            /*把播放时间设置好了 进度也会改变*/
            var width = $bar.width();
            /* e.offsetX e.offsetY 当前点击的地方 距离坐标的坐标和上边的坐标 相对于当前元素的 */
            var place = e.offsetX;
            /*计算播放时间*/
            var time = place / width * video.duration;
            /*设置*/
            video.currentTime = time;
            /*触发 播放时间更改事件 */
            /*必须视频加载完成的时候才能看到效果 */
            /*遇到跃进没有效果 file形式打开页面 */
        })

        /*6.播放完毕重置功能*/
        video.onended = function () {
            video.currentTime = 0;
            /*播放按钮*/
            $switch.addClass('fa-play').removeClass('fa-pause');
        }
    })
</script>
</body>
</html>

```

### 地理定位


>在桌面浏览器使用geolocation会遇到网络阻塞问题 （国内政策）

>PositionError {code: 2, message: "Network location provider at 'https://www.googleapis.com/' : No response received."}

```
<script>
    if (navigator.geolocation) {
        /*getCurrentPosition 获取当前定位信息*/
        navigator.geolocation.getCurrentPosition(function (position) {
            /*获取定位信息成功*/
            /*position 定位信息对象*/
            /*position 属性 coords 坐标对象*/
            /*coords 有 经纬度 海拔 ... */
            /* latitude 维度 longitude 经度 */

        }, function (PositionError) {
            /*获取定位信息失败*/
            /*PositionError 失败信息*/
        })
    }
</script>
```

```
<script>

    /*h5 geolocation */
    if (navigator.geolocation) {
        navigator.geolocation.getCurrentPosition(function (position) {
            /*获取定位成功回调函数*/
            /*定位数据*/
            console.log(position);
            var latitude = position.coords.latitude;
            var longitude = position.coords.longitude;

// 这些都是写死
            var map = new BMap.Map("container"); // container表示显示哪个容器
// 把经度纬度传给百度
            /*40.1691162668,116.6348530780*/
            var point = new BMap.Point(longitude, latitude);
//默认的比例
            map.centerAndZoom(point, 20);
//添加鼠标滚动缩放
            map.enableScrollWheelZoom();
// 只写上面三行就可出现地图了，并且会定位
// 定义好了一个图片标记
            var myIcon = new BMap.Icon("1.png", new BMap.Size(128, 128));
// 创建标注
            var marker = new BMap.Marker(point, {icon: myIcon});
            map.addOverlay(marker);
//点击地图，获取经纬度坐标
            map.addEventListener("click", function (e) {
                console.log("经度坐标：" + e.point.lng + " 纬度坐标：" + e.point.lat);
            });
        }, function (error) {
            /*获取定位失败回调函数*/
            /*失败原因*/
            console.log(error)
        });
    }

    // 这些都是写死
    var map = new BMap.Map("container"); // container表示显示哪个容器
    // 把经度纬度传给百度
    /*40.1691162668,116.6348530780*/
    var point = new BMap.Point(116.6348530780, 40.1691162668);
    //默认的比例
    map.centerAndZoom(point, 20);
    //添加鼠标滚动缩放
    map.enableScrollWheelZoom();
    // 只写上面三行就可出现地图了，并且会定位
    // 定义好了一个图片标记
    var myIcon = new BMap.Icon("1.png", new BMap.Size(128, 128));
    // 创建标注
    var marker = new BMap.Marker(point, {icon: myIcon});
    map.addOverlay(marker);
    //点击地图，获取经纬度坐标
    map.addEventListener("click", function (e) {
        console.log("经度坐标：" + e.point.lng + " 纬度坐标：" + e.point.lat);
    });

</script>
```
