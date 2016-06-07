# HTML基础知识

## 什么是 HTML？
HTML 是用来描述网页的一种语言。
- HTML 指的是超文本标记语言 (Hyper Text Markup Language)
- HTML 不是一种编程语言，而是一种标记语言 (markup language)

## 插入样式表的方式
- 外部样式表

      <head>
          <link rel="stylesheet" type="text/css" href="mystyle.css">
      </head>
- 内部样式表

在 head 部分通过 ```<style>``` 标签定义内部样式表。

- 内联样式

## 标签
### ```<img>```标签

```<img> ```是空标签，意思是说，它只包含属性，并且没有闭合标签。

属性有：
- 源属性（src）：src 指 "source"。源属性的值是图像的 URL 地址。
- 替换文本属性（alt 属性）：在浏览器无法载入图像时，告诉读者他们失去的信息。此时，浏览器将显示这个替代性的文本而不是图像。
- align属性，对其方式，有"bottom"”middle””top”,以及使其浮动的”left””right”

### 自定义列表
是项目及其注释的组合：自定义列表以``` <dl>``` 标签开始，每个自定义列表项以``` <dt> ```开始，每个自定义列表项的定义以 ```<dd>``` 开始。

    <dl>
      <dt>Coffee</dt>
      <dd>Black hot drink</dd>
      <dt>Milk</dt>
      <dd>White cold drink</dd>
    </dl>
浏览器显示如下：
 <dl>
      <dt>Coffee</dt>
      <dd>Black hot drink</dd>
      <dt>Milk</dt>
      <dd>White cold drink</dd>
    </dl>
列表项内部可以使用段落、换行符、图片、链接以及其他列表等等。
## <!DOCTYPE>
<!DOCTYPE> 不是 HTML 标签。它为浏览器提供一项信息（声明），即 HTML 是用什么版本编写的。

在 HTML 4.01 中，<!DOCTYPE> 声明引用 DTD（Document Type Definition，文档类型定义），因为 HTML 4.01 基于 SGML。DTD 规定了标记语言的规则，这样浏览器才能正确地呈现内容。

HTML5 不基于 SGML，所以不需要引用 DTD。

## ```<head>``` 元素

是所有头部元素的容器，其中的元素可包含脚本，指示浏览器在何处可以找到样式表，提供元信息，等等，比如：
```<title>、<base>、<link>、<meta>、<script> 以及 <style>```。


其中 ```<base> ``` 元素为页面上的所有链接规定默认地址或默认目标（target）：

      <head>
        <base href="http://www.w3school.com.cn/images/" />
        <base target="_blank" />
      </head>
      
HTML <meta> 元素
元数据（metadata）是关于数据的信息。
<meta> 标签提供关于 HTML 文档的元数据。元数据不会显示在页面上，但是对于机器是可读的。
典型的情况是，meta 元素被用于规定页面的描述、关键词、文档的作者、最后修改时间以及其他元数据。
元数据可用于浏览器（如何显示内容或重新加载页面），搜索引擎（关键词），或其他 web 服务。
针对搜索引擎的关键词
一些搜索引擎会利用 meta 元素的 name 和 content 属性来索引您的页面。
下面的 meta 元素定义页面的描述：
<meta name="description" content="Free Web tutorials on HTML, CSS, XML" />
下面的 meta 元素定义页面的关键词：
<meta name="keywords" content="HTML, CSS, XML" />
name 和 content 属性的作用是描述页面的内容。

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


