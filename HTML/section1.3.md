# 面试题目

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

title:  前端面试题目HTML部分总结

## 标签
- 行内元素有哪些？块级元素有哪些？ 空(void)元素有那些？

	- CSS规范规定，每个元素都有默认的display值，如div的display默认值为“block”，则为“块级”元素；span默认display属性值为“inline”，是“行内”元素。

	- （1）行内元素有：`a span img input select strong`
	- （2）块级元素有：`div ul ol li dl dt dd h1-h6 p`
	- （3）常见的空元素：`<br> <hr> <img> <input> <link> <meta>`
	- 全部块级元素：    
    
			<div>文档分区。<p>行。<h1>-<h6>标题级别 1-6.
			<dd>定义列表中定义条目描述。<dl>定义列表。
			<ol>有序列表。<ul>无序列表。
			<table>表格<form>表单。	
			<address>联系方式信息。<blockquote>块引用。
			<fieldset>表单元素分组。
			<hr>水平分割线。
			<noscript>不支持脚本或禁用脚本时显示的内容。
			<pre>预格式化文本。
			<tfoot>表脚注。
			HTML5：虽然”块级“在新的 HTML5 元素中没有明确定义
			<article> 文章内容。<aside> 伴随内容。		
			<audio> 音频播放。<video> 视频。
			<canvas> 绘制图形。
			<figcaption> 图文信息组标题
			<figure> 图文信息组 (参照 <figcaption>)。
			<footer> 区段尾或页尾。<header> 区段头或页头	
			<hgroup> 标题组。
			<output> 表单输出。
			<section> 一个页面区段。


- `<strong>`，`<em>`和`<b>`，`<i>`标签

		从表现形式上来看，<em> 和<i>都是表现为斜体，<strong>和<b>都是表现为加粗。
		从意义上来看，<b> <i>是视觉要素，分别表示无意义的加粗，无意义的斜体。
		 <em> 和 <strong> 是表达要素(phrase elements)。
		<em> （emphasized text）表示一般的强调文本，
		而 < strong > （strong emphasized text）表示比 < em > 语义更强的的强调文本。

- label的作用是什么？是怎么用的？

label标签来定义表单控件间的关系,当用户选择该标签时，浏览器会自动将焦点转到和标签相关的表单控件上。

	<label for="Name">Number:</label>
	<input type=“text“name="Name" id="Name"/>
	<label>Date:<input type="text" name="B"/></label>

- iframe有那些缺点？
	- 是什么：iframe 元素会创建包含另外一个文档的内联框架（即行内框架）
  	- iframe会阻塞主页面的Onload事件；
   - iframe和主页面共享连接池，而浏览器对相同域的连接有限制，所以会影响页面的并行加载。
   -	使用iframe之前需要考虑这两个缺点。如果需要使用iframe，最好是通过javascript动态给iframe添加src属性值，这样可以绕开以上两个问题。


## 兼容
- 常见兼容性问题？

	- png24位的图片在iE6浏览器上出现背景，解决方案是做成PNG8.
	- 浏览器默认的margin和padding不同。解决方案是加一个全局的*{margin:0;padding:0;}来统一。
	- 浮动ie产生的双倍距离 `#box{ float:left; width:100px; margin:0 0 0 10px;}`这种情况之下IE会产生20px的距离，解决方案是在float的标签样式控制中加入 `_display:inline;`将其转化为行内属性。(_这个符号只有ie6会识别)
	- 解决ie的兼容性问题，可以使用渐进识别的方式，从总体中逐渐排除局部。首先，巧妙的使用“\9”这一标记，将IE游览器从所有情况中分离出来。接着，再次使用“+”将IE8和IE7、IE6分离开来，这样IE8已经独立识别。
	
			  .bb{
			   background-color:#f1ee18;/*所有识别*/
			  .background-color:#00deff\9; /*IE6、7、8识别*/
			  +background-color:#a200ff;/*IE6、7识别*/
			  _background-color:#1e0bd1;/*IE6识别*/
			  }

	- IE下,可以使用获取常规属性的方法来获取自定义属性,也可以使用getAttribute()获取自定义属性;Firefox下,只能使用getAttribute()获取自定义属性.解决方法:统一通过getAttribute()获取自定义属性.
	- IE下,event对象有x,y属性,但是没有pageX,pageY属性;Firefox下,event对象有pageX,pageY属性,但是没有x,y属性.解决方法：（条件注释）缺点是在IE浏览器下可能会增加额外的HTTP请求数。
	- Chrome 中文界面下默认会将小于 12px 的文本强制按照 12px 显示,可通过加入 CSS 属性 -webkit-text-size-adjust: none; 解决.
	- 超链接访问过后hover样式就不出现了 被点击访问过的超链接样式不在具有hover和active了.解决方法是改变CSS属性的排列顺序:L-V-H-A : a:link {} a:visited {} a:hover {} a:active {}

