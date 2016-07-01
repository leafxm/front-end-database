# 基础知识

## 数据类型
ES5中基本数据类型有五种：Undefined,Null,Boolean,Number和String，还有一种复杂数据类型Object。

ES6引入新的原始数据类型Symbol,表示独一无二的值。

## 操作符
有递增递减操作符、布尔操作符、乘性操作符、加性操作符、关系操作符和相等操作符等。

注意隐式转换。

delete 操作符，用来删除对象的属性（不能用来操作变量

## 语句
if,while,do-while,for,for-in,label,with等

## 变量
基本类型值指的是简单的数据段，而引用类型值指那些可能由多个值构成的对象。

可以为引用类型的值添加、改变、删除属性和方法，对基本类型这样不会出错，但是**无效**。

复制变量的方式：基本类型会建立一个完全独立的新变量，把值复制过去；而引用类型复制的是指向原对象的指针，结束后两个变量将引用同一个对象。

传递参数：按值传递，引用类型复制指向原对象的指针，当把参数名指向新的内存空间，则和原对象无关了。

## 执行环境和作用域
执行环境(execution context,EC)定义变量或函数有权访问的其他数据，决定其各自行为。每个执行环境有个与之关联的变量对象(variable object,VO)，环境中定义的所有变量和函数都保存在这个变量中。

全局执行环境：在Web 浏览器中，全局执行环境被认为是window 对象，因此所有全局变量和函数都是作为window 对象的属性和方法创建的。

全局执行环境中有变量、函数表达式，this，函数声明这样几种数据，函数执行环境中还包括arguments和自由变量（在该函数中使用却不是在该函数中声明的变量）的取值作用域。

函数作用域在定义时确定。函数的执行环境在执行时确定。

JS引擎在进入一段可执行代码时，需要完成三个初始化工作：

1. 创建全局对象(Global Object)
2. 构建执行环境栈，并创建一个全局执行环境(execution context,EC)，并将其压入执行环境栈。
3. 创建与EC关联的全局变量对象VO，并把VO指向全局对象。

当执行函数A时，JS引擎需要完成：

1. 创建函数A的执行环境EC，把EC推入执行环境栈顶部。
2. 创建函数A的作用域链
3. 创建当前函数的活动对象(activation object)AO,AO中包含了函数的形参、arguments对象、this对象、以及局部变量和内部函数的定义，然后AO会被推入作用域链的顶端。这里还会对在其中定义的函数添加其作用域为这个函数（所以函数的作用域是它定义的环境）。

参考
[ECMA-262-3 in detail. Chapter 1. Execution Contexts.](http://dmitrysoshnikov.com/ecmascript/chapter-1-execution-contexts/)
[ECMA-262-3 in detail. Chapter 2. Variable object.](http://dmitrysoshnikov.com/ecmascript/chapter-2-variable-object/) 


### 变量提升
因为在函数执行时，刚进入函数就会初始化变量和函数声明，变量赋值为undefined，函数声明为它本身，所以，在函数中变量定义前就可以访问到变量了。

### this 
this是在函数执行时确认值的。全局范围的this指向window对象。

函数调用时确认this指向的方式是：

1. 如果**这个**函数是直接调用，则非严格模式时this指代全局范围的this，严格模式时this为undefined。
2. 如果是由对象调用，则this指向该对象（通过bind、call、apply可以把函数的this指向相应的对象）
3. 函数被当做构造函数调用时，this指向这个新对象
4. DOM事件处理程序中，this指向这个处理程序被所绑定到的HTML DOM节点。

## Event Loop
js引擎是单线程的，但是浏览器中还有别的web APIs(如DOM，ajax，setTimeout），当执行这些代码时，js引擎会把操作交给相应的web API，然后继续执行以后的代码，web API执行完相应操作后，将结果放入callback queue，当js引擎空闲时event loop会去callback queue查看是否有待执行的回调函数，如果有的话js引擎会去依次执行这些回调函数。

![](http://image.beekka.com/blog/2014/bg2014100802.png)

参考 [Philip Roberts: What the heck is the event loop anyway?](http://2014.jsconf.eu/speakers/philip-roberts-what-the-heck-is-the-event-loop-anyway.html)
