# CSS基础知识



## CSS选择器
### 有哪些？ 
1. 类选择器 (.className)
2. ID选择器 #id
3. 通配符选择器（ * ）
4. 标签选择器（div, h1, p）
5. 属性选择器（a[rel = "external"]） 
  
  除了等号还可以有 ~=（完整包含）、^=(开头）、$=（结尾）、```*=```（ 包含）、|=（连字符衔接的开头）
6. 组合选择器
 
 包括相邻选择器（h1 + p）、子选择器（ul > li）、后代选择器（li a）、同级且在之后的选择器（.a ~ .b) 
7. 伪元素选择器(::fist-line,::first-letter,::after,::before)
8. 伪类选择器

  8.1 结构型伪类选择器(:root,:first-child,:last-chilid,:nth-child(n),:nth-last-child(n),:only-child,:empty...)

  以上child都可以换成of-type。两者的区别是：child是在父元素的所有子元素（包括不同类型）中定位，如果这个元素符合前面的选择器就选中；而of-type是在父元素所有符合前面选择器（都是同类型）的子元素中定位。

 8.2 链接伪类选择符（:link,:visited)
 8.3 用户行为伪类选择符（:hover,:active,:focus)
 8.4 目标伪类选择符（:target 当一个元素被指向URI目标时）
 8.5 元素状态伪类选择符（:enabled,:disabled,:checked）		
 8.6 逻辑性伪类选择符(:not(s))

### 优先级计算	

行内样式1000 -- id100 -- 类、伪类、属性选择器10 -- 类型选择器、伪元素选择器1  

通过相加计算大的优先级高，值相等的话后声明的优先级高。如果权重相同，则最后定义的样式会起作用，但是应该避免这种情况出现

### 优化方式
浏览器从右到左解析css选择符，并且越具体的选择符查找效率越高（比如id显然高于标签选择符）。

优化CSS选择器效率，可以从以下几个方面：
1. 避免普遍规则
2. 不要在ID选择器或类名选择器前加标签名或类名
3. 尽可能使用具体的类别
4. 避免使用后代选择器
5. 标签分类规则中不要包含一个子选择器
6. 借助相关继承关系

参考 https://developer.mozilla.org/en-US/docs/Web/Guide/CSS/Writing_efficient_CSS


## CSS属性
### CSS1,2常见属性
1. 背景属性  background(-attachment,-color,-image,-position,-repeat)
  
  background-attachment设置背景是否随文档滚动，默认为scroll，可以设置为fixed（相对于可视区域固定）。
2. 边框属性
  
  border
  
  - 表示位置的 -bottom,-left,-top,-right
  - 其他 -color,-style,-width(可以与位置组合，位置放前面)
  
  outline（-color,-style,-width）
  
3. 文本属性 

        color 设置文本颜色
        direction 设置文本方向。
        line-height 设置行高。
        letter-spacing 设置字符间距。
        text-align 对齐元素中的文本。
        text-decoration 向文本添加修饰。
        text-indent 缩进元素中文本的首行。
        text-shadow 设置文本阴影。
        text-transform 控制元素中的字母。
        unicode-bidi 设置文本方向。
        white-space 设置元素中空白的处理方式。
        word-spacing 设置字间距。

4. 字体属性
   font(-family,-size,-style,-weight,-variant)
5. 列表属性（list-style,list-stle-image,list-position,list-style-tpe)
6. 表格属性（border-collapse,border-spacing,caption-side,empty-cells,table-layout)

还有与盒模型、定位相关的属性在下面介绍。

### 可继承的属性
- 文本相关的color，font-family, font-size, font-style,font-variant, font-weight, font, letter-spacing,line-height, text-align, text-indent, texttransform,word-spacing
- 列表相关的list-style-image, list-style-position,list-style-type, list-style
- 其他 color、visibility等
- 不可继承的样式：border padding margin width height（盒模型）
### 书写顺序
1. 位置属性(position, top, right, z-index, display, float等)
2. 大小(width, height, padding, margin)
3. 文字系列(font, line-height, letter-spacing, color- text-align等)
4. 背景(background, border等)
5. 其他(animation, transition等)



## 盒模型
### 是什么？
盒模型包括： 内容(content)、填充(padding)、边框(border)、边界(margin)。 

