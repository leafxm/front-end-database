# 关于HTML5

HTML5
HTML5 中的一些有趣的新特性：
•	用于绘画的 canvas 元素
•	用于媒介回放的 video 和 audio 元素
•	对本地离线存储的更好的支持
•	新的特殊内容元素，比如 article、footer、header、nav、section
•	新的表单控件，比如 calendar、date、time、email、url、search
•	 
HTML 5 Canvas vs. SVG
SVG
SVG 是一种使用 XML 描述 2D 图形的语言。
可以为某个元素附加 JavaScript 事件处理器。
在 SVG 中，每个被绘制的图形均被视为对象。如果 SVG 对象的属性发生变化，那么浏览器能够自动重现图形。
Canvas
Canvas 通过 JavaScript 来绘制 2D 图形。
Canvas 是逐像素进行渲染的。
在 canvas 中，一旦图形被绘制完成，它就不会继续得到浏览器的关注。如果其位置发生变化，那么整个场景也需要重新绘制，包括任何或许已被图形覆盖的对象。
Canvas 与 SVG 的比较
下表列出了 canvas 与 SVG 之间的一些不同之处。
Canvas
•	依赖分辨率
•	不支持事件处理器
•	弱的文本渲染能力
•	能够以 .png 或 .jpg 格式保存结果图像
•	最适合图像密集型的游戏，其中的许多对象会被频繁重绘
SVG
•	不依赖分辨率
•	支持事件处理器
•	最适合带有大型渲染区域的应用程序（比如谷歌地图）
•	复杂度高会减慢渲染速度（任何过度使用 DOM 的应用都不快）
•	不适合游戏应用
WEB存储
HTML5 提供了两种在客户端存储数据的新方法：
•	localStorage - 没有时间限制的数据存储
•	sessionStorage - 针对一个 session 的数据存储。当用户关闭浏览器窗口后，数据会被删除。
HTML5 使用 JavaScript 来存储和访问数据。

应用程序缓存
 Cache Manifest
Web Worker
当在 HTML 页面中执行脚本时，页面的状态是不可响应的，直到脚本已完成。
web worker 是运行在后台的 JavaScript，独立于其他脚本，不会影响页面的性能。您可以继续做任何愿意做的事情：点击、选取内容等等，而此时 web worker 在后台运行。模拟出web多线程
服务器发送事件
Server-Sent 事件 - 单向消息传递
Server-Sent 事件指的是网页自动获取来自服务器的更新。
以前也可能做到这一点，前提是网页不得不询问是否有可用的更新。通过服务器发送事件，更新能够自动到达。
例子：Facebook/Twitter 更新、估价更新、新的博文、赛事结果等。
表单
Input类型：
•	email （自动验证）
•	url （自动验证）
•	number  
•	range  
•	Date pickers (date, month, week, time, datetime, datetime-local)  
•	search 表现为普通文本域，用于搜索域
•	color 点击选择颜色

表单元素
datalist 元素
datalist 元素规定输入域的选项列表。
列表是通过 datalist 内的 option 元素创建的。
如需把 datalist 绑定到输入域，请用输入域的 list 属性引用 datalist 的 id：
 

keygen 元素
keygen 元素的作用是提供一种验证用户的可靠方法。
keygen 元素是密钥对生成器（key-pair generator）。当提交表单时，会生成两个键，一个是私钥，一个公钥。
私钥（private key）存储于客户端，公钥（public key）则被发送到服务器。公钥可用于之后验证用户的客户端证书（client certificate）。
目前，浏览器对此元素的糟糕的支持度不足以使其成为一种有用的安全标准。

output 元素
output 元素用于不同类型的输出，比如计算或脚本输出：

表单属性
新的 input 属性：
•	autocomplete 自动完成 on/off
•	autofocus 自动地获得焦点
•	form规定输入域所属的一个或多个表单
•	form overrides (formaction, formenctype, formmethod, formnovalidate, formtarget) 表单重写属性
•	height 和 width 定用于 image 类型的 input 标签的图像高度和宽度
•	list 规定输入域的 datalist。datalist 是输入域的选项列表。
•	min, max 和 step
•	multiple 规定输入域中可选择多个值
•	pattern (regexp) 
•	placeholder 描述输入域所期待的值
•	required 必须在提交之前填写输入域（不能为空）