# 引用类型

## Obj类型

创建方法：1.new Func\(\) 使用构造函数  2.对象字面量

访问属性：1.obj\['name'\] 2.obj.name 第一种可以通过变量访问属性，可以使用会导致语法错的的字符串表示属性名

ES6对对象进行了扩展：

* 可以在对象中只写属性名，属性值则为属性名代表的变量；方法可以简写为 func\(\){}这种形式

* 对象字面量定义时，可以在‘\[\]'内用表达式作为属性名

* Object.is\(\)比较两个值是否严格相等，+0不等于-0，NaN等于自身

* Object.assign\(\)，用于对象合并， 第一个参数是目标对象。后面都是源对象，同名属性后面覆盖前面的，只复制自身属性，浅拷贝，可以用来为对象添加属性和方法、以空对象为目标来克隆对象、合并多个对象、为属性指定默认值等。

* Object.getOwnPropertyDescriptor\(对象，属性名\)方法获取属性的描述对象
* 属性的遍历:for...in不含Symbol的自身和继承的可枚举属性，Object.keys\(obj\)不含Symbol的自身可枚举属性,Object.getOwnPropertyNames\(obj\)返回不含Symbol包含不可枚举属性的包含对象自身所有属性的数组,Object.getOwnPropertySymbols\(obj\)返回包含自身所有Symbol属性的数组,Reflect.ownKeys\(obj\)返回对象自身所有属性。
* 关于原型的\_\_proto\_\_属性，和Object.setPrototypeOf\(\)和Object.getPrototypeOf\(\)方法
* Object.values\(\)和Object.entries\(\)返回相应数组

## Array类型

创建方法：1.new Array\(\) 传递一个数字参数表示生成数组长度，其他表示数组元素内容 2.数组字面量

length属性：不是只读的

检测数组的方法：1.arr instanceof  Array 2.Array.isArray\(arr\) 3.Object.prototype.toString.call\(arr\)=="\[object Array\]"

转换为字符串的方法：toLocaleString\(\),toString\(\),valueOf\(\),join\(\) 前三者默认以逗号相隔

栈方法：push\(\),pop\(\)

队列方法：shift\(\),unshift\(\)

重排序方法：reverse\(\),sort\(\) 返回排序后的数组，原数组改变

操作方法：concat\(item1,item2....\),slice\(begin\[,end\]\)参数可为负数,splice\(start, deleteCount\[, item1\[, item2\[, ...\]\]\]\),前两者不影响原数组返回新数组，splice改变原数组，返回删除项组成的数组

位置方法：indexOf\(\),lastIndexOf\(\)

迭代方法：every\(\) ,some\(\) ,filter\(\),forEach\(\),map\(\) 它们的参数都为 \(_callback_\[, _thisArg_\]\)，回调函数被调用时传入参数为 \(element, index, array\) 区别在于返回值，every\(\)每项都返回true则返回true ，some任一项返回true则返回true ，filter返回返回true的项组成的数组，forEach没有返回值，map返回每项经过函数返回的结果组成的数组