有两种：IE 盒子模型和标准 W3C 盒子模型。区别是元素width、height属性的计算方式不同，W3C盒模型元素宽高只对内容部分计算，而IE是对content+左右padding+左右border计算。

### CSS3中的新属性 box-sizing
有以下三种值：content-box（默认）, padding-box和border-box。

含义是元素width、height属性的计算方式，content-box是只包括内容部分，padding-box是content+左右padding，border-box是content+左右padding+左右border。

### margin
#### margin的参考线

在margin属性中一共有两类参考线，top和left的参考线属于一类，right和bottom的参考线属于另一类。top和left是以外元素为参考，right和bottom是以元素本身为参考。margin的位移方向是指margin数值为正值时候的情形，如果是负值则位移方向相反。

也就是说，top和left是该元素相对于与它相邻的元素移动，而right和bottom则是与该元素相邻的元素相对于该元素移动。

#### margin叠加
是什么：普通文档流中块级框垂直边距相遇时，外边距高度等于两个发生叠加的外边距高度中的较大者。行内框、 浮动框或绝对定位框之间的外边距不会叠加。

一般来说， 垂直外边距叠加有三种情况：
1. 元素自身叠加 当元素没有内容（即空元素）、内边距、边框时， 它的上下边距就相遇了， 即会产生叠加（垂直方向）。 当为元素添加内容、 内边距、 边框任何一项， 就会取消叠加。
2. 相邻元素叠加 相邻的两个元素， 如果它们的上下边距相遇，即会产生叠加。
3.  包含（父子）元素叠加 包含元素的外边距隔着父元素的内边距和边框， 当这两项都不存在的时候， 父子元素垂直外边距相邻， 产生叠加。 添加任何一项即会取消叠加。


## 定位方式

### position属性
普通流（文档流）指元素按照其在 HTML 中的位置顺序决定排布的过程。
- 默认static，没有定位，元素出现在普通流中。属性top、bottom、left、right在position为static的情况下无效。其用法为：在改变了元素的position属性后可以将元素重置为static让其回归到页面默认的普通流中。
- 相对定位 position:relative。普通流定位模型一部分。相对于其在普通流中的位置进行定位。原来位置还是会被占据，只是它不再显示在那里。会导致覆盖其他框。position: relative不会改变行内元素的display属性。
- 绝对定位 position:absolute。使元素脱离普通流，不占据空间。位置相对于最近的已定位祖先元素，没有祖先元素时相对于最初包含块。应用了position: absolute的元素会改变display属性。width会变成auto（与内容块宽度相同，会受到父元素的宽度影响）。如果没有设置top、bottom、left、right属性的话，浏览器会默认设置成auto，而auto的值则是该元素的“默认位置”。即设置position: absolute前后的offsetTop和offsetLeft属性值不变。Firefox的话会直接将top、left设置成offsetTop和offsetLeft的值而非auto。IE7下的表现更类似于float，会附加到父元素的末尾。
- 固定定位 fixed。绝对定位的子类别。差异在于固定元素的包含块是视口。

一些特性：
-  应用了position: relative/absolute的元素，margin属性仍然有效。如果设置了left、top、bottom、right的属性，建议大家不要设置margin数据，因为很难精确元素的定位，尽量减少干扰因素。
-  position: absolute忽略根元素的padding。
-  在IE6/7中设置position属性后会导致z-index属性失效
-  行内元素在应用了position：absolute之后会改变display属性，变为block
-  应用了position: absolute / relative之后，会覆盖其他非定位元素（即position为static的元素），如果你不想覆盖到其他元素，也可以将z-index设置成-1。

### float
浮动 float:left(right)浮动框左右移动直到外边缘碰到**包含框或另一个浮动框的边缘**。浮动框不在普通流中。行框围绕浮动框。创建浮动框可以使文本围绕图像。对行框应用`clear:(left\right\both\none)`,表示框的哪些边不应该挨着浮动框。会将元素的display属性变更为block。

浮动特性：
- 父元素的高度无法被撑开，影响与父元素同级的元素
- 与浮动元素同级的非浮动元素（内联元素）会跟随其后
- 浮动元素的前一个元素不会受到任何影响