面试题目
标签
•	行内元素有哪些？块级元素有哪些？ 空(void)元素有那些？
CSS规范规定，每个元素都有默认的display值，如div的display默认值为“block”，则为“块级”元素；span默认display属性值为“inline”，是“行内”元素。
（1）行内元素有：a span img input select strong
（2）块级元素有：div ul ol li dl dt dd h1-h6 p
（3）常见的空元素：<br> <hr> <img> <input> <link> <meta>
•	<strong>，<em>和<b>，<i>标签
从表现形式上来看，<em> 和<i>都是表现为斜体，<strong>和<b>都是表现为加粗。
从意义上来看，<b> <i>是视觉要素，分别表示无意义的加粗，无意义的斜体。 <em> 和 <strong> 是表达要素(phrase elements)。< em > （emphasized text）表示一般的强调文本，而 < strong > （strong emphasized text）表示比 < em > 语义更强的的强调文本。
•	label的作用是什么？是怎么用的？
label标签来定义表单控件间的关系,当用户选择该标签时，浏览器会自动将焦点转到和标签相关的表单控件上。
<label for="Name">Number:</label>
<input type=“text“name="Name" id="Name"/>
<label>Date:<input type="text" name="B"/></label>
•	iframe有那些缺点？
是什么：iframe 元素会创建包含另外一个文档的内联框架（即行内框架）
缺点：iframe会阻塞主页面的Onload事件；
iframe和主页面共享连接池，而浏览器对相同域的连接有限制，所以会影响页面的并行加载。
使用iframe之前需要考虑这两个缺点。如果需要使用iframe，最好是通过javascript动态给iframe添加src属性值，这样可以可以绕开以上两个问题。
兼容
•	常见兼容性问题？
o	png24位的图片在iE6浏览器上出现背景，解决方案是做成PNG8.
o	浏览器默认的margin和padding不同。解决方案是加一个全局的*{margin:0;padding:0;}来统一。
o	浮动ie产生的双倍距离 #box{ float:left; width:100px; margin:0 0 0 10px;}这种情况之下IE会产生20px的距离，解决方案是在float的标签样式控制中加入 _display:inline;将其转化为行内属性。(_这个符号只有ie6会识别)
o	解决ie的兼容性问题，可以使用渐进识别的方式，从总体中逐渐排除局部。首先，巧妙的使用“\9”这一标记，将IE游览器从所有情况中分离出来。接着，再次使用“+”将IE8和IE7、IE6分离开来，这样IE8已经独立识别。
  .bb{
 background-color:#f1ee18;/*所有识别*/
 .background-color:#00deff\9; /*IE6、7、8识别*/
  +background-color:#a200ff;/*IE6、7识别*/
_background-color:#1e0bd1;/*IE6识别*/
}
o	IE下,可以使用获取常规属性的方法来获取自定义属性,也可以使用getAttribute()获取自定义属性;Firefox下,只能使用getAttribute()获取自定义属性.解决方法:统一通过getAttribute()获取自定义属性.
o	IE下,event对象有x,y属性,但是没有pageX,pageY属性;Firefox下,event对象有pageX,pageY属性,但是没有x,y属性.解决方法：（条件注释）缺点是在IE浏览器下可能会增加额外的HTTP请求数。
o	Chrome 中文界面下默认会将小于 12px 的文本强制按照 12px 显示,可通过加入 CSS 属性 -webkit-text-size-adjust: none; 解决.
o	超链接访问过后hover样式就不出现了 被点击访问过的超链接样式不在具有hover和active了.解决方法是改变CSS属性的排列顺序:L-V-H-A : a:link {} a:visited {} a:hover {} a:active {}
HTML5相关问题
•	HTML5 为什么只需要写 <!DOCTYPE HTML>？
HTML5 不基于 SGML，因此不需要对DTD进行引用，但是需要doctype来规范浏览器的行为（让浏览器按照它们应该的方式来运行）；而HTML4.01基于SGML,所以需要对DTD进行引用，才能告知浏览器文档所使用的文档类型。
•	html5有哪些新特性、移除了那些元素？如何处理HTML5新标签的浏览器兼容问题？如何区分 HTML 和HTML5？
HTML5 现在已经不是 SGML 的子集，主要是关于图像，位置，存储，多任务等功能的增加。新特性有：
绘画 canvas ；用于媒介回放的 video 和 audio 元素
本地离线存储 localStorage 长期存储数据，浏览器关闭后数据不丢失
sessionStorage 的数据在浏览器关闭后自动删除
语意化更好的内容元素，比如 article、footer、header、nav、section
表单控件，calendar、date、time、email、url、search
新的技术webworker, websockt, Geolocation
o	移除的元素
纯表现的元素：basefont，big，center，font, s，strike，tt，u；
对可用性产生负面影响的元素：frame，frameset，noframes；
o	兼容性问题：
IE8/IE7/IE6支持通过document.createElement方法产生的标签，
可以利用这一特性让这些浏览器支持HTML5新标签，浏览器支持新标签后，
还需要添加标签默认的样式；
当然最好的方式是直接使用成熟的框架、使用最多的是html5shim框架
<!--[if lt IE 9]>
<script> src="http://html5shim.googlecode.com/
svn/trunk/html5.js"</script>
<![endif]-->
•	HTML5的离线储存？
o	localStorage 长期存储数据，浏览器关闭后数据不丢失；
o	sessionStorage 数据在浏览器关闭后自动删除。
在用户没有与因特网连接时，可以正常访问站点或应用，在用户与因特网连接时，更新用户机器上的缓存文件。 原理：HTML5的离线存储是基于一个新建的.appcache文件的缓存机制(不是存储技术)，通过这个文件上的解析清单离线存储资源，这些资源就会像cookie一样被存储了下来。之后当网络在处于离线状态下时，浏览器会通过被离线存储的数据进行页面展示。
在离线状态时，操作window.applicationCache进行需求实现。
•	浏览器是怎么对HTML5的离线储存资源进行管理和加载的呢？
在线的情况下，浏览器发现html头部有manifest属性，它会请求manifest文件，如果是第一次访问app，那么浏览器就会根据manifest文件的内容下载相应的资源并且进行离线存储。如果已经访问过app并且资源已经离线存储了，那么浏览器就会使用离线的资源加载页面，然后浏览器会对比新的manifest文件与旧的manifest文件，如果文件没有发生改变，就不做任何操作，如果文件改变了，那么就会重新下载文件中的资源并进行离线存储。离线的情况下，浏览器就直接使用离线存储的资源。
•	HTML5的form如何关闭自动完成功能？
o	给不想要提示的 form 或下某个input 设置为 autocomplete=off。
其他
•	Doctype作用？标准模式与兼容模式各有什么区别?
o	（1）、<!DOCTYPE>声明位于HTML文档中的第一行，处于标签之前。告知浏览器的解析器用什么文档标准解析这个文档。DOCTYPE不存在或格式不正确会导致文档以兼容模式呈现。
o	（2）、标准模式的排版 和JS运作模式都是以该浏览器支持的最高标准运行。在兼容模式中，页面以宽松的向后兼容的方式显示,模拟老式浏览器的行为以防止站点无法工作。
•	你知道多少种Doctype文档类型？
o	该标签可声明三种 DTD 类型，分别表示严格版本、过渡版本以及基于框架的 HTML 文档。
o	HTML 4.01 规定了三种文档类型：Strict、Transitional 以及 Frameset。
o	XHTML 1.0 规定了三种 XML 文档类型：Strict、Transitional 以及 Frameset。
o	Standards （标准）模式（也就是严格呈现模式）用于呈现遵循最新标准的网页，而 Quirks（包容）模式（也就是松散呈现模式或者兼容模式）用于呈现为传统浏览器而设计的网页。
•	XHTML和HTML的区别？
o	1.所有的标记都必须要有一个相应的结束标记
o	2.所有标签的元素和属性的名字都必须使用小写
o	3.所有的XML标记都必须合理嵌套
o	4.所有的属性必须用引号""括起来
o	5.把所有<和&特殊符号用编码表示
o	6.给所有属性赋一个值
o	7.不要在注释内容中使“--”
o	8.图片必须有说明文字

