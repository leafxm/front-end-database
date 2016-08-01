# 面试题目

## **基本概念**

* 介绍js的基本数据类型。哪些是引用类型？

  * number,string,boolean,null,undefined
  * 对象、数组和函数是引用类型；字符串是特例，不能改写内容，使用引用方式存储，行为接近值方式

* JavaScript有几种类型的值？，你能画一下他们的内存图吗？


栈：原始数据类型（Undefined，Null，Boolean，Number、String） 堆：引用数据类型（对象、数组和函数）

两种类型的区别是：存储位置不同；

原始数据类型直接存储在栈\(stack\)中的简单数据段，占据空间小、大小固定，属于被频繁使用数据，所以放入栈中存储；

引用数据类型存储在堆\(heap\)中的对象,占据空间大、大小不固定,如果存储在栈中，将会影响程序运行的性能；引用数据类型在栈中存储了指针，该指针指向堆中该实体的起始地址。当解释器寻找引用值时，会首先检索其在栈中的地址，取得地址后从堆中获得实体

* null，undefined 的区别？

  * 当声明的变量还未被初始化时，变量的默认值为undefined，而null表示一个空对象指针
  * null表示空值，typeof\(null\)结果是object，但null本身不是对象；undefined表示无值，typeof\(undefined\)结果是undefined
  * null转为数值时为0；undefined转为数值时为NaN。
  * undefined表示"缺少值"，就是此处应该有一个值，但是还没有给出。典型用法是：（1）变量被声明了，但没有赋值时，就等于undefined。（2\) 调用函数时，应该提供的参数没有提供，该参数等于undefined。（3）对象没有赋值的属性，该属性的值为undefined。（4）函数没有返回值时，默认返回undefined。null表示空对象指针，即该处不应该有值。典型用法是：（1） 作为函数的参数，表示该函数的参数不是对象。（2） 作为对象原型链的终点。
  * 运算符==将它们视为相等，必须区分可用===或typeof

* 怎么判断是不是数组

  * 答：a instanceof Array
  * Array.isArray\(a\)
  * 试一下Array的内置，可以使用是Array不可以则不是
  * 其实还有 Object.prototype.toString.call\(\[1,2,3\]\) === '\[object Array\]'

* 怎么把一个类数组对象转化为数组

  * 答：Array.prototype.slice.call\(\)；

* JavaScript的数据对象有 属性配置的值。

  * writable：这个属性的值是否可以改。
  * configurable：这个属性的配置是否可以删除，修改。
  * enumerable：这个属性是否能在for…in循环中遍历出来或在Object.keys中列举出来。
  * value：属性值。


## **函数**

* attribute和property的区别是什么？

  * attribute是dom元素在文档中作为html标签拥有的属性，是一个特性节点，每个DOM元素都有一个对应的attributes属性来存放所有的attribute节点，attributes是一个类数组的容器，（如class、value）
  * property就是dom元素在js中作为对象拥有的属性，就是一个以名值对\(name=”value”\)的形式存放在Object中的属性，如div.id （div表示一个DOM节点）
  * 所以：对于html的标准属性来说，attribute和property是同步的，是会自动更新的，但是对于自定义的属性来说，他们是不同步的

* 说说你对作用域链的理解

  * 作用域链的作用是保证执行环境里有权访问的变量和函数是有序的，作用域链的变量只能向上访问，变量访问到window对象即被终止，作用域链向下访问变量是不被允许的。
  * 全局函数无法查看局部函数的内部细节，但局部函数可以查看其上层的函数细节，直至全局细节。当需要从局部函数查找某一属性或方法时，如果当前作用域没有找到，就会上溯到上层作用域查找，直至全局函数，这种组织形式就是作用域链。

* eval是做什么的？

  * 它的功能是把对应的字符串解析成JS代码并运行；应该避免使用eval，不安全（引起XSS攻击），非常耗性能（2次，一次解析成js语句，一次执行）。