float高度塌陷解决方案：
- 添加空div（clear:both;）清理浮动
- 	after伪元素	   

      .floatfix:after{
            clear:both;content:".";
            height:0;display:block;
            visibility:hidden;}
       或者
      .floatfix:after{ content:""; display:table; clear:both; }
- 使父容器形成BFC,比如父容器也float，父元素设置overflow：auto；zoom：1

### float和position
1.同时应用
- position:relative和float：元素同时应用了position: relative、float、（top / left / bottom / right）属性后，则元素先浮动到相应的位置，然后再根据（top / left / bottom / right）所设置的距离来发生偏移。
- position:absolute和float：元素同时应用了position: absolute及float属性，则float失效。
  
2.覆盖问题
- 两个位置相同的元素同级元素，设置postion:absolute的元素会覆盖设置float的元素
- 如果没有把float的元素的position设置成relative的话，你想通过设置float元素的z-index来的达到覆盖position:absolute是无效的。
 
3.清浮动问题
- 同时应用position: absolute和float: left会导致清除浮动无效（position: relative则可以清除浮动）。

4.position:absolute和float属性的异同
- 共同点：对内联元素设置float和absolute属性，可以让元素脱离文档流，并且可以设置其宽高。
- 不同点：float仍会占据位置，absolute会覆盖文档流中的其他元素。

### 层叠上下文和z-index
层叠上下文：层叠上下文是HTML元素的三维概念，这些HTML元素在一条假想的相对于面向（电脑屏幕的）视窗或者网页的用户的z轴上延伸，HTML元素依据其自身属性按照优先级顺序占用层叠上下文的空间。

层叠水平：决定了同一个层叠上下文中元素在z轴上的显示顺序。层叠水平的比较只有在当前层叠上下文元素中才有意义。

层叠顺序：元素发生层叠时候有着特定的垂直显示顺序。

原则：
- 谁大谁上：当具有明显的层叠水平标示的时候，如识别的z-indx值，在同一个层叠上下文领域，层叠水平值大的那一个覆盖小的那一个。通俗讲就是官大的压死官小的。
- 后来居上：当元素的层叠水平一致、层叠顺序相同的时候，在DOM流中处于后面的元素会覆盖前面的元素。

z-index可以设置成三个值：
- auto，默认值。当设置为auto的时候，当前元素的层叠级数是0，同时这个盒不会创建新的层级上下文（除非是根元素，即<html>）；
- <integer>。指示层叠级数，可以使负值，同时无论是什么值，都会创建一个新的层叠上下文；
- inherit。父元素继承

z-index属性目前只有在position:relative、position:absolute和position:fixed参与的情况下才有作用，表示层级，类似photoshop中层级的概念。


先说一下如果创建层叠上下文，css创建层叠上下文的方法有很多，但是常用的也就够那么几种

	1. 定位元素中z-index不等于auto的会为该元素创建层叠上下文
	2. html根元素默认会创建层叠上下文（这是一个特例，知道就行）
	3. 元素的opacity不等于1会创建层叠上下文

元素的transform不等于none会创建层叠上下文

	1. z-index仅在定位元素（position不等于static）中有效
	2. 七阶层叠水平图
	3. z-index层叠水平的比较仅限于父级层叠上下文中

其次需要注意以下几点：
　　
	1. 在开发中尽量避免层叠上下文的多层嵌套，因为层叠上下文嵌套过多的话容易产生混乱，如果对层叠上下文理解不够的话是不好把控的。　　
	2. 非浮层元素（对话框等）尽量不要用z-index（通过层叠顺序或者dom顺序或者通过层叠上下文进行处理）　
	3. z-index设置数值时尽量用个位数