•	content="application/xhtml+xml;"是什么意思？
wap2.0网站，使用的是xhtml mp语言。xhtml mp是xhtml的子集。
在xhml mp中，支持三种MIME类型
1.	application/vnd.wap.xhtml+xml
2.	application/xhtml+xml
3.	text/html
第一种类型是一些非智能手机的wap浏览器所需要的，以便正确显示XHTML MP文档。
第二种是XHTML系列文档的类型
第三种是HTML文档的类型。这样用IE6就可以正常浏览这些文档，而如果遇到上面的两种类型就会弹出一个对话框。
目前，为了兼容最低标准，很多网站使用的还是application/vnd.wap.xhtml+xml的mime类型。

•	如何实现网页的多语言版本？
o	静态：不同页面用不同语言展示
o	动态：对于动态页面文件（PHP，ASP等），可以使用语言变量
<script>, <script async> and <script defer>.
•	没有async或者defer，浏览器会在渲染这个脚本标签下的元素之前立即加载执行脚本，会阻塞页面渲染
•	加async，浏览器会在加载脚本的同时继续加载、渲染HTML页面，下载完成后暂停HTML解析立即执行脚本，所以有可能出现脚本执行顺序被打乱的情况
•	加defer，在下载脚本时HTML仍然在解析，HTML解析完成之后再按照原本的顺序执行脚本。但是不是所有浏览器都支持。

 
•	语义化的理解？
o	1，去掉或者丢失样式的时候能够让页面呈现出清晰的结构
o	2，有利于SEO：和搜索引擎建立良好沟通，有助于爬虫抓取更多的有效信息：爬虫依赖于标签来确定上下文和各个关键字的权重；
o	3，方便其他设备解析（如屏幕阅读器、盲人阅读器、移动设备）以意义的方式来渲染网页；
o	4，使阅读源代码的人对网站更容易将网站分块，便于阅读维护理解。
HTML5中新增加的很多标签（如：<article>、<nav>、<header>和<footer>等）就是基于语义化设计原则。
•	什么是 FOUC（无样式内容闪烁）？你如何来避免 FOUC？
FOUC - Flash Of Unstyled Content 文档样式闪烁
   <style type="text/css" media="all">@import "../fouc.css";</style>