* 说说你对闭包的理解？

  * 产生和形式：函数可以访问其定义时的作用域的变量（？），当函数B定义在函数A内，它的作用域链就包含了函数A的作用域，这样当函数B被在函数A外部引用（通过return或者定义为this.fun函数A被call到别的对象上？）时，函数A的作用域也被保存了下来。
  * 特性：可以读取函数内部的变量，另一个就是让这些变量的值始终保持在内存中。

* 闭包的应用

  * 实现私有成员
  * 保护命名空间
  * 避免污染全局变量
  * 变量需要长期驻留在内存

* function\(\){}\(\)为什么会出错？function g\(\){ }\(\)呢？如何修改为IIFE呢？

  * 前者期望是立即调用一个匿名函数表达式，结果是进行了函数声明，函数声明必须要有标识符做为函数名称。后者期望是立即调用一个具名函数表达式，结果是声明了函数 g。末尾的括号作为分组运算符，必须要提供表达式做为参数。无论在全局环境或者局部环境里遇到了这样的function关键字，默认的，它会将它当作是一个函数声明，而不是函数表达式。表达式语句不得以 function 或者 { 开头。
  * （）、！、+、-、=等运算符，都将函数声明转换成函数表达式，消除了javascript引擎识别函数表达式和函数声明的歧义，告诉javascript引擎这是一个函数表达式，不是函数声明，可以在后面加括号，并立即执行函数的代码。

* IIFE的作用？

  * 模仿一个私有作用域，用匿名函数作为一个“容器”，“容器”内部可以访问外部的变量，而外部环境不能访问“容器”内部的变量，所以\( function\(\){…} \)\(\)内部定义的变量不会和外部的变量发生冲突，俗称“匿名包裹器”或“命名空间”。

* 匿名函数的典型用例

  * addEventListener

* 模仿块级作用域

  \(function\(\){ \/\/这里是块级作用域 }\)\(\);

* \["1", "2", "3"\].map\(parseInt\) 答案是多少？

  * \[1, NaN, NaN\] 因为 parseInt 需要两个参数 \(val, radix\)，其中 radix 表示解析时用的基数。map 传了 3 个 \(element, index, array\)，对应的 radix 不合法导致解析失败。


## **面向对象**

* 介绍js有哪些内置对象？

Object 是 JavaScript 中所有对象的父对象

数据封装类对象：Object、Array、Boolean、Number 和 String 其他对象：Function、Arguments、Math、Date、RegExp、Error


* 什么是window对象? 什么是document对象?

  * Window 对象表示浏览器中打开的窗口。如果文档包含框架（frame 或 iframe 标签），浏览器会为 HTML 文档创建一个 window 对象，并为每个框架创建一个额外的 window 对象。
  * Document 对象：每个载入浏览器的 HTML 文档都会成为 Document 对象。Document 对象使我们可以从脚本中对 HTML 页面中的所有元素进行访问。提示：Document 对象是 Window 对象的一部分，可通过 window.document 属性对其进行访问。

* 谈谈This对象的理解。

  * this是js的一个关键字，随着函数使用场合不同，this的值会发生变化。但是有一个总原则，那就是this指的是调用函数的那个对象。
  * this一般情况下：是全局对象Global。 作为方法调用，那么this就是指这个对象

* 构造函数的运行机制

  * 所谓"构造函数"，其实就是一个普通函数，但是内部使用了this变量。对构造函数使用new运算符，就能生成实例，并且this变量会绑定在实例对象上。在JavaScript中，任何合法的函数都可以作为对象的构造函数，这既包括系统内置函数，也包括用户自己定义的函数。
  * 通常来说，构造函数没有返回值，它们只是初始化由this指针传递进来的对象，并且什么也不返回。如果一个函数有返回值，被返回的对象就成了new表达式的值。从形式上看，一个函数被作为构造函数还是普通函数执行的唯一区别，是否用new运算符。 **如果一个函数的返回值是引用类型（数组，对象或者函数）的数据，那么这个函数作为构造函数用new运算符执行构造时，运算的结果将被它的返回值取代，这时候，构造函数体内的this值丢失了，取而代之的是被返回的对象**。

* 在使用new操作符来调用一个构造函数的时候，发生了什么呢？其实很简单，就发生了四件事：

  ```
      var obj  ={};
      obj.__proto__ = CO.prototype;
      CO.call(obj);
      return obj;

  ```

  第一行，创建一个空对象obj。

  第二行，将这个空对象的\__proto\__成员指向了构造函数对象的prototype成员对象。

  第三行，将构造函数的作用域赋给新对象（因此this 就指向了这个新对象）

  第四行，返回新对象obj。

* call\(\)和apply\(\)和bind（）的区别

  * apply\(\)传递参数是用数组形式
  * bind（）不立即执行

* js实现继承方式及其优缺点

  * 借用构造函数（伪造对象，经典继承） `function Sub(){ Super.call(this); }`
  * 原型继承 `Child.prototype = new Parent();`
  * 组合式继承
  * 原型式继承
  * 寄生式继承
  * 寄生组合式继承

* 那为什么子类的原型为什么要指向父类的实例，为什么不直接等于向父类的原型？

  * 如果直接指向父类的原型，那么子类对象修改的时候父类的原型也会修改。所以指向实例，只修改一个父类的实例。

* JS 怎么实现一个类。怎么实例化这个类
  * 构造函数，new实例化，类的属性和方法，还可以定义在构造函数的prototype对象之上。
  * Object.create\(\)法。"类"就是一个对象，不是函数。直接用Object.create\(\)生成实例

* 如何判断一个对象是否属于某个类？

  * 使用instanceof


  * 看该对象的constructor属性
  * toString\(\)方法 Object.prototype.toString.apply\(o\);

* javascript对象的几种创建方式


1、对象字面量的方式

2、用工厂方式来创建 new Object\(\);再添加属性


3、构造函数\(可以无参、有参、加原型，以及有参原型混合）

* JavaScript原型? 有什么特点？

Javascript规定，每一个构造函数都有一个prototype属性，指向另一个对象。这个对象的所有属性和方法，都会被构造函数的实例继承。这意味着，我们可以把那些不变的属性和方法，直接定义在prototype对象上。这时所有实例指向prototype对象（同一个内存地址），因此就提高了运行效率。（我：主要是为了共用一个对象一段内存而提出）

当我们需要一个属性的时，Javascript引擎会先看当前对象中是否有这个属性， 如果没有的话，就会查找他的\_\_**proto\_\_**指针指向的Prototype对象是否有这个属性，如此递推下去，一直检索到 Object 内建对象。 特点： JavaScript对象是通过引用来传递的，我们创建的每个新对象实体中并没有一份属于自己的原型副本。当我们修改原型时，与之相关的对象也会继承这一改变。 函数的原型对象constructor默认指向函数本身，原型对象除了有原型属性外，为了实现继承，还有一个原型链指针proto，该指针指向上一层的原型对象，而上一层的原型对象的结构依然类似，这样利用proto一直指向Object的原型对象上，而Object的原型对象用Object.proto = null表示原型链的最顶端，如此便形成了javascript的原型链继承，同时也解释了为什么所有的javascript对象都具有Object的基本方法真正形成原型链的是每个对象的\_\_**proto\_\_**属性，而不是函数的prototype属性，这是很重要的。


* Array的sort方法工作原理是什么样的？
  * 如果调用该方法时没有使用参数，将按字母顺序对数组中的元素进行排序，说得更精确点，是按照字符编码的顺序进行排序。要实现这一点，首先应把数组的元素都转换成字符串（如有必要），以便进行比较。
  * 如果想按照其他标准进行排序，就需要提供比较函数，该函数要比较两个值，然后返回一个用于说明这两个值的相对顺序的数字。比较函数应该具有两个参数 a 和 b

* 那如果想要sort排序数字怎么办？

  * function\(a,b\){return b-a;}这样是降序

* String有哪些方法呀？

  * concat charAt slice substr substring 等等（其实现在觉得应该加一句说string是基本数据类型，没有方法，string的方法是String构造函数创建的引用类型的方法~）

* 那replace方法怎么用的呀？

  * 两个参数 1.RegExp对象或者是字符串2.字符串或者函数 然后替换可以用正则进行全局替换。。。。

* Javascript中，有一个函数，执行对象查找时，永远不会去查找原型，这个函数是？

  * hasOwnProperty
  * javaScript中hasOwnProperty函数方法是返回一个布尔值，指出一个对象是否具有指定名称的属性。此方法无法检查该对象的原型链中是否具有该属性；该属性必须是对象本身的一个成员。
  * 使用方法：object.hasOwnProperty\(proName\)

* 如何检查自定义全局变量？


 创建一个新的 iframe, 然后将其 `contentWindow` 中的属性值  与当前 window 中的属性值对比, 不在其中的就是自定义对象 

## **DOM 和事件**

* document.write\(\)的用法?和 innerHTML的区别?

document.write\(\)方法可以用在两个方面：页面载入过程中用实时脚本创建页面内容，以及用延时脚本创建本窗口或新窗口的内容。

document.write只能重绘整个页面。innerHTML可以重绘页面的一部分

* innerHTML，innerText和outerHTML，outerText的区别？

举个例子来说吧。

```
<div><span>内容</span></div>

```

使用这几个来获取上面div的内容的话，区别如下：

innerHTML:`"<span>内容</span>"`,带有html标签

innerText:"内容",不带html标签

outerHTML:"`<div><span>内容</span></div>`"

outerText:获取元素跟innterText是一样的。

* document.ready和onload的区别
  * JavaScript文档加载完成事件页面加载完成有两种事件，一是ready，表示文档结构已经加载完成（不包含图片等非文字媒体文件），二是onload，指示页 面包含图片等文件在内的所有元素都加载完成。\(可以说：ready 在onload 前加载！！！\)

* onmousemove和onmouseover的区别：

  * 时间上：onmousemove事件触发后，再触发onmouseover事件。
  * 按钮上：不区分鼠标按钮。
  * 动作上：onmouseover只在刚进入区域时触发，onmousemove除了刚进入区域触发外，在区域内移动鼠标，也会触发

* addEventListener最后一个参数是做什么用的？

  * 答：规定事件是冒泡还是捕获。false是冒泡，true是捕获

* 什么是冒泡，什么是捕获

  * 答：当一个元素触发了一个事件之后就会向上层传递直至body，document。捕获是从最不具体的传至最具体的

* 所有的事件都可以冒泡么

  * blur、focus、change、load和unload不能像其它事件一样冒泡。事实上blur和focus可以用事件捕获而非事件冒泡的方法获得（在IE之外的其它浏览器中）。

* stopPropagation, preventDefault 和 return false 的区别？

  * stopPropagation：阻止事件冒泡
  * preventDefault：阻止浏览器默认动作，如: 点击 a 链接节点的跳转动作, 表单提交动作
  * return false：退出执行, return false 之后的所有触发事件和动作都不会被执行. 有时候 return false 可以用来替代stopPropagation\(\) 和 preventDefault\(\)

* 事件是？IE与火狐的事件机制有什么区别？ 如何**阻止**事件冒泡

  * 我们在网页中的某个操作（有的操作对应多个事件）。例如：当我们点击一个按钮就会产生一个事件。是可以被 JavaScript 侦测到的行为。
  * 事件处理机制：IE是事件冒泡、火狐是事件捕获；
  * w3c的方法是e.stopPropagation\(\)，IE则是使用e.cancelBubble = true

* 事件代理与委托

  * 是什么：把事件处理器添加到一个祖先元素上，这样就避免了把事件处理器添加到多个子级元素上。在祖先节点上统一处理，减轻对event listener的管理负担
  * 实现的基础：事件冒泡，当一个元素上的事件被触发的时候，同样的事件将会在那个元素的所有祖先元素中被触发。任何一个事件的目标元素都是最开始的那个元素，并且它在我们的元素对象中以属性的形式出现。使用事件代理，我们可以把事件处理器添加到一个元素上，等待一个事件从它的子级元素里冒泡上来，并且可以得知这个事件是从哪个元素开始的。
  * 应用：table；lazing loading（需要动态添加子节点）；一组元素都绑定类似的event listener的时候，就可以考虑使用Event Delegation。
  * 优点：那些需要创建的以及驻留在内存中的事件处理器少了。这是很重要的一点，我们得到了性能上的提升，同时降低了崩溃的风险。在DOM更新后无须重新绑定事件处理器了。如果你的页面是动态生成的，比如说通过Ajax，你不需要再在元素被载入或者卸载的时候来添加或者删除事件处理器了。

    ```
    function editCell(e)    
    {
        e = e || window.event;
        var target =  e.target || e.srcElement;
        if(target.tagName.toLowerCase() =='td') 
           {
                // DO SOMETHING WITH THE CELL
          }
    }

    ```



## **实现**

* 鼠标滑过一个元素出现一个弹出层

  * 就dom 0级来举例子的话是 onmouseover dispaly:block

* 鼠标滑的快不让他出现怎么办

  * 设置一个setTimeout 当鼠标在上面停留的时间小于设定的时间的话他还没有出来事件就被取消掉了

* 现在我想要这个元素在页面下方是弹出层在上方显示，元素在上方时弹出层在下方显示？

  * 判断元素距离页面底端的位置，位置大于弹出层的高度的话就在下方弹出，否则在上方弹出

* 如果我现在想把他做成一个工具给别人用要怎么做？

  * 首先使用模块化，注意不要和其他的方法什么的有冲突，然后把里面设置方法出入所需的参数，比如哪个元素，什么事件，弹出层的大小等等

* 那想做一个好的工具参数肯定很多，你怎么能方便别人使用呢？毕竟参数这么多别人会记不住的

  * 我可能会设置成一个对象，传入对象的属性，这样就方便记住了。

* 如何平铺一张背景图？

  * js方法： 判断浏览器高度，设置图片的高度

* 如果让图片按比例放大缩小呢？

  * 用Js来判断宽高，然后按比例放大（面试官说屏幕壁板都是横屏，所以width设置为100%就可以了）

* 写一个通用的事件侦听器函数。

  ```
  // event(事件)工具集，来源：github.com/markyun
     markyun.Event = {
         // 页面加载完成后
         readyEvent : function(fn) {
             if (fn==null) {
                 fn=document;
             }
             var oldonload = window.onload;
             if (typeof window.onload != 'function') {
                 window.onload = fn;
             } else {
                 window.onload = function() {
                     oldonload();
                     fn();
                 };
             }
         },
         // 视能力分别使用dom0||dom2||IE方式 来绑定事件
         // 参数： 操作的元素,事件名称 ,事件处理程序
         addEvent : function(element, type, handler) {
             if (element.addEventListener) {
                 //事件类型、需要执行的函数、是否捕捉
                 element.addEventListener(type, handler, false);
             } else if (element.attachEvent) {
                 element.attachEvent('on' + type, function() {
                     handler.call(element);
                 });
             } else {
                 element['on' + type] = handler;
             }
         },
         // 移除事件
         removeEvent : function(element, type, handler) {
             if (element.removeEventListener) {
                 element.removeEventListener(type, handler, false);
             } else if (element.datachEvent) {
                 element.detachEvent('on' + type, handler);
             } else {
                 element['on' + type] = null;
             }
         },
         // 阻止事件 (主要是事件冒泡，因为IE不支持事件捕获)
         stopPropagation : function(ev) {
             if (ev.stopPropagation) {
                 ev.stopPropagation();
             } else {
                 ev.cancelBubble = true;
             }
         },
         // 取消事件的默认行为
         preventDefault : function(event) {
             if (event.preventDefault) {
                 event.preventDefault();
             } else {
                 event.returnValue = false;
             }
         },
         // 获取事件目标
         getTarget : function(event) {
             return event.target || event.srcElement;
         },
         // 获取event对象的引用，取到事件的所有信息，确保随时能使用event；
         getEvent : function(e) {
             var ev = e || window.event;
             if (!ev) {
                 var c = this.getEvent.caller;
                 while (c) {
                     ev = c.arguments[0];
                     if (ev && Event == ev.constructor) {
                         break;
                     }
                     c = c.caller;
                 }
             }
             return ev;
         }
     };

  ```


## **jquery**

* Jquery与jQuery UI 有啥区别？
  * jQuery是一个js库，主要提供的功能是选择器，属性修改和事件绑定等等。
  * jQuery UI则是在jQuery的基础上，利用jQuery的扩展性，设计的插件。提供了一些常用的界面元素，诸如对话框、拖动行为、改变大小行为等等

* jquery 中如何将数组转化为json字符串，然后再转化回来？

  * jQuery中没有提供这个功能，所以你需要先编写两个jQuery的扩展：

    ```
    $.fn.stringifyArray = function(array) {
        return JSON.stringify(array)
    }

    $.fn.parseArray = function(array) {
        return JSON.parse(array)
    }

    然后调用：
    $("").stringifyArray(array)

    ```


* 针对 jQuery 的优化方法？

  * 基于Class的选择性的性能相对于Id选择器开销很大，因为需遍历所有DOM元素。
  * 频繁操作的DOM，先缓存起来再操作。用Jquery的链式调用更好。比如：`var str=$("a").attr("href");`
  * for 循环每一次循环都查找了数组 \(arr\) 的.length 属性，在开始循环的时候设置一个变量来存储这个数字，可以让循环跑得更快：`for (var i = size, length = arr.length; i < length; i++) {}`

* 你觉得jQuery或zepto源码有哪些写的好的地方


jquery源码封装在一个匿名函数的自执行环境中，有助于防止变量的全局污染，然后通过传入window对象参数，可以使window对象作为局部变量使用，好处是当jquery中访问window对象的时候，就不用将作用域链退回到顶层作用域了，从而可以更快的访问window对象。同样，传入undefined参数，可以缩短查找undefined时的作用域链。

```
(function( window, undefined ) {
     //用一个函数域包起来，就是所谓的沙箱
     //在这里边var定义的变量，属于这个函数域内的局部变量，避免污染全局
     //把当前沙箱需要的外部变量通过函数参数引入进来
     //只要保证参数对内提供的接口的一致性，你还可以随意替换传进来的这个参数
    window.jQuery = window.$ = jQuery;
})( window );

```

jquery将一些原型属性和方法封装在了jquery.prototype中，为了缩短名称，又赋值给了jquery.fn，这是很形象的写法。

有一些数组或对象的方法经常能使用到，应将它们保存为局部变量以提高访问速度。

将全局对象window作为参数传入，则可以使之在匿名函数内部作为局部变量访问，提供访问速度。

jquery实现的链式调用可以节约代码，所返回的都是同一个对象，可以提高代码效率。

* jquery 如何绑定事件？
* JQuery一个对象可以同时绑定多个事件，这是如何实现的？

  * 在jQuery内部实现中，每个元素对应的每个事件，只会调用一次addEventListener，用来触发事件分派函数。jQuery是利用jquery.data函数将这两个函数存在对象专属的存储空间里，当触发了click事件的同时也触发了事件分派函数，该函数会遍历专属的存储空间，根据一系列的条件筛选事件函数，这些条件包括子选择符，事件组名等等，最后将筛选出来的函数一一执行。

* jQuery取到的元素和原生Js取到的元素有什么区别

  * 通过JavaScript方法获得的DOM元素就是DOM对象。而通过jQuery选择器取得的DOM元素，是对DOM对象进行的一个包装，此时得到的就是jQuery对象。对于jQuery对象，就可以使用相应的jQuery方法。

* jQuery的联级有什么好处

  * 节省代码量，代码看起来更优雅。




## **node**

* 如何判断当前脚本运行在浏览器还是node环境中？（阿里）

  * 通过判断Global对象是否为window，如果不为window，当前脚本没有运行在浏览器中

* Node.js的适用场景？

  * 高并发、聊天、实时消息推送

* 对Node的优点和缺点提出了自己的看法？

  * （优点）因为Node是基于事件驱动和无阻塞的，所以非常适合处理并发请求，因此构建在Node上的代理服务器相比其他技术实现（如Ruby）的服务器表现要好得多。 此外，与Node代理服务器交互的客户端代码是由javascript语言编写的，因此客户端和服务器端都用同一种语言编写，这是非常美妙的事情
  * Node是一个相对新的开源项目，所以不太稳定，它总是一直在变，而且缺少足够多的第三方库支持。看起来，就像是Ruby\/Rails当年的样子。


## **其他**

* "use strict";是什么意思 ? 使用它的好处和坏处分别是什么？

  * 严格模式。
  * 好处：消除Javascript语法的一些不合理、不严谨之处，减少一些怪异行为;消除代码运行的一些不安全之处，保证代码运行的安全；提高编译器效率，增加运行速度；为未来新版本的Javascript做好铺垫。
  * 坏处：同样的代码，在"严格模式"中，可能会有不一样的运行结果；一些在"正常模式"下可以运行的语句，在"严格模式"下将不能运行。
  * 严格模式主要有以下限制：
    * 变量必须声明后再使用
    * 函数的参数不能有同名属性，否则报错
    * 不能使用with语句
    * 不能对只读属性赋值，否则报错
    * 不能使用前缀0表示八进制数，否则报错
    * 不能删除不可删除的属性，否则报错
    * 不能删除变量delete prop，会报错，只能删除属性delete global\[prop\]
    * eval不会在它的外层作用域引入变量
    * eval和arguments不能被重新赋值
    * arguments不会自动反映函数参数的变化
    * 不能使用arguments.callee
    * 不能使用arguments.caller
    * 禁止this指向全局对象
    * 不能使用fn.caller和fn.arguments获取函数调用的堆栈
    * 增加了保留字（比如protected、static和interface）


* 什么是组件？


所谓组件，即封装起来的具有独立功能的UI部件。component , widget , module , plugin ...etc

* 那些操作会造成内存泄漏？

  * 内存泄漏指任何对象在您不再拥有或需要它之后仍然存在。
  * 当页面中元素被移除或替换时，若元素绑定的事件仍没被移除，在IE中不会作出恰当处理，此时要先手工移除事件，不然会存在内存泄露。
  * 闭包可以维持函数内局部变量，使其得不到释放。
  * setTimeout 的第一个参数使用字符串而非函数的话，会引发内存泄漏。
  * 控制台日志、循环（在两个对象彼此引用且彼此保留时，就会产生一个循环）

* 异步加载和延迟加载

  * 动态插入script标签
  * 通过ajax去获取js代码，然后通过eval执行
  * script标签上添加defer或者async属性
  * 创建并插入iframe，让它异步执行js

* 说几条写JavaScript的基本规范？

  1. 不要在同一行声明多个变量。
  2. 请使用 ===\/!==来比较true\/false或者数值
  3. 使用对象字面量替代new Array这种形式
  4. 不要使用全局函数。
  5. switch语句必须带有default分支
  6. 函数不应该有时候有返回值，有时候没有返回值。
  7. For循环、if语句必须使用大括号
  8. for-in循环中的变量应该使用var关键字明确限定作用域，从而避免作用域污染。

* JSON 的了解？

  * JSON\(JavaScript Object Notation\) 是一种轻量级的数据交换格式。
  * 它是基于JavaScript的一个子集。数据格式简单, 易于读写, 占用带宽小 {"age":"12", "name":"back"}

  * JSON在string上下文中，它是字符串。

  * 也有JSON对象，它有两个方法，一个是JSON.parse,将字符串解析为对象，一个是JSON.stringfy将对象序列化为JSON字符串。

* Javascript垃圾回收方法

  * 标记清除（mark and sweep）：（常用）当变量进入执行环境的时候，垃圾回收器将其标记为“进入环境”，当变量离开环境的时候（函数执行结束）将其标记为“离开环境”。垃圾回收器会在运行的时候给存储在内存中的所有变量加上标记，然后去掉环境中的变量以及被环境中变量所引用的变量（闭包），在这些完成之后仍存在标记的就是要删除的变量了
  * 引用计数\(reference counting\)：跟踪记录每个值被使用的次数，当声明了一个变量并将一个引用类型赋值给该变量的时候这个值的引用次数就加1，如果该变量的值变成了另外一个，则这个值得引用次数减1，当这个值的引用次数变为0的时 候，说明没有变量在使用，这个值没法被访问了，因此可以将其占用的空间回收，这样垃圾回收器会在运行的时候清理掉引用次数为0的值占用的空间。
  * 在IE中虽然JavaScript对象通过标记清除的方式进行垃圾回收，但BOM与DOM对象却是通过引用计数回收垃圾的， 也就是说只要涉及BOM及DOM就会出现循环引用问题。


## **ES6的了解**

* 新增模板字符串（为JavaScript提供了简单的字符串插值功能）
* 箭头函数（操作符左边为输入的参数，而右边则是进行的操作以及返回的值Inputs=&gt;outputs。）
* for-of（用来遍历数据—例如数组中的值。）
* arguments对象可被不定参数和默认参数完美代替。
* ES6将promise对象纳入规范，提供了原生的Promise对象。
* 增加了let和const命令，用来声明变量。
* let命令实际上就增加了块级作用域。ES6规定，var命令和function命令声明的全局变量，属于全局对象的属性；let命令、const命令、class命令声明的全局变量，不属于全局对象的属性。
* 还有就是引入module模块的概念

## **js数组去重**

以下是数组去重的三种方法：

```
Array.prototype.unique1 = function () {
  var n = []; //一个新的临时数组
  for (var i = 0; i < this.length; i++) //遍历当前数组
  {
    //如果当前数组的第i已经保存进了临时数组，那么跳过，
    //否则把当前项push到临时数组里面
    if (n.indexOf(this[i]) == -1) n.push(this[i]);
  }
  return n;
}

Array.prototype.unique2 = function()
{
    var n = {},r=[]; //n为hash表，r为临时数组
    for(var i = 0; i < this.length; i++) //遍历当前数组
    {
        if (!n[this[i]]) //如果hash表中没有当前项
        {
            n[this[i]] = true; //存入hash表
            r.push(this[i]); //把当前数组的当前项push到临时数组里面
        }
    }
    return r;
}



Array.prototype.unique3 = function()
{
    var n = [this[0]]; //结果数组
    for(var i = 1; i < this.length; i++) //从第二项开始遍历
    {
        //如果当前数组的第i项在当前数组中第一次出现的位置不是i，
        //那么表示第i项是重复的，忽略掉。否则存入结果数组
        if (this.indexOf(this[i]) == i) n.push(this[i]);
    }
    return n;
}

```

## **实现一个函数clone，可以对JavaScript中的5种主要的数据类型（包括Number、String、Object、Array、Boolean）进行值复制**

```
Object.prototype.clone = function(){
       var o = this instanceof Array ? [] : {};
        for(var e in this){
                o[e] =this[e] instanceof Object ? this[e].clone() : this[e];
        }
        return o;
}


```

## **编写一个方法 求一个字符串的字节长度**

假设：一个英文字符占用一个字节，一个中文字符占用两个字节

```
 function GetBytes(str){    
        var len = str.length;   
        var bytes = len;    
        for(var i=0; i<len; i++){   
            if (str.charCodeAt(i) > 255) bytes++;
        }   
        return bytes;   
    }
    alert(GetBytes("你好,as"));
```

