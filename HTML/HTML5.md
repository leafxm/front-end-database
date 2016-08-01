# 关于HTML5

HTML5主要有新标签、新表单特性、Canvas、数据存储、新的网络连接协议web socket、模拟多线程的web worker，还有引入多媒体、地理应用等方面的内容。
##新的Doctype
HTML5 不基于 SGML，所以不需要引用 DTD。只需使用```<!DOCTYPE html>  ```即可。
## 新标签
html5新增了一些结构型和语义化的标签，比如：section、header、footer、nav、article和aside、figure等。

其中，section用来定义文档中的区域（或节），nav表示主导航区域，article侧重于表示是内容片断，而aside用来表示与页面内容松散相关的内容，可用来做侧边栏、引文、广告等。

## 表单元素
###1. input元素
html5提供了让```<input>```的type特性有更多的值：

- email
- url
- number 属性有 max min step value（初始值）
- range 调节杆效果 属性同number
- datepickers (date, month, week, time, datetime, datetime-local)
- search 和搜索引擎交互的
- color 选择颜色以RGB方式记录显示
- progress 进度条
 
也有一些新属性：

- list： <datalist> 元素的 ID，该元素的内容，<option> 元素被用作提示信息，会在 input 的建议区域作为提议显示出来。
- pattern： 一个正则表达式，用于检查控件的值，能够作用于 type 值是 text， tel， search， url， 和 email 的 input 元素。
- form： 一个字符串，用于表明该 input 属于哪个 <form> 元素。一个 input 只能存在于一个表单中。

###2. datalist元素
datalist 元素规定输入域的选项列表。列表通过 datalist 内的 option 元素创建的。

	<input id="awardWon" name="awardWon" type="text" list="awards">
	<datalist id="awards">
	  <select>
	    <option value="Best Picture"></option>
	    <option value="Best Director"></option>
	  </select>
	</datalist>

### 3.output元素
自动提交计算结果

###4. 新属性
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


## Web socket
是一种不同于HTTP的通信协议。最大特点是可以双向通信。事件驱动，常见事件有open、message、error、close等。使用send方法发送数据，监听message事件来接收服务器发回的数据。可以持续连接数据流，流量小，适合做监听状态的工作，游戏、股票、实时视频等。使用全双工工作方式。

WebSocket是Web应用程序的传输协议，它提供了双向的，按序到达的数据流。他是一个HTML5协议，WebSocket的连接是持久的，他通过在客户端和服务器之间保持双工连接，服务器的更新可以被及时推送给客户端，而不需要客户端以一定时间间隔去轮询。


## Web Worker
当在 HTML 页面中执行脚本时，页面的状态是不可响应的，直到脚本已完成。

web worker 是运行在后台的 JavaScript，独立于其他脚本，不会影响页面的性能。主要作用是模拟出web多线程。子线程完全受主线程控制，不可访问 DOM APIs。

可以用于：

- 数据的计算和加密，如计算斐波拉契函数的值，特别费时；再比如文件的 MD5 值比对，一个大文件的 MD5 值计算也是很费时的。
- 音、视频流的编解码工作，这些工作搞微信的技术人员应该没有少做。有兴趣的童鞋可以看看这个技术分享，是杭州的 hehe123 搞的一个WebRTC 分享，内容还不错。
- 等等费时间的事情

worker主线程,模拟多线程:

1. 通过 worker = new Worker( url ) 加载一个JS文件来创建一个worker，同时返回一个worker实例。 
2. 通过worker.postMessage( data ) 方法来向worker发送数据。 
3. 绑定worker.onmessage方法来接收worker发送过来的数据。 
4. 可以使用 worker.terminate() 来终止一个worker的执行。


## 多媒体
引入```<vidio>```和```<audio>```标签。

## draggable属性
给元素设置draggable="true"，它就可以被拖拽了。通过拖放事件，可以控制拖放相关的各个方面。

拖动一个元素时，将依次触发下列事件（作用于被拖动的元素）：

1. dragstart 按下鼠标键并开始移动鼠标时，会在被拖放的元素上触发
2. drag 元素被拖动期间会持续触发该事件
3. dragend 拖动停止时触发（无论是把元素放到了有效的放置目标，还是无效的放置目标上）

默认情况下，浏览器不会在拖动期间改变被拖动元素的外观，但你可以自己修改。不过，大多数浏览器会为正被拖动的元素创建一个半透明的副本，这个副本始终跟随着光标移动。

当元素被拖放到一个有效的放置目标上时，下列事件会依次发生（作用于作为放置目标的元素）：

1. dragenter 元素被拖动到放置目标上时触发
2. dragover 被拖动的元素还在放置目标的范围内移动时，就会持续触发该事件
3. drop 被拖拽的元素在目标元素上同时鼠标放开触发该事件
	
在dragover中一定要执行preventDefault()，否则ondrop事件不会被触发。

dataTransfer 对象是事件e的对象，用来保存被拖拽的数据。有用来设置拖拽效果的属性和用来设置拖拽数据的方法。
dropEffect 属性可以知道被拖动的元素能够执行哪种放置行为（有none,move,copy,link)。只有搭配effectAllowed 属性才有用(ondragstart 事件处理程序中设置)。effectAllowed 属性表示允许拖动元素的哪种dropEffect。

## contentEditable 属性
通过在元素上设置contentEditable="true"可以让元素变成可编辑状态。

## data 属性
使用“data-”开头定义自定义属性。在js中可以通过getAttribute来获得，在css中可以通过attr()来获得，可以用于给hover伪类的content赋值。

## 跨文档消息传递
postMessage()方法接收两个参数：一条消息和一个表示消息接收方来自哪个域的字符串，接收到消息会触发message事件,其事件对象包含data，origin，source三个属性

## 历史状态管理
history.pushState()方法，该方法可以接收三个参数：状态对象、新状态的标题和可选的相对URL。还有popState()方法和replaceState方法。