##HTML5
- HTML5 为什么只需要写 <!DOCTYPE HTML>？

 - HTML5 不基于 SGML，因此不需要对DTD(Document Type Definition，文档类型定义)进行引用，但是需要doctype来规范浏览器的行为（让浏览器按照它们应该的方式来运行）；而HTML4.01基于SGML,所以需要对DTD进行引用，才能告知浏览器文档所使用的文档类型。

- html5有哪些新特性、移除了那些元素？如何处理HTML5新标签的浏览器兼容问题？如何区分 HTML 和HTML5？

	- HTML5 现在已经不是 SGML 的子集，主要是关于图像，位置，存储，多任务等功能的增加。新特性有：
		
			html5新增标签：article、section、aside、header、hgroup、footer、source、figure

			绘画 canvas ；用于媒介回放的 video 和 audio 元素
			本地离线存储 localStorage 长期存储数据，浏览器关闭后数据不丢失
			sessionStorage 的数据在浏览器关闭后自动删除
			语意化更好的内容元素，比如 article、footer、header、nav、section
			表单控件，email，url，number，range，search，color，meter，progress，
			calendar、date、time、email、url、search
			新的技术webworker, websocket, Geolocation
			拖放：draggable=”true”
			画布：canvas标签（与SVG矢量伸缩图形的区别）		
			地理定位：navigation.geolocation
			web存储：localStorage，sessionStorage
			应用缓存： Application Cache Manifest

Web Worker：当在 HTML 页面中执行脚本时，页面的状态是不可响应的，直到脚本已完成。web worker 是运行在后台的 JavaScript，独立于其他脚本，不会影响页面的性能。您可以继续做任何愿意做的事情：点击、选取内容等等，而此时 web worker 在后台运行。
			
websocket服务器发送事件：Server-Sent 事件–单向消息传递。Server-Sent 事件指的是网页自动获取来自服务器的更新。
			
表单：(1.Input类型：email、url、number、range、Date pickers、search、color)—>(2.表单元素：datalist、keygen、output)—>(3.表单属性：autocomplete、autofocus、form、min, max 和 step、multiple、pattern、placeholder、required)
			
	- 移除的元素
		
			纯表现的元素：basefont，big，center，font, s，strike，tt，u；
			对可用性产生负面影响的元素：frame，frameset，noframes；

	- 兼容性问题：

			IE8/IE7/IE6支持通过document.createElement方法产生的标签，
			可以利用这一特性让这些浏览器支持HTML5新标签，浏览器支持新标签后，
			还需要添加标签默认的样式；
			当然最好的方式是直接使用成熟的框架、使用最多的是html5shim框架
			<!--[if lt IE 9]>
			<script> src="http://html5shim.googlecode.com/
			svn/trunk/html5.js"</script>
			<![endif]-->



- HTML5的离线储存？

	- localStorage    长期存储数据，浏览器关闭后数据不丢失；
	- sessionStorage  数据在浏览器关闭后自动删除。

在用户没有与因特网连接时，可以正常访问站点或应用，在用户与因特网连接时，更新用户机器上的缓存文件。
原理：HTML5的离线存储是基于一个新建的.appcache文件的缓存机制(不是存储技术)，通过这个文件上的解析清单离线存储资源，这些资源就会像cookie一样被存储了下来。之后当网络在处于离线状态下时，浏览器会通过被离线存储的数据进行页面展示。

如何使用：

1. 页面头部像下面一样加入一个manifest的属性；
2. 在cache.manifest文件的编写离线存储的资源；
	  
		CACHE MANIFEST
	    #v0.11
	    CACHE:
	    js/app.js
	    css/style.css
	    NETWORK:
	    resourse/logo.png
	    FALLBACK:
	    / /offline.html
3. 在离线状态时，操作window.applicationCache进行需求实现。


- 浏览器是怎么对HTML5的离线储存资源进行管理和加载的呢？

在线的情况下，浏览器发现html头部有manifest属性，它会请求manifest文件，如果是第一次访问app，那么浏览器就会根据manifest文件的内容下载相应的资源并且进行离线存储。如果已经访问过app并且资源已经离线存储了，那么浏览器就会使用离线的资源加载页面，然后浏览器会对比新的manifest文件与旧的manifest文件，如果文件没有发生改变，就不做任何操作，如果文件改变了，那么就会重新下载文件中的资源并进行离线存储。离线的情况下，浏览器就直接使用离线存储的资源。

- HTML5的form如何关闭自动完成功能？
   
	- 给不想要提示的 form 或下某个input 设置为 autocomplete=off。


