# -Web-
响应式Web设计 - HTML5和CSS3实战，Ben Frain 著，王永强 译，读书笔记



第一章 响应式网页

$: 响应式网页设计(RWD,Responsive Web Design)，
由Ethan Marcotte提出，是将三种已有的开发技巧(弹性网格布局、弹性图片、媒体和媒体查询)进行整合，如果用一句话概括就是针对任意设备对网页内容进行完美布局的一种显示机制。

$: 视口和屏幕尺寸
视口是指浏览器窗口内的内容区域，不包含工具栏、标签栏等。也就是网页的实际显示区域。
屏幕尺寸是指设备的物理显示区域。



第二章 媒体查询：支持不同的视口

$: CSS3的媒体查询模块，可以针对设备特性(如视口宽度)设置特定的CSS样式。它是由媒体类型和一个或多个检测媒体特性的条件表达式组成。

$:媒体查询语法：
1> <link rel="stylesheet" type="text/css" media="screen and (orientation:portrait) and (min-width:800px)" href="screen-style.css">
满足media条件，则加载screen-style.css样式文件。

2> @media screen and (max-width:960px){/*样式*/} （推荐）
在CSS文件中加入这些代码，针对特定屏幕使用特定样式。

3> @import url("phone.css") screen and (max-width:360px);
通过@import引入CSS文件，但是切记，使用这种方式会增加HTTP请求，进而影响加载速度，使用时需谨慎。

$: 媒体查询可以检测到哪些特性？
width: 视口宽度
height: 视口高度
device-width: 渲染表面的宽度(一般指设备屏幕的宽度)
device-height: 渲染表面的高度(一般指设备屏幕的高度)
orientation: 检查设备处于横向还是纵向
aspect-ratio：基于视口宽度和高度的宽高比。如16:9比例的显示屏可以定义为aspect-ratio:16/9
device-aspect-ratio: 基于设备渲染平面的宽高比
resolution: 用来检测屏幕或打印机的分辨率
grid: 用来检测输出设备是网格设备还是位图设备

$: 阻止移动浏览器自动调整页面大小
<meta name="viewpoint" content="initial-scale=2.0,width=device-width" /> 插入<head>标签之中
width:可视区域的宽度，值可为数字或关键词device-width
height:同width
intial-scale:页面首次被显示是可视区域的缩放级别，取值1.0则页面按实际尺寸显示，无任何缩放
maximum-scale=1.0, minimum-scale=1.0;可视区域的缩放级别，
maximum-scale用户可将页面放大的程序，1.0将禁止用户放大到实际尺寸之上。
user-scalable:是否可对页面进行缩放，no 禁止缩放

$: 使用meta阻止移动浏览器自动调整页面大小后，可以使用媒体查询来针对特定设备设置专有样式。

$: 响应式设计中内容始终优先
窄视口设备的用户应该先看到主内容，再看到侧边栏。“内容优先”原则，HTML代码中的内容区域应该放在侧边栏区域前，这样默认显示时会先显示内容区域，然而在大视口中，由于设置了内容区域和侧边栏区域的浮动，因此，不会影响正常显示。即
<article>内容</article>
<nav>侧边栏</nav>