而引用CSS文件的@import就是造成这个问题的罪魁祸首。IE会先加载整个HTML文档的DOM，然后再去导入外部的CSS文件，因此，在页面DOM加载完成到CSS导入完成中间会有一段时间页面上的内容是没有样式的，这段时间的长短跟网速，电脑速度都有关系。
解决方法简单的出奇，只要在<head>之间加入一个<link>或者<script>元素就可以了。
实现
•	如何在页面上实现一个圆形的可点击区域？
o	1、map+area或者svg
o	2、border-radius
o	3、纯js实现 需要求一个点在不在圆上简单算法、获取鼠标坐标等等
•	实现不使用 border 画出1px高的线，在不同浏览器的标准模式与怪异模式下都能保持一致的效果。
•	<div style="height:1px;overflow:hidden;background:#ccc"></div>
浏览器
•	浏览器的内核分别是什么?
o	Trident内核：IE,MaxThon,TT,The World,360,搜狗浏览器等。[又称MSHTML]
o	Gecko内核：Firefox，Netscape6及以上版本，MozillaSuite/SeaMonkey等
o	Presto内核：Opera7及以上。 [Opera内核原为：Presto，现为：Blink;]
o	Webkit内核：Safari,Chrome等。 [ Chrome的：Blink（WebKit的分支）]
•	介绍一下你对浏览器内核的理解？
通常所谓的浏览器内核也就是浏览器所采用的渲染引擎，渲染引擎决定了浏览器如何显示网页的内容以及页面的格式信息。不同的浏览器内核对网页编写语法的解释也有不同，因此同一网页在不同的内核的浏览器里的渲染（显示）效果也可能不同，这也是网页编写者需要在不同内核的浏览器中测试网页显示效果的原因。
主要分成两部分：渲染引擎(layout engineer或Rendering Engine)和JS引擎。
渲染引擎：负责取得网页的内容（HTML、XML、图像等等）、整理讯息（例如加入CSS等），以及计算网页的显示方式，然后会输出至显示器或打印机。浏览器内核的不同对于网页的语法解释会有不同，所以渲染的效果也不相同。所有网页浏览器、电子邮件客户端以及其它需要编辑、显示网络内容的应用程序都需要内核。
JS引擎则：解析和执行javascript来实现网页的动态效果。
最开始渲染引擎和JS引擎并没有区分的很明确，后来JS引擎越来越独立，内核就倾向于只指渲染引擎。
•	浏览器如何渲染网页的？
在DOM树构建的同时，浏览器会构建渲染树（render tree）。渲染树的节点（渲染器），在Gecko中称为frame，而在webkit中称为renderer。渲染器是在文档解析和创建DOM节点后创建的，会计算DOM节点的样式信息。
其实浏览器加载显示html的顺序是按下面的顺序进行的：
1.	IE下载的顺序是从上到下，渲染的顺序也是从上到下，下载和渲染是同时进行的。
2.	在渲染到页面的某一部分时，其上面的所有部分都已经下载完成（并不是说所有相关联的元素都已经下载完）。
3.	如果遇到语义解释性的标签嵌入文件（JS脚本，CSS下载过程会启用单独连接进行下载。
4.	并且在下载后进行解析，解析过程中，停止页面所有往下元素的下载。
5.	样式表在下载完成后，将和以前下载的所有样式表一起进行解析，解析完成后，将对此前所有元素（含以前已经渲染的）重新进行渲染。
6.	JS、CSS中如有重定义，后定义函数将覆盖前定义函数。
Firefox处理下载和渲染顺序大体相同，只是在细微之处有些差别，例如：iframe的渲染
如果你的网页比较大，希望部分内容先显示出来，粘住浏览者，那么你可以按照上面的规则合理的布局你的网页，达到预期的目的。
JS的加载
不能并行下载和解析（阻塞下载）
当引用了JS的时候，浏览器发送1个jsrequest就会一直等待该request的返回。因为浏览器需要1个稳定的DOM树结构，而JS中很有可能有代码直接改变了DOM树结构，比如使用 document.write 或 appendChild,甚至是直接使用的location.href进行跳转，浏览器为了防止出现JS修改DOM树，需要重新构建DOM树的情况，所以就会阻塞其他的下载和呈现.
http://www.html5rocks.com/zh/tutorials/internals/howbrowserswork/#Themainflow
什么是渐进式渲染？
•	尽快渲染展示内容的技术
•	比如 lazy loading of images,当图片要展示的时候js再加载它而不是在页面加载的时候就把全部图片加载完
•	比如 prioritizing visible content，仅包括页面需要的最少的必要css/内容/脚本 让页面尽快在浏览器渲染展示出来，然后利用 defer的js来加载其他资源和内容