![](http://mmbiz.qpic.cn/mmbiz/zPh0erYjkib0TXMuJRGH7TPOQvyawxuLGGSRb5ujzXtCfTjx6VNXZIN5x9Q92gbWo2hWZwB7PvDvVT3HRML7icDg/640?wx_fmt=png&tp=webp&wxfrom=5&wx_lazy=1)
参考 [深入理解CSS中的层叠上下文和层叠顺序](http://www.zhangxinxu.com/wordpress/2016/01/understand-css-stacking-context-order-z-index/)
[不起眼的 z-index 却能牵扯出这么大的学问](http://mp.weixin.qq.com/s?__biz=MzAxODE2MjM1MA==&mid=2651550819&idx=1&sn=7693f3c2a9d925bf069a08de90705682&scene=1&srcid=0508Uhp17Oga5IQzT9HDhUac#rd)

### BFC 规范
W3C CSS 2.1 规范中的一个概念,它决定了元素如何对其内容进行定位,以及与其他元素的关系和相互作用。

BFC，块级格式化上下文，一个创建了新的BFC的盒子是独立布局的，盒子里面的子元素的样式不会影响到外面的元素。在同一个BFC中的两个相邻的块级盒在垂直方向（和布局方向有关系）的margin会发生折叠。

在进行盒子元素布局的时候， BFC 提供了一个环境， 在这个环境中按照一定规则进行布局不会影响到其它环境中的布局。比如浮动元素会形成 BFC，浮动元素内部子元素的主要受该浮动元素影响，两个浮动元素之间是互不影响的。也就是说，如果一个元素符合了成为 BFC 的条件，该元素内部元素的布局和定位就和外部元素互不影响(除非内部的盒子建立了新的  BFC)， 是一个隔离了的独立容器。

规定满足下列CSS声明之一的元素便会生成BFC。
父元素

	float的值不为none
	overflow的值不为visible
	display的值为inline-block、table-cell、table-caption
	position的值为absolute或fixed


### 居中
见博文 [水平垂直居中总结](http://leafxm.com/2016/05/08/centerH/)

居中一个浮动元素：浮动元素宽高确定，设置postion:relative,并使用负margin法
	
		     .div {
		      width:500px ; height:300px;//高度可以不设
		      margin: -150px 0 0 -250px;
		      position:relative;相对定位
		      background-color:pink;//方便看效果
		      left:50%;
		      top:50%;
		    }

## display

- 块状元素和行内元素的区别？
	- width、height属性
	- 是否换行
	- width块状默认100%，行内（Inline）类型的元素则是根据自身的内容及子元素来决定宽度。
	- 块状元素：P、DIV、UL、LI、DD、DT...；行内元素：A、IMG、SPAN、STRONG...

- 列出display的值，说明他们的作用。
		
		- none	此元素不会被显示。
		- block	此元素将显示为块级元素，此元素前后会带有换行
		- inline	默认。此元素会被显示为内联元素，元素前后没有换行
		- inline-block	行内块元素。象行内元素一样显示，但其内容象块类型元素一样显示
		- list-item 象块类型元素一样显示，并添加样式列表标记。
		- table	此元素会作为块级表格来显示（类似 <table>），表格前后带有换行符。
		- inline-table	此元素会作为内联表格来显示
		- table-cell	此元素会作为一个表格单元格显示（类似 <td> 和<th>）
		- inherit 规定应该从父元素继承 display 属性的值。

- display:none和visibility:hidden的区别？
	- display:none  隐藏对应的元素，在文档布局中不再给它分配空间，它各边的元素会合拢，就当他从来不存在。
	- visibility:hidden  隐藏对应的元素，但是在文档布局中仍保留原来的空间。

- position跟display、margin collapse、overflow、float这些特性相互叠加后会怎么样？
	- position和float和display的关系： "position:absolute" 和 "position:fixed" 优先级最高，有它存在的时候，浮动不起作用，'display' 的值也需要调整； 其次，元素的 'float' 特性的值不是 "none" 的时候或者它是根元素（body）的时候，调整 'display' 的值； 最后，非根元素，并且非浮动元素，并且非绝对定位的元素，'display' 特性值同设置值。（display大概的转换规则：inline-table转为table，其他常见的转为block,list-item保持）

这从另一个侧面说明了一个问题：浮动或绝对定位的元素，只能是块元素或表格。

[http://www.cnblogs.com/jackyWHJ/p/3756087.html](http://www.cnblogs.com/jackyWHJ/p/3756087.html)

- inline-block空隙怎么解决
	- 不换行，或前一个闭合和后一个开始连在一起
	- 不闭合标签
	- 父元素font-size:0
	- letter-spacing 父元素-3px 子元素0
	- word-spacing 父元素 -6px 子元素0
	- 负margin -3px



    
 






   

