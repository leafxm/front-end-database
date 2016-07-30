# BOM和DOM

## BOM浏览器对象模型

### window对象

top 对象始终指向最外围的框架，也就是整个浏览器窗口。

parent 对象表示包含当前框架的框架，而self 对象则回指window

窗口位置：window.screenX\/Y

框口大小：

*  window.innerWidth\/Height 包含滚动条的浏览器视口完整尺寸，手机浏览器中表示visual viewport尺寸

* document. documentElement. clientWidth\/Height 不包含滚动条的浏览器视口尺寸，手机浏览器中表示layout vieport尺寸



打开窗口：window.open\(\)。这个方法可以接收4 个参数：要加载的URL、窗口目标、一个特性字符串以及一个表示新页面是否取代浏览器历史记录中当前加载页面的布尔值。

setTimeout和setInterval：注意回调函数的作用域和执行上下文。如果第一个参数是代码字符串，那么它的上级作用域是全局作用域，而使用函数则是定义时的作用域。如果第一个参数是函数名，那么相当于该函数是直接调用（即使是用obj.fun这样的形式\)，而匿名函数中的obj.func的this是指向obj，但是this也是全局的（因为这个匿名函数相当于直接调用）。

系统对话框：alert\(\)，confirm\(\)和prompt\(\)

### location对象

提供了与当前窗口中加载的文档有关的信息，还提供了一些导航功能。

查询字符串参数：location.search 返回从问号到URL 末尾的所有内容，以“？"开头

位置操作：location.href或window.location 设置为一个URL 值，调用assign\(\)方法，也可以通过hash、search、hostname、pathname 和port属性来改变。replace\(\)方法让用户不能回到前一个页面。reload\(\)，作用是重新加载当前显示的页面，传参true强制从服务器加载

### history对象

保存历史记录。参数为数字表示前进或后退页数，可以为字符串。有back\(\),forward\(\)方法和length属性

## DOM文档对象模型

DOM描绘了一个层次化的节点树。

### 节点类型

 node类型：Element类型、Text类型、Attr类型、comment类型、document类型、documentFragment类型。

每个节点都有属性NodeType，是用一个整数表示节点类型，如：元素element 1、属性attr 2、文本text 3、注释comments 8、文档document 9 。对Element类型来说，元素的nodeName属性 中保存都是元素的标签名。

### 节点关系

#### 父关系

1. parentNode
2. parentElement

#### 兄弟关系

1. previousSibling
2. previousElementSibling IE9以下不支持
3. nextSibling
4. nextElementSibling IE9以下不支持

#### **子关系**

1. childNodes:返回即时NodeList
2. chidren:返回即时HTMLCollection，子元素都是element，IE9以下不支持
3. firstNode
4. lastNode
5. hasChildNodes方法：判断是否包含子节点

对于DOM元素，有childElementCount,firstElementChild,lastElementChild,previousElementSibling,nextElementSibling\(避免IE9前对文本节点是否被返回的不一致性\)
### **节点创建型API**

1. createElement
2. createTextNode
3. parent.cloneNode（true）true表示复制子节点
4. createDocumentFragment 用于添加大量节点到文档，防止回流造成的性能问题

只是创建，并没有添加到文档中，需要通过页面修改型API来加入节点

### **页面修改型API**

1. parent.appendChild\(child\)
2. parentNode.insertBefore\(newNode,refNode\); 参考元素要是父元素的子元素
3. parent.removeChlid\(node\); 返回被删除的节点
4. parent.replaceChild\(newChild,oldChild\)

不管是新增还是替换节点，如果新增或替换的节点是原本存在页面上的，则其原来位置的节点将被移除，也就是说同一个节点不能存在于页面的多个位置。

### **节点查询型API**

1. document.getElementById id大小写敏感
2. document.getElementsByTagName 返回即时的HTMLCollection类型\(结果会随文档树变化而变化\)
3. document.getElementsByName 返回即时的NodeList对象
4. document.getElementsByClassName 返回即时的HTMLCollection类型，IE9以下浏览器不支持，可用空格相隔获取多个classname
5. document.querySelector 和 document.querySelectorAll 都是使用深度优先来获取元素，前者返回第一个匹配的元素，后者返回所有匹配元素，返回的是一个非即时的NodeList，ie8以下的浏览器不支持

调用者也可以是一个元素
### **元素属性型API**

1. element.setAttribute\(name,value\)
2. element.getAttribute\(name\)

### **元素样式型API**

1. window.getComputedStyle\(element\[, pseudoElt\]\) window.getComputedStyle是用来获取应用到元素后的样式，假设某个元素并未设置高度而是通过其内容将其高度撑开，这时候要获取它的高度就要用到getComputedStyle
2. element.getBoundingClientRect\(\); 返回元素的大小以及相对于浏览器可视窗口的位置

### DOM操作

#### 动态脚本

动态创建script元素，为它添加src属性。

或者动态创建script元素，通过appendChild （textNode，IE中使用script.text）来添加内容

#### 动态样式

动态创建link元素，为它添加rel、type、href等属性并添加为head元素的子元素。

或者动态创建style元素，通过appendChild（textNode，IE中使用style.styleSheet.cssText）来添加内容

#### 操作表格

通过rows属性获得全部行，行的cells属性获得该行的列，它们有length属性获得个数，在事件中可以使用this.cellIndex和this.parentNode.rowIndex获得表格单元的行列数（从0计算）。



### HTML5中的DOM扩展

classList属性，获得元素的类名，该属性还有add,contains,remove,toggle方法