## 其他
- Doctype作用？标准模式与兼容模式各有什么区别?
	- （1）、<!DOCTYPE>声明位于HTML文档中的第一行，处于 <html> 标签之前。告知浏览器的解析器用什么文档标准解析这个文档。DOCTYPE不存在或格式不正确会导致文档以兼容模式呈现。
	- （2）、标准模式的排版 和JS运作模式都是以该浏览器支持的最高标准运行。在兼容模式中，页面以宽松的向后兼容的方式显示,模拟老式浏览器的行为以防止站点无法工作。

- 你知道多少种Doctype文档类型？
	- 该标签可声明三种 DTD 类型，分别表示严格版本、过渡版本以及基于框架的 HTML 文档。
	- HTML 4.01 规定了三种文档类型：Strict、Transitional 以及 Frameset。都包含所有 HTML 元素和属性，差别为不包括展示性的和弃用的元素（比如 font），不允许框架集；包含前面的但不允许框架集；允许框架集。
	-  XHTML 1.0 规定了三种 XML 文档类型：Strict、Transitional 以及 Frameset。同上，但是必须以格式正确的 XML 来编写标记。
	-  Standards （标准）模式（也就是严格呈现模式）用于呈现遵循最新标准的网页，而 Quirks（包容）模式（也就是松散呈现模式或者兼容模式）用于呈现为传统浏览器而设计的网页。

- HTML与XHTML——二者有什么区别
	- 1.所有的标记都必须要有一个相应的结束标记
	- 2.所有标签的元素和属性的名字都必须使用小写
	- 3.所有的XML标记都必须合理嵌套
	- 4.所有的属性必须用引号""括起来
	- 5.把所有<和&特殊符号用编码表示
	- 6.给所有属性赋一个值
	- 7.不要在注释内容中使“--”
	- 8.图片必须有说明文字

- content="application/xhtml+xml;"是什么意思？

wap2.0网站，使用的是xhtml mp语言。xhtml mp是xhtml的子集。

在xhml mp中，支持三种MIME类型

1. application/vnd.wap.xhtml+xml
2. application/xhtml+xml
3. text/html

第一种类型是一些非智能手机的wap浏览器所需要的，以便正确显示XHTML MP文档。

第二种是XHTML系列文档的类型

第三种是HTML文档的类型。这样用IE6就可以正常浏览这些文档，而如果遇到上面的两种类型就会弹出一个对话框。

目前，为了兼容最低标准，很多网站使用的还是application/vnd.wap.xhtml+xml的mime类型。

- 如何实现网页的多语言版本？
	- 静态：不同页面用不同语言展示
	- 动态：对于动态页面文件（PHP，ASP等），可以使用语言变量

- ` <script>, <script async> and <script defer>`.
	-  没有async或者defer，浏览器会在渲染这个脚本标签下的元素之前立即加载执行脚本，会阻塞页面渲染
	-  加async，浏览器会在加载脚本的同时继续加载、渲染HTML页面，下载完成后暂停HTML解析立即执行脚本，所以有可能出现脚本执行顺序被打乱的情况
	-  加defer，在下载脚本时HTML仍然在解析，HTML解析完成之后再按照原本的顺序执行脚本。onload事件触发前被调用。但是不是所有浏览器都支持。
	

- 语义化的理解？
	- 1，去掉或者丢失样式的时候能够让页面呈现出清晰的结构
	- 2，有利于SEO：和搜索引擎建立良好沟通，有助于爬虫抓取更多的有效信息：爬虫依赖于标签来确定上下文和各个关键字的权重；
	- 3，方便其他设备解析（如屏幕阅读器、盲人阅读器、移动设备）以意义的方式来渲染网页；
	- 4，使阅读源代码的人对网站更容易将网站分块，便于阅读维护理解。

- 写/描述一段语义的html代码吧。
   HTML5中新增加的很多标签（如：`<article>、<nav>、<header>和<footer>`等）就是基于语义化设计原则
 
- 什么是 FOUC（无样式内容闪烁）？你如何来避免 FOUC？

   FOUC - Flash Of Unstyled Content 文档样式闪烁

	   <style type="text/css" media="all">@import "../fouc.css";</style>

   而引用CSS文件的@import就是造成这个问题的罪魁祸首。IE会先加载整个HTML文档的DOM，然后再去导入外部的CSS文件，因此，在页面DOM加载完成到CSS导入完成中间会有一段时间页面上的内容是没有样式的，这段时间的长短跟网速，电脑速度都有关系。

   解决方法简单的出奇，只要在`<head>`之间加入一个`<link>`或者`<script>`元素就可以了。


	
## 实现
- 如何在页面上实现一个圆形的可点击区域？
	- 1、map+area或者svg
	- 2、border-radius
	- 3、纯js实现 需要求一个点在不在圆上简单算法、获取鼠标坐标等等

- 实现不使用 border 画出1px高的线，在不同浏览器的标准模式与怪异模式下都能保持一致的效果。

		<div style="height:1px;overflow:hidden;background:#ccc"></div>