归并方法：reduce\(\),reduceRight\(\),参数为\(callback,_\[\_initialValue_\]\_\)，回调函数被调用时传入参数为\(`previousValue,currentValue,index,array)`

ES6中新增方法：

* Array.from\(arrayLike\[, mapFn\[, thisArg\]\]\) 将类数组转换为数组

* Array.of\(element0\[, element1\[, ...\[, elementN\]\]\]\) 把元素转换为数组，弥补Array\(\)和new Array\(\)的不足

* copyWithin\(targetStart, start\[, end = this.length\]\) 数组内部成员赋值到其他位置，返回当前数组，会改变原数组

* find\(_callback_\[, _thisArg_\]\)和findIndex\(_callback_\[, _thisArg_\]\)查找第一个回调函数返回true的元素或者元素索引

* fill\(value\[, start = 0\[, end = this.length\]\]\) 填充，返回当前数组并改变原数组

* entries\(\)，keys\(\)和values\(\) 分别表示对数组键值对、键名、键值遍历，返回相应迭代器

* includes\(searchElement\[, fromIndex\]\) 判断数组是否包含指定值

数组的空位：ES5中forEach\(\),filter\(\),every\(\)和some\(\)会跳过空位，map\(\)跳过空位但保留这个值，join\(\)和toString\(\)把空位视为undefined转换为空字符串。ES6中将空位转为undefined.

## Date类型

new Date\(\) 不传递参数为当前时间，传递参数按参数设置时间。获得当前时间的毫秒表示：+new Date\(\) 或 Date.now\(\)

时间日期组件方法：getTime\(\)\/setTime\(毫秒\),getFullYear,getMonth,getDate,getDay星期,getHours,getMinutes,getSeconds,getMilliseconds，和相应的set方法

## RegExp类型

语法：var expression = \/ pattern \/ flags 字面量形式，也可以用RegExp构造函数

flags包括 g,i,m,分别表示全局、不区分大小写，多行

pattern是可以包含字符类、限定符、分组、向前查找和反向引用的正则表达式。

元字符要转义，包括\( \[ { \ ^ $ \| \) ? \* + .\]}

实例方法：

* exec\(str\),返回包含第一个匹配项信息的数组，有index和input两个额外属性，第一项为与整个模式匹配的字符串，其他项时与模式中的捕获组匹配的字符串。设置全局标志则向后查找，不设置则一直返回第一个匹配项信息。

* test\(str\) 匹配返回true，否则返回false

* toString\(\),toLocaleString\(\)，返回正则表达式字面量


构造函数的属性：input $\_,lastMatch $&,lastParen $+,leftContext $\`,mutiline $\*,rightContext $'

## Function类型

见函数章节。

ES6中对函数进行了扩展，函数参数可以默认声明，且length返回没有指定默认值得参数个数。在函数参数中可以用rest参数’...'来获取多余参数，得到的是一个数组。而在调用函数传参的时候可以使用spread运算\(...\)来把数组转换为逗号分隔的参数序列，可以取代apply方法用于Math.max、arr.push等。

name属性做了修改，对匿名函数会返回实际的函数名。

箭头函数，函数体内this就是定义时所在对象。

## 基本包装类型Boolean、Number 和String

和基本类型的差别在于生命期，自动创建的基本包装类型的对象，只存在于一行代码的执行瞬间，然后立即被销毁。

直接实例化基本包装类型，导致typeof 的结果是object，instanceof是其包装类型。

### Number

toString\(\)方法可以传递一个表示基数的参数。

还有方法toFiexed,toExponential,toPrecision.

ES6中，提供了二进制和八进制的新写法0b,0o,和方法isFinite\(\),isNaN\(\),parseInt\(\),parseFloat\(\),isInteger\(\)和属性EPSILON表示极小的常量为浮点数计算设置误差范围，以及安全整数和isSafeInteger\(\)方法。

### String

字符方法： charAt\(i\)和charCodeAt\(i\)

字符串操作方法：concat\(\) 用于连接字符一般用"+“完成，slice\(start\[,end\]\)、substr\(start\[,length\]\)和substring\(start\[,end\]\),substring将负参数转为0

字符串位置方法：indexOf\(\)和lastIndexOf\(\)

trim\(\)方法，去除前后空格

大小写转换方法：：toLowerCase\(\)、toLocaleLowerCase\(\)、toUpperCase\(\)和toLocaleUpperCase\(\)

字符串的模式匹配方法：

* match\(\)，同RegExp的exec\(\)方法

* search\(\)，返回第一个匹配项的索引

* replace\(\)，第一个参数可以是字符串或正则表达式，第二个参数是字符串或函数，函数的参数有：模式的匹配项、模式匹配项在字符串中的位置和原始字符串

* split\(\)


localeCompare\(\)方法，比较字符串
fromCharCode\(\)方法，把字符编码转换为字符

## 单体内置对象

### Global对象

URI 编码方法：encodeURI\(\)和encodeURIComponent\(\)

eval方法

属性：undefined、NaN和Infinity和原生引用类型的构造函数如Object、Function

### Math

属性：Math.E 自然对数的底数，即常量e的值，Math.LN10 10的自然对数，Math.LN2 2的自然对数，Math.LOG2E 以2为底e的对数，Math.LOG10E 以10为底e的对数，Math.PI π的值，Math.SQRT1\_2 1\/2的平方根（即2的平方根的倒数），Math.SQRT2 2的平方根

min\(\)和max\(\)方法,可以用Math.max.apply\(Math,arr\)来求数组最大值，ES6中用Math,max\(...arr\)即可。

舍入方法：ceil\(\),floor\(\),round\(\)

random\(\)方法，生成0~1之间的随机数，可以用Math.floor\(Math.random\(\) \* 可能值的总数 + 第一个可能的值\)随机生成一个数。

其他方法：Math.abs\(num\),Math.exp\(num\), Math.log\(num\) , Math.pow\(num,power\) , Math.sqrt\(num\) , Math.asin\(x\),   Math.acos\(x\) ,Math.atan\(x\),Math.atan2\(y,x\),Math.cos\(x\), Math.sin\(x\),Math.tan\(x\)

ES6扩展了指数运算符\(\*\*）和以下方法：

* Math.trunc\(\) 去除一个数的小数部分，返回整数部分，非数值会转换为数值

* Math.sign\(\) 判断一个数到底是正数、负数还是0，返回+1 -1 +0 -0 NaN

* Math.cbrt\(\) 计算一个数的立方，先转换为数值

* Math.clz32\(\) 整数使用32位二进制形式表示有多少个前导0（count leading zero...）,只考虑整数部分

* Math.imul\(\) 返回两个数以32位带符号整数形式相乘的结果，返回的也是一个32位的带符号整数

* Math.fround\(\) 返回一个数单精度浮点数形式

* Math.hypot\(\) 返回所有参数平方和的平方根

* 对数方法：log1p\(\),log10\(\),log2\(\)

* 三角函数方法：sinh\(\),cosh\(\),tanh\(\),asinh\(\),acosh\(\),atanh\(\)


## ES6中的Map和Set

### Map

它类似于对象，也是键值对的集合，但是“键”的范围不限于字符串，各种类型的值（包括对象）都可以当作键。也就是说，Object结构提供了“字符串—值”的对应，Map结构提供了“值—值”的对应，是一种更完善的Hash结构实现。如果你需要“键值对”的数据结构，Map比Object更合适。

属性：size表示有多少个键值对

操作方法： set\(key,value\) 返回Map 本身，可以采用链式写法 ，get\(key\)，has\(key\)，delete\(key\)，clear\(\)

遍历方法： keys\(\),values\(\),entries\(\),forEach\(\)

WeakMap:键名所指对象不计入垃圾回收，没有遍历操作、size属性、clear方法，可用于DOM节点做键名时

### Set

没有重复值的数组

属性：Set.prototype.constructor,Set.prototype.size\(成员总数）

操作方法：add\(value\),delete\(value\),has\(value\),clear\(\)

遍历操作：keys\(\),values\(\),entries\(\),forEach\(\)

应用： \[...new Set\(array\)\] 去除重复数组成员，\[...set\]将set结构变为数组

WeakSet:成员只能是对象，对象都是弱引用，垃圾回收机制不考虑，不可遍历，没有clear方法,可用于存储DOM节点

