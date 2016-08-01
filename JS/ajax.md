## AJAX

var xhr = new XMLHttpRequest\(\);

xhr.open\("get", "example.php", true\); \/\/最后一个参数表示是否异步

xhr.send\(\);\/\/参数为作为请求主体发送的数据，没有就null

收到响应后，响应数据自动填充XHR对象的属性，有responseText、responseXML、status、statusText，异步的话有readyState属性，它的改变会触发readystatechange 事件。

readyState中0表示未初始化，没调用open\(\)方法，1表示启动，调用open\(\)未调用send\(\),2发送，调用send\(\)未收到响应，3接收到部分响应数据，4接收到全部响应数据。

### HTTP头部信息

使用setRequestHeader\(\)方法可以设置自定义的请求头部信息。这个方法接受两个参数：头部字段的名称和头部字段的值。要成功发送请求头部信息，必须在调用open\(\)方法之后且调用send\(\)方法之前调用setRequestHeader\(\)。调用XHR 对象的getResponseHeader\(\) 方法并传入头部字段名称，可以取得相应的响应头部信息。而调用getAllResponseHeaders\(\)方法则可以取得一个包含所有头部信息的长字符串。

### get和post请求

get通常请求用于向服务器查询信息，具有幂等性。一般将查询字符串参数追加到URL 的末尾，以便将信息发送给服务器。查询字符串中每个参数的名称和值都必须使用encodeURIComponent\(\)进行编码，且用&号分开。

post通常用于向服务器发送应该被保存的数据。通过创建FormData对象，可以序列化表单以及创建与表单格式相同的数据（用于通过XHR 传输）。使用FormData 的方便之处体现在不必明确地在XHR 对象上设置请求头部。XHR 对象能够识别传入的数据类型是FormData 的实例，并配置适当的头部信息。

### 进度事件

* loadstart：在接收到响应数据的第一个字节时触发。

* progress：在接收响应期间持续不断地触发。

*  error：在请求发生错误时触发。事件处理程序会接收到一个event 对象，其target 属性是XHR 对象，但包含着三个额外的属性：lengthComputable（进度是否可用的布尔值）、position（表示已经接收的字节数） 和totalSize（根据Content-Length 响应头部确定的预期字节数）。

*  abort：在因为调用abort\(\)方法而终止连接时触发。

* load：在接收到完整的响应数据时触发。

* loadend：在通信完成或者触发error、abort 或load 事件后触发。


## 跨域

问题来源——同源策略，协议相同、域名相同、端口相同。

### CORS（跨源资源共享）

CORS 背后的基本思想，就是使用自定义的HTTP 头部让浏览器与服务器进行沟通，从而决定请求或响应是应该成功，还是应该失败。

发送请求时给它附加一个额外的Origin 头部，其中包含请求页面的源信息（协议、域名和端口），以便服务器根据这个头部信息来决定是否给予响应。服务器设置Access-Control-Allow-Origin，请求和响应都不包含cookie 信息。跨域XHR 对象也有一些限制，不能使用setRequestHeader\(\)设置自定义头部、 不能发送和接收cookie、调用getAllResponseHeaders\(\)方法总会返回空字符串。

### JSONP

JSONP 由两部分组成：回调函数和数据。回调函数是当响应到来时应该在页面中调用的函数。回调函数的名字一般是在请求中指定的。通过动态&lt;script&gt;元素来使用，使用时可以为src 属性指定一个跨域URL。问题：安全问题，难以判断请求是否失败。

### window.name

window.name 在一个窗口（标签）的生命周期之内是共享的，利用这点就可以传输一些数据。

可以父窗口打开一个不同源的子窗口，该网页信息写入window.name，然后子窗口调回到主窗口同域的代理页面网址，就可以读取window.name信息了。结合iframe可以直接读取信息。

### document.domain

跨子域。 把两个同主域，不同子域的文件的 document.domain 设置成**为页面本身或者更高一级的域名。**

### location.hash

监听hashchange事件，子页面可以通过window.location.hash给父页面传数据，父页面可以改变iframe子页面的src来给子页面传数据。

### postMessage

使用postMessage\(data,url\)来发送数据，  调用postMessage方法的window对象是指要接收消息的那一个window对象。通过message事件，监听对方的消息，message事件对象的属性有source、origin、data，接收消息的窗口可以用event.source引用发送消息的窗口，而event.origin可以过滤掉不是发送给本窗口的消息。可以通过它来读写其他窗口的localStorage.

以上后四种方法经常配合iframe使用， iframe主要的两个API就是contentWindow,和contentDocument ，前者用于获取iframe的window对象，后者 获取iframe的document对象。



## 安全

### XSS（跨站脚本攻击，Cross Site Script\)

当来自用户的不可信数据在没有验证以及反射回浏览器而没有进行编码或转义的情况下进行了处理， 导致浏览器引擎执行了代码。\

反射型XSS：简单地把用户输入“反射”给浏览器，往往需要用户点击一个恶意链接才能攻击成功。

存储型XSS：把用户输入数据存储在服务器端（恶意js代码的博客）

DOM Based XSS：修改页面DOM节点形成的XSS

防护：验证输入并基于语境和按照正确顺序转义不可信数据。

### CSRF

对于未被授权系统有权访问某个资源的情况，我们称之为CSRF（Cross-Site Request Forgery，跨站点请求伪造）。未被授权系统会伪装自己，让处理请求的服务器认为它是合法的。



请注意，下列措施对防范CSRF 攻击不起作用：要求发送POST 而不是GET 请求——很容易改变。 检查来源URL 以确定是否可信——来源记录很容易伪造。 基于cookie 信息进行验证——同样很容易伪造。

防御：验证码，要求以SSL 连接来访问可以通过XHR 请求的资源、要求每一次请求都要附带经过相应算法计算得到的验证码。 



