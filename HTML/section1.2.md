# 关于HTML5

HTML5主要有新标签、新表单特性、Canvas、数据存储、引入多媒体、新的网络连接协议、模拟多线程的web worker等方面的内容。
## 新标签
html5新增了一些结构型和语义化的标签，比如：section、header、footer、nav、article和aside、figure等。

其中，section用来定义文档中的区域（或节），nav表示主导航区域，article侧重于表示是内容片断，而aside用来表示与页面内容松散相关的内容，可用来做侧边栏、引文、广告等。

## 表单元素
### input元素
html5提供了让```<input>```的type特性有更多的值：

- email
- url
- number 属性有 max min step value（初始值）
- range 调节杆效果 属性同number
- datepickers (date, month, week, time, datetime, datetime-local)
- search 和搜索引擎交互的
- color 选择颜色以RGB方式记录显示
- progress 进度条
 
也有一些新特性：

- list： <datalist> 元素的 ID，该元素的内容，<option> 元素被用作提示信息，会在 input 的建议区域作为提议显示出来。
- pattern： 一个正则表达式，用于检查控件的值，能够作用于 type 值是 text， tel， search， url， 和 email 的 input 元素。
- form： 一个字符串，用于表明该 input 属于哪个 <form> 元素。一个 input 只能存在于一个表单中。

### datalist元素
datalist 元素规定输入域的选项列表。列表通过 datalist 内的 option 元素创建的。

<input id="awardWon" name="awardWon" type="text" list="awards">
<datalist id="awards">
  <select>
    <option value="Best Picture"></option>
    <option value="Best Director"></option>
  </select>
</datalist>

### output元素
自动提交计算结果

### 新属性
- autofocus 页面刚打开的时候焦点设置到某个文本框
- placeholder 输入之前的灰色的字，用来提醒
- required 表示必须输入，没输入会有异性
- autocomplete 可以设置为off来禁止自动完成功能

## Canvas 
一种新的绘制图形的方法。

### 和SVG的对比

SVG 是一种使用 XML 描述 2D 图形的语言，Canvas 通过 JavaScript 来绘制 2D 图形。对比如下：

| Canvas | SVG |
|-- | -- |
|依赖分辨率|不依赖分辨率|
|不支持事件处理器|支持事件处理器|
|弱的文本渲染能力|最适合带有大型渲染区域的应用程序（比如谷歌地图）|
|最适合图像密集型的游戏，其中的许多对象会被频繁重绘|不适合游戏应用|

## 数据存储
HTML5 提供了两种在客户端存储数据的新方法：
- localStorage  没有时间限制的数据存储
- sessionStorage  针对一个 session 的数据存储。当用户关闭浏览器窗口后，数据会被删除。

HTML5 使用 JavaScript 来存储和访问数据。

应用程序缓存
 Cache Manifest
### 和cookie的对比

## 多媒体

## Web socket

## Web Worker
当在 HTML 页面中执行脚本时，页面的状态是不可响应的，直到脚本已完成。
web worker 是运行在后台的 JavaScript，独立于其他脚本，不会影响页面的性能。您可以继续做任何愿意做的事情：点击、选取内容等等，而此时 web worker 在后台运行。模拟出web多线程
服务器发送事件
Server-Sent 事件 - 单向消息传递
Server-Sent 事件指的是网页自动获取来自服务器的更新。
以前也可能做到这一点，前提是网页不得不询问是否有可用的更新。通过服务器发送事件，更新能够自动到达。
例子：Facebook/Twitter 更新、估价更新、新的博文、赛事结果等。


