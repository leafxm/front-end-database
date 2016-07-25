# 对象

## Obj类型

创建方法：1.new Func\(\) 使用构造函数  2.对象字面量

访问属性：1.obj\['name'\] 2.obj.name 第一种可以通过变量访问属性，可以使用会导致语法错的的字符串表示属性名

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

归并方法：reduce\(\),reduceRight\(\),参数为\(callback,_\[_initialValue_\]_\)，回调函数被调用时传入参数为\(`previousValue,currentValue,index,array)`



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





