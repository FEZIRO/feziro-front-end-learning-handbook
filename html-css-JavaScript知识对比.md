#  前端知识/对比手册（持续更新）

#### 很喜欢以对比的方式记录一些容易混淆或者迷惑的前端特性和概念

（整理FEZIRO，内容参考自MDN Web Docs）

<br>

## 伪类和伪元素对比

| 名称   | 语法 | 数量             | 作用                             |
| ------ | ---- | ---------------- | -------------------------------- |
| 伪类   | ：   | 可单个可多个叠加 | 基于DOM产生不同修饰DOM元素的状态 |
| 伪元素 | ：： | 只能单个使用     | 创建不存在DOM中的新元素对象      |

<br/>

## let和const和var对比

| 名称  | 变量提升 | 全局变量 | 重复声明 | 重新赋值 | 暂时死区 | 块作用域 | 只声明不初始化 |
| ----- | -------- | -------- | -------- | -------- | -------- | -------- | -------------- |
| var   | √        | √        | √        | √        | x        | x        | √              |
| let   | x        | x        | x        | √        | √        | √        | √              |
| const | x        | x        | x        | x        | √        | √        | x              |

<br>

## visiable：hidden 和 opacity：0 和 display：none对比

| 名称             | 作用       | 可否点击 |
| ---------------- | ---------- | -------- |
| visiable：hidden | 占位隐藏   | 否       |
| opacity：0       | 占位隐藏   | 是       |
| display：none    | 不占位隐藏 | 否       |

<br>

## 单行溢出隐藏、多行溢出隐藏

| 名称     | css                                                          |
| -------- | ------------------------------------------------------------ |
| 单行溢出 | `width:150px(固定宽度)`<br>`white-space:no-wrap`<br>`overflow:hidden`<br>`text-overflow:ellipsis` |
| 多行溢出 | `width:150px（固定宽度）`<br>`display:-webkit-box;`<br>`-webkit-box-orient:vertical`<br>`-webkit-line-camp:3`<br>`overflow:hidden` |

<br>

## Set、Map和WeakSet、WeakMap的区别

1. WeakSet和WeakMap类没有entiries, keys, values等方法，无法被遍历。

2. WeakSet和WeakMap类只能用对象作为键（key），没有强引用的键，垃圾回收机制可以回收。

3. set, map键和值可以是任意类型。

  <br>

  

## flex：1是什么

| flex：1 | 等于                                              |
| ------- | ------------------------------------------------- |
| flex：1 | flex-grow：1;<br>flex-shrink: 1;<br>flex-basis: 1 |

<br>

## flex布局子项单独靠右

```
  //父元素
  display: flex;
  align-items: center;

  （方法1）
  //子元素
  flex: 1;
  text-align: right;

  （方法2）
  //子元素
  margin-left: auto;
```

<br>

## 垃圾回收GC机制

1、全局变量不会被回收<br>2、局部变量会被回收（函数运行完内部的变量会被回收）<br>3、只要被另外一个作用域所引用不会被回收（闭包	）

| 机制     | 工作原理                                                     |
| -------- | ------------------------------------------------------------ |
| 标记清除 | 标记方式：特殊位的反转、维护一个列表<br>原理：垃圾收集器在运行的时候会给存储在内存中的所有变量都加上标记，然后它会去掉环境中的变量已经被环境中变量被标记为引用的变量，在此之后再被标记的变量将被视为准备删除的变量。最后垃圾回收器清除标记的变量，回收它们所占用的内存空间，目前主流浏览器都是使用标记清除式的垃圾回收策略，只不过收集的间隔有所不同。 |
| 引用计数 | 原理：每次引用加一，被释放时减一，当这个值的引用次数变成 0 时，就可以将其内存空间回收<br>缺点：循环引用(obj1 和 obj2 通过各自的属性相互引用，也就是说，这两个对象的引用次数都是 2) |

<br>

## ES7/ES8新特性

| 版本 | 新特性                                                       |
| ---- | ------------------------------------------------------------ |
| ES7  | 求幂运算符（**）<br>新增Array.prototype.includes()方法       |
| ES8  | async、await异步解决方案<br>Object.entries()<br>Object.values()<br>Object.getOwnPropertyDescriptors获取对象的属性描述符<br>字符串填充padStart()、padEnd() |

<br>



<br>

## null、undefined、NaN区别

| 名称      | 含义                                                         | 特性                                          |
| --------- | ------------------------------------------------------------ | --------------------------------------------- |
| null      | 是一个字面量，指示变量未指向任何对象, 但变量存在且不报undefined错 | 在布尔运算中被认为是falsy<br>类型判断是object |
| undefined | 一个没有被赋值的变量的类型是undefined。如果方法或者是语句中**操作的变量没有被赋值，则会返回undefined** | 原始数据类型<br>类型判断是undefined           |
| NaN       | 不是一个数字                                                 | 不等于任何值，自己不等于自己，可用isNaN()检测 |

<br>

## 严格模式中的变化

1. 无法再意外创建**全局变量**
2. 使引起静默失败**(注:不报错也没有任何效果)**的赋值操作抛出异常。
3. **试图删除不可删除的属性时会抛出异常**。
4. **要求一个对象内的所有属性名在对象内必须唯一**。正常模式下重名属性是允许的，最后一个重名的属性决定其属性值。因为只有最后一个属性起作用，当代码要去改变属性值而不是修改最后一个重名属性的时候，复制这个对象就产生一连串的bug。在严格模式下，重名属性被认为是语法错误。
5. **要求函数的参数名唯一**。在正常模式下, 最后一个重名参数名会掩盖之前的重名参数. 之前的参数仍然可以通过 `arguments[i] 来访问`, 还不是完全无法访问. 然而, 这种隐藏毫无意义而且可能是意料之外的 (比如它可能本来是打错了), 所以在严格模式下重名参数被认为是语法错误。
6. **禁止八进制数字语法**。
7. **禁止设置primitive值的属性**，不采用严格模式,设置属性将会简单忽略(no-op),采用严格模式,将抛出TypeError错误。
8. **禁用 with语句**。
9. **严格模式下 eval 仅仅为被运行的代码创建变量**, 所以 eval 不会使得名称映射到外部变量或者其他局部变量。
10. **禁止删除声明变量**。
11. **严格模式中一部分字符变成了保留的关键字**。这些字符包括`implements`, `interface`, `let`, `package`, `private`, `protected`, `public`, `static`和`yield`。在严格模式下，你不能再用这些名字作为变量名或者形参名。
12. **禁止不在脚本或者函数层面上的函数声明**。在浏览器的普通代码中，在“所有地方”的函数声明都是合法的。
13. **不再支持 arguments.callee**。
14. **参数的值不会随 arguments 对象的值的改变而变化**。
15. **名称 eval和 arguments不能通过程序语法被绑定(be bound)或赋值**。

<br>

## JavaScript基本数据类型（primitive）？

是一种既非对象也无方法的数据（primitive），基本类型值可以被替换，但不能被改变。

共有7种基本类型：**string，number，bigint，boolean，null，undefined，symbol**

<br>

## encodeURI和encodeURIComponent区别

| 名称                                   | 区别                                                         |
| -------------------------------------- | ------------------------------------------------------------ |
| encodeURI、decodeURI                   | 不会对 ASCII字母、数字、~!@#$&*()=:/,;?+'进行编码解码，编码整个URL，然后需要使用这个URL推荐使用 |
| encodeURIComponent、decodeURIComponent | 除 A-Z a-z 0-9 - _ . ! ~ * ' ( )之外编码解码一切字符，编码的范围更广，编码URL中的参数的时候推荐使用 |

<br>

## 栈内存、堆内存区别

| 栈内存             | 堆内存                       |
| ------------------ | ---------------------------- |
| 存储基础数据类型   | 存储引用数据类型             |
| 按值访问           | 按引用访问                   |
| 存储的值大小固定   | 存储的值大小不定，可动态调整 |
| 空间小，效率高     | 空间大，效率低               |
| 先进后出，后进先出 | 无序存储，根据引用访问       |

<br>

## 赋值，深拷贝，浅拷贝区别

| 类型   | 区别                                                         |
| ------ | ------------------------------------------------------------ |
| 赋值   | 基本数据类型：赋值之后两个变量互不影响<br />引用数据类型：赋值两个变量具有相同的引用，指向同一个对象，相互之间有影响 |
| 浅拷贝 | **创建一个新对象，这个对象有着原始对象属性值的一份精确拷贝**。如果属性是基本类型，拷贝的就是基本类型的值，如果属性是引用类型，拷贝的就是内存地址 ，所以如果其中一个对象改变了这个地址，就会影响到另一个对象<br />`{...a} 展开语法`<br />`Object.assign()`<br />`Array.prototype.slice()`<br /> |
| 深拷贝 | 拷贝后不会影响原对象，两者互相独立，互不影响<br />`JSON.parse(JSON.stringify(object))`<br />迭代复制 |

| 类型   | 和原数据是否指向同一对象？ | 第一层数据为基本数据类型     | 原数据中包含子对象           |
| ------ | -------------------------- | ---------------------------- | ---------------------------- |
| 赋值   | 是                         | 改变**会**使原数据一起改变   | 改变**会**使原数据一起改变   |
| 浅拷贝 | 否                         | 改变**不会**使原数据一起改变 | 改变**会**使原数据一起改变   |
| 深拷贝 | 否                         | 改变**不会**使原数据一起改变 | 改变**不会**使原数据一起改变 |

<br>

## Javascript的7种继承区别

| 继承方式                     | 实现方式                                                     | 缺点                                                         |
| ---------------------------- | ------------------------------------------------------------ | ------------------------------------------------------------ |
| 原型继承                     | **子类的原型**指向**父类的实例**                             | 1、没有办法在不影响所有对象实例的情况下，给父类的构造函数传递参数。<br />2、有引用类型的时候，各个实例对该引用的操作会影响其他实例<br /> |
| 借用构造函数继承             | 子类构造函数调用父类构造函数                                 | 1、父类的原型中定义的方法，对子类型而言也是不可见的<br />    |
| 组合继承                     | 将原型继承和借用构造函数继承组合到一起                       | 1、调用两次父类构造函数，一次是在创建子类型原型的时候，另一次是在子类型构造函数内部<br />2、子类最终会包含超类型对象的全部实例属性，但我们不得不在调用子类型构造函数时重写这些属性。 |
| 原型式继承（寄生类继承）     | Object.create(继承对象);                                     |                                                              |
| 寄生式继承（寄生类继承）     | 是原型式继承的加强版，即在产生了这个继承了父类的对象之后，为这个对象添加一些增强方法。 |                                                              |
| 寄生组合式继承（寄生类继承） | 是寄生式继承的加强版                                         | 无                                                           |
| Class继承                    | 通过extends关键字实现继承                                    | 无                                                           |



<br>

## mouse over和mouse enter区别

共同点：当二者都没有子元素时，二者的行为是一致的，但是二者内部都包含子元素时，行为就不同了。

| 名称        | 区别                                                   | 是否冒泡 | 对应移除事件  | 触发顺序 |
| ----------- | ------------------------------------------------------ | -------- | ------------- | -------- |
| mouse over  | 鼠标移入元素或其子元素都会触发事件，所以有一个重复触发 | 是       | mouse     out | 先       |
| mouse enter | 只在父元素触发，当鼠标穿过一个元素时，只会触发一次。   | 否       | mouse  leave  | 后       |



<br>

## 跨域方法区别

同源是指"协议+域名（子域名和主域名）+端口"三者相同，即便两个不同域名指向同一个 ip 地址也非同源

|               方法                | 实现方式                                                     | 缺点                                     |
| :-------------------------------: | :----------------------------------------------------------- | ---------------------------------------- |
|             CROS跨域              | 后端设置跨域响应头`Access-Control-Allow-Origin`<br>该属性表示哪些域名可以访问资源，如果设置通配符则表示所有网站都可以访问资源。 | 发送请求时出现**简单请求**和**复杂请求** |
|             JSONP跨域             | 利用 script 标签没有跨域限制的漏洞，JSONP 请求一定需要对方的服务器做支持才可以 | 只支持GET请求<br>**可能会遭受 XSS 攻击** |
|           websocket跨域           | `socket.send(data)`<br>`socket.onmessage(data)`等等          | 需要浏览器支持HTML5                      |
|           HTML标签跨域            | <img src=''><br/><link href=''><br/><script src=''>          | 只支持跨域资源加载和jsonp                |
|      二级域名跨域（iframe）       | 两个不同子域名页面都通过 js 强制设置 document.domain 为基础主域，就实现了同域 | 只能用于二级域名相同的情况               |
|          postMessage跨域          | 发送`otherWindow.postMessage(message, targetOrigin, [transfer])`<br>接收`currentWindow.onmessage(message)`<br>可以实现页面和其打开的新窗口的数据传递、多窗口之间消息传递、页面与嵌套的 iframe 消息传递<br>**postMessage()方法允许来自不同源的脚本采用异步方式进行有限的通信，可以实现跨文本档、多窗口、跨域消息传递**。 | 需要浏览器支持HTML5                      |
| Node中间件代理跨域、Nginx反向代理 | 代理接收前端请求，再将请求转发到目标服务器，代理拿到数据再转发给前端 | 需要中间者（转发请求代理）               |
|      location.hash (iframe)       | a.html 欲与 c.html 跨域相互通信，通过中间页 b.html (a.html 和 b.html 是同域的)来实现。 三个页面，不同域之间利用 iframe 的 location.hash 传值，相同域之间直接 js 访问来通信(通过url后添加hash值传递内容) | 需要中间者（同域名页面）                 |
|        window.name(iframe)        | window.name 属性的独特之处：name 值在不同的页面（甚至不同域名）加载后依旧存在，并且可以支持非常长的 name 值（2MB）。 | 需要中间者（同域名页面）                 |

<br>

## Cookie、Session Storage、Local Storage、Session的区别

| 名称            | 存储地方 | 特性                                                         | 客户端可修改 | 操作api                                                      |
| --------------- | -------- | ------------------------------------------------------------ | ------------ | ------------------------------------------------------------ |
| Cookie          | 客户端   | 自动随请求头提交<br>同域名数据共享<br>https only数据不可获取<br>存储大小有限（最大 4kb )<br>存储内容只接受 String 类型 | 是           | document.cookie: 返回由key=value的拼接字符串<br>原生接口不友好，需要自己封装 |
| Local Storage   | 客户端   | 不随请求头提交<br>长期保存（不会自动清除）<br>同域名数据共享<br>存储空间（最大5MB) | 是           | sessionStorage.set(key,value)<br>sessionStorage.get(key)     |
| Session Storage | 客户端   | 不随请求头提交<br/>每个tab页面数据独立（即使同域名页面）<br>关闭tab页面自动清除 | 是           | localStorage.set(key,value)<br/>localStorage.get(key)        |
| Session         | 服务端   | 由后端服务器操作数据<br>安全性高<br>存储大小无限制           | 否           | 由后端语言决定                                               |

<br>

## 重绘、回流的区别

| 名称 | 概念                                                         | 如何触发                                                     |
| ---- | ------------------------------------------------------------ | ------------------------------------------------------------ |
| 重绘 | 当render tree中的一些元素需要更新属性<br>只是影响元素的外观，风格，而不会影响布局<br>（不会引起回流） | 改变元素颜色<br>改变元素背景色                               |
| 回流 | 当render tree中的一部分(或全部)因为元素<br>的规模尺寸，布局，隐藏等改变而需要重新构建<br>（必然会引起重绘） | 页面初次渲染<br>浏览器窗口大小改变<br>元素尺寸/位置/内容发生改变，比如文本变化或图片被另一个不同尺寸的图片所替代<br>元素字体大小变化<br>添加或者删除可见的 DOM 元素<br>激活 CSS 伪类（:hover……） |

#### 重绘属性：

color，border-style， visibility，text-decoration ，text-align，background ， background-image

background-position ，background-repeat , background-size，background-color，:hover

outline-color， outline ， outline -style ， outline-width ，box-shadow，opacity等

#### 回流属性：

width，height ，padding ，margin , display， border-width，border ，min-height

top，bottom，left，right，position，float ，clear

text-align，overflow-y，font-weight，overflow， font-family，line-height， vertival-vlign ，

white-space ，font-size等

现代的浏览器都是很聪明的，由于每次回流都会造成额外的计算消耗，因此大多数浏览器都会通过队列化修改并批量执行来优化重排过程。浏览器会将修改操作放入到队列里，直到过了一段时间或者操作达到了一个阈值，才清空队列。但当你获取布局信息的操作的时候，会强制队列刷新

以下属性和方法需要返回最新布局信息，因此浏览器不得不清空队列，触发回流重绘来返回正确的值

- offsetTop、offsetLeft、offsetWidth、offsetHeight
- scrollTop、scrollLeft、scrollWidth、scrollHeight
- clientTop、clientLeft、clientWidth、clientHeight
- getComputedStyle()
- getBoundingClientRect()

#### 如何减少触发重绘和回流

- 尽可能的减少DOM元素相互影响
- 避免设置内联样式
- 尽量简写CSS样式
- 删除复杂动画，尽量给动画元素设置position:fixed/absolute，使动画元素从DOM流中独立出来，从而减少对其他元素的影响。同时，尽量牺牲平滑度去满足性能，因为动画精度太强，会造成更多次的repaint/reflow
- 避免使用table进行布局：table的每个元素的大小以及内容的改动，都会导致整个table进行重新计算，造成大幅度的repaint或者reflow。改用div则可以进行针对性的repaint和避免不必要的reflow
- 避免在CSS中使用运算式：学习CSS的时候就知道，这个应该避免，不应该加深到这一层再去了解，因为这个的后果确实非常严重，一旦存在动画性的repaint/reflow，那么每一帧动画都会进行计算，性能消耗不容小觑。
- 减少DOM的层级，减少DOM的数量，DOM数量越少越好
- 慎改class！！去改子元素少的DOM的class
- 尽量采取批量更新元素样式的方式，比如可以将需要修改的样式集合放在一个class里，将这个class附给元素

<br>

## 前端性能优化渠道

| 名称             | 做法                                                         | 目的                                                   |
| ---------------- | ------------------------------------------------------------ | ------------------------------------------------------ |
| 浏览器缓存       | 强缓存(`expires/cache-control`)、协商缓存(`last-modified + if-modified-since`、`ETag+If-None-Match`) | 减少不必要的资源请求                                   |
| 资源打包压缩     | js、css、HTML等资源压缩                                      | 减小请求资源体积                                       |
| 图片图标资源优化 | 使用HTML元素的尺寸图片、使用雪碧图、使用字体图标（iconfont） | 减少请求数和请求时间                                   |
| CDN缓存资源      | 通过将静态资源(例如javascript，css，图片等等）缓存到离用户很近的相同网络运营商的CDN节点上 | 提升用户的访问速度，还能节省服务器的带宽消耗，降低负载 |
| 异步加载js代码   | script标签添加defer或async属性<br>没定义defer和async，异步加载的方式是动态创建script | 减少js阻塞渲染                                         |
| 预解析DNS        | 通过 DNS 预解析来告诉浏览器未来我们可能从某个特定的 URL 获取资源，当浏览器真正使用到该域中的某个资源时就可以尽快地完成 DNS 解析<br><link rel="dns-prefetch" href="//example.com"> | 提前减少资源加载时的DNS解析时间                        |
| 避免css表达式    | 避免css表达式                                                | 减少计算时间                                           |

<br>

## web安全问题对比

| 名称                 | 表现                                                         | 防御措施                                                     |
| -------------------- | ------------------------------------------------------------ | ------------------------------------------------------------ |
| SQL注入              | 后台人员使用用户输入的数据来组装SQL查询语句的时候不做防范， 遇到一些恶意的输入， 最后生成的SQL就会有问题。 | 加入过滤和验证机制                                           |
| XSS （跨站脚本攻击） | 通过代码注入的方式来达到攻击的目的                           | 字符转译<br>CSP(内容安全策略)                                |
| CSRF （跨站请求伪造) | 借用用户的身份或权限偷偷的完成某些操作，借助了 cookie 的特性，因为在其他域名的页面中，请求目标网站，就会带着目标网站的 cookie进行借用身份 | 加入各个层级的权限验证，检查请求头的refer地址                |
| 点击劫持             | 在某些操作的按钮上加一层透明的iframe，点击一下， 就入坑了    | 使用 HTTP 响应头属性防御（  X-Frame-Options 可以阻止嵌入网页的渲染。）<br>使用 Javascript 防御，判断顶层视口的域名是不是和本页面的域名一致 |
| 中间人攻击           | 通过拦截正常的网络通信数据，并进行数据篡改和嗅探来达到攻击的目的，而通信的双方却毫不知情 | 使用HTTPS<br>不要在公共Wi-Fi上发送敏感数据<br>不要点击恶意链接或电子邮件 |
| window.opener篡改    | 带有 target="_blank" 跳转的网页拥有了浏览器window.opener 对象赋予的对原网页的跳转权限，这可能会被恶意网站利用，例如一个恶意网站在某目标网站放了其恶意网址，该目标网站用户在新窗口打开页面时，恶意网站利用该漏洞将原目标网站跳转到伪造的钓鱼页面，用户返回到原窗口时可能会忽视浏览器 URL 已发生了变化，伪造页面即可进一步进行钓鱼或其他恶意行为 | 所有的外部链接都替换为内部的跳转连接服务，点击连接时，先跳到内部地址，再由服务器 redirect 到外部网址 |

<br>

## HTML的href和src区别

| 名称 | 含义                                                         |
| ---- | ------------------------------------------------------------ |
| href | （超文本引用）用来建立当前元素和文档之间的链接，在加载它的时候，不会停止对当前文档的处理，浏览器会继续往下走（页面会并行加载后续内容）<br>常用的有：link、a |
| src  | 表示引入内容是页面必不可少的一部分，src指向的内容会嵌入到文档中当前标签所在的位置。当浏览器解析到该元素时，会暂停浏览器的渲染，知道该资源加载完毕（浏览器需要加载完毕src的内容才会继续往下走。）<br/>常用的有：img、script、iframe |

<br>

## module.exports、exports、export、export default、import、require区别

| 名称           | 含义                                                         | 规范      | 用法                                         |
| -------------- | ------------------------------------------------------------ | --------- | -------------------------------------------- |
| module.exports | 模块导出                                                     | common.js | module.exports={x:xx}<br>module.exports.x=xx |
| exports        | 模块导出<br>（指向module.exports，不能直接将exports变量指向一个值，这样等于切断了exports与module.exports的联系） | common.js | exports.x=xxx                                |
| require        | 模块导入（导入名称随意）                                     | common.js | const x = require('文件')                    |
| export         | 单模块导出                                                   | ES6       | export xxx                                   |
| export default | 整体模块导出                                                 | ES6       | export default xxx                           |
| import         | 模块导入（导入名称与导出名称对应）                           | ES6       | import {x} from xxx<br/>import x from xxx    |



<br>

## offsetWidth、clientWidth、width、scrollWidth、clientX、screenX、offsetX、pageX区别

| 名称                         | 含义                                                         |
| :--------------------------- | ------------------------------------------------------------ |
| offsetWidth、offsetHeight    | 返回元素的宽高度**数值**（包括内容宽高、内边距和边框，**不包括外边距**） |
| clientWidth、clientHeight    | 返回元素的宽高度**数值**（包括内容宽高、内边距，**不包括边框和外边距**） |
| style.width、style.height    | 返回元素的宽高度**字符串**（包括内容宽高，**不包括内边距、边框和外边距**） |
| scrollWidth、scrollHeight    | 返回元素的宽高度**数值**（包括内容宽高、内边距和溢出尺寸，**不包括边框和外边距**），无溢出的情况，与clientWidth相同 |
| offsetTop、offsetLeft        | 返回元素的上外缘/左边缘距离最近采用定位父元素内壁的距离**数值**，如果父元素中没有采用定位的，则是获取上外边缘距离文档内壁的距离 |
| scrollTop、scrollLeft        | 此属性可以获取或者设置对象的最左边/顶边到对象在当前窗口显示的范围内的左边的距离，也就是元素被滚动条向左拉动/向下拉动的距离（网页被卷去的高、左距离） |
| event.clientX、event.clientY | 鼠标指针相对于浏览器（这里说的是浏览器的有效区域）左上角X、Y轴的坐标， **不随滚动条滚动而改变** |
| event.pageX、event.pageY     | 鼠标指针相对于浏览器（这里说的是浏览器的有效区域）左上角X、Y轴的坐标；  **随滚动条滚动而改变** |
| event.screenX、event.screenY | 鼠标指针相对于**显示器屏幕(包括浏览器工具栏之类)**左上角X、Y轴的坐标 |
| event.offsetX、event.offsetY | 鼠标指针相对于**当前事件绑定元素**左上角X、Y轴的坐标         |

![clientX-pageX.](/Volumes/个人/前端学习/前端学习对比手册（冯梓荣）/images/clientX-pageX..png)

<br>

## css各种元素居中方法区别总结

##### 垂直居中

| 名称         | 做法                                                       |
| ------------ | ---------------------------------------------------------- |
| 单行内联元素 | 父元素line-height：height                                  |
| 多行内联元素 | 父元素flex-direction + justify-content：center             |
|              | 父元素：table，子元素table-cell + vertical-align：middle   |
| 块级元素     | 父元素relative，子元素absolute+负margin：元素一半高度      |
|              | 父元素relative，子元素absolute+transform：translate(-50%） |
|              | 父元素flex+align-items（副轴居中）                         |
|              | 父元素表格<td>，子元素table-cell+vertical-align：middle    |



##### 水平居中

| 名称         | 做法                                                         |
| ------------ | ------------------------------------------------------------ |
| 行内元素     | 父元素text-align：center                                     |
| 块级元素     | 元素自身定宽且margin：0 auto                                 |
|              | 元素自身padding-left、padding-right左右相同距离              |
|              | 父元素relative，子元素absolute+transform：translateX（-50%） |
|              | 父元素text-align：center，子元素inline-block                 |
|              | 父元素flex+justify-content：center                           |
|              | 父元素flex+margin                                            |
|              | 子元素table+margin：0 auto                                   |
| 多块级元素   | 父元素flex+justify-content：center                           |
|              | 父元素text-align：center，子元素inline-block                 |
| 浮动元素     | 父元素flex+justify-content：center                           |
|              | 父元素relative + 子元素（定宽）absolute、负margin：自身元素一半 |
|              | 父元素relative + 子元素（定宽）absolute、transform：translateX（-50%） |
| 绝对定位元素 | 父元素relative，子元素absolute + margin：0 auto + left：0 + right：0 |
|              | 父元素relative，子元素absolute +transform：translate（-50%，-50%） |



##### 水平垂直居中

| 名称     | 做法                                                         |
| -------- | ------------------------------------------------------------ |
| 所有元素 | 父元素flex+justify-content+align-items                       |
|          | 父元素relative，子元素absolute+transform：translate(-50%,-50%) |
|          | 父元素relative，子元素absolute+负margin：自身的宽高度一半    |
|          | 父元素flex/grid，子元素margin：auto                          |
|          | 父元素relative，子元素absolute+margin：auto（已知高度宽度）  |

<br>



## Ajax的readyState状态码

| 状态码 | 含义                                               |
| ------ | -------------------------------------------------- |
| 0      | （未初始化）还没调用send方法                       |
| 1      | （载入）已经调用send方法，正在发送请求             |
| 2      | （载入完成）send方法执行完毕，已接收到全部响应内容 |
| 3      | （交互）正在解析响应内容                           |
| 4      | （完成）响应内容解析完成，可以在客户端调用内容     |

<br>



## 主流浏览器内核区别

| 浏览器                           | 内核渲染引擎                           |
| -------------------------------- | -------------------------------------- |
| Chrome（基于Chromium）           | Webkit（旧）<br>Blink（新）            |
| Safari                           | Webkit                                 |
| Firefox                          | Gecko                                  |
| IE                               | Trident                                |
| Microsoft Edge                   | edgeHTML                               |
| 新Microsoft Edge（基于Chromium） | Blink                                  |
| Opera（基于Chromium）            | Presto（旧）<br>Blink（新）            |
| 360浏览器、猎豹浏览器            | IE+Chrome双内核                        |
| 搜狗、遨游、QQ浏览器内核         | Trident（兼容模式）+Webkit（高速模式） |

<br>



## 双飞翼布局和圣杯布局区别

圣杯布局和双飞翼布局解决的问题是一样的，就是两边等宽，中间自适应的三栏布局，中间栏要在放在文档流前面以优先渲染，双飞翼布局比圣杯布局多创建了一个div，但不用相对布局了

| 名称       | 相同点                                                       | 不同点                                                       |
| ---------- | ------------------------------------------------------------ | ------------------------------------------------------------ |
| 圣杯布局   | 两边等宽，中间自适应的三栏布局<br>中间栏要在放在文档流前面以优先渲染 | 父元素padding左右预留子元素宽度，子元素浮动+负margin+相对定位relative实现 |
| 双飞翼布局 | 两边等宽，中间自适应的三栏布局<br/>中间栏要在放在文档流前面以优先渲染 | 使用一个容器包裹中间布局，中间布局margin左右两边，左右布局使用负margin即可 |

圣杯布局结构

```html
<header></header>
<section>
	<div class="middle">中</div>
  <div class="left">左</div>
  <div class="right">右</div>
</section>
<footer></footer>

<style>
  //三栏布局容器
  section{
		overflow: hidden;
    padding: 0 200px;
  }
  
  .middle{
    float:left;
		width:100%;
  }
  
  .left{
		float:left;
    width:200px;
    //关键
    margin-left: -100%;
    position: relative;
    left: -200px;
  }
  
  .right{
		float:left;
    width:200px;
    //关键
    margin-left: -200px;
    position: relative;
    right: -200px;
  }
</style>
```



双飞翼布局结构

```
<header></header>
<section class="middle">
  <div class="middle-inside">中</div>
</section>
<div class="left">左</div>
<div class="right">右</div>
<footer></footer>
 
 <style>
  //中间middle容器
  .middle{
		float: left;
    width: 100%;
  }
  
  .middle-inside{
   	margin: 0 200px;
  }
  
  .left{
		float: left;
    width: 200px;
    margin-left: -100%;
  }
  
  .right{
		float: left;
    width: 200px;
    margin-left: -200px;
  }
</style>
```



<br>

## 节流和防抖区别

| 名称 | 概念                                                         | 使用场景                                                     |
| ---- | ------------------------------------------------------------ | ------------------------------------------------------------ |
| 节流 | 面对高频触发，只有在大于等于指定时间时才会执行操作           | 窗口调整(resize)<br>页面滚动(scroll)<br/>抢购疯狂点击(movedown)<br/>滚动加载<br/>加载更多或滚到底部监听<br/>高频点击提交<br/>表单重复提交 |
| 防抖 | 面对高频触发不会执行操作，但当每次触发后超过指定时间才会执行操作 | 实时搜索(keyup)<br/>拖拽(mousemove)<br/>手机号、邮箱验证输入检测<br/>窗口大小Resize |

节流写法

```javascript
function throttle (handle, wait) {
        let lastTime = 0;
        return function (e) {
            let nowTime = new Date().getTime()
            if (nowTime - lastTime > wait) {
                handle();
                lastTime = nowTime;
            }
        }
    }
```



防抖写法

```javascript
 function debounce (handle, delay) {
        let time = null;
        return function () {
            let self = this,arg = arguments;
            clearTimeout(time);
            time = setTimeout(function () {
                handle.apply(self, arg);　　//this绑定
            }, delay)
        }
    }
```



## HTML5 主要新增标签、属性、特性

| 标签/属性/特性                 | 含义                                                       |
| ------------------------------ | ---------------------------------------------------------- |
| header标签                     | 头部                                                       |
| footer标签                     | 尾部                                                       |
| nav标签                        | 导航栏                                                     |
| section标签                    | 具体内容                                                   |
| article标签                    | 文章                                                       |
| aside标签                      | 内容侧边栏                                                 |
| video标签                      | 视频                                                       |
| audio标签                      | 音频                                                       |
| canvas标签                     | 画布                                                       |
| mark标签                       | 高亮引用文字                                               |
| time标签                       | 日期时间                                                   |
| figure标签                     | 包裹图像img标签                                            |
| figcaption标签                 | 添加标题，必须要放在figure标签里面                         |
| progress标签                   | 进度栏                                                     |
| meter标签                      | 刻度值，用于某些计量，例如温度、重量等                     |
| datalist标签                   | 用户会在他们输入数据时看到域定义选项的下拉列表             |
| <input type='email'/>          | 输入邮件类型                                               |
| <input type='url'/>            | 输入url地址类型                                            |
| <input type='number'/>         | 输入数字类型                                               |
| <input type='range'/>          | 滑动栏输入，并且可以设置最大以及最小值                     |
| <input type='date'/>           | 选取日、月、年                                             |
| <input type='month'/>          | 选取月、年                                                 |
| <input type='week'/>           | 选取周和年                                                 |
| <input type='time'/>           | 选取时间（小时和分钟）                                     |
| <input type='datetime-local'/> | 选取时间、日、月、年（本地时间）                           |
| <input type='search'/>         | 搜索框                                                     |
| <input type='color'/>          | 颜色输入                                                   |
| contenteditable="true"属性     | 使元素可以编辑，并且这个属性是可以继承的。                 |
| autocomplete属性               | 设置表单成功提交过的数据，下一次有提示(一般会关闭这个功能) |
| placeholder属性                | 提示信息                                                   |
| required属性                   | 是否必须填写                                               |
| pattern属性                    | 正则验证表单内容                                           |
| multiple属性                   | 输入框可以输入多个值，一般和email控件一起使用              |
| maxlength属性                  | 最大长度                                                   |
| minlength属性                  | 最小长度                                                   |
| step属性                       | 规定数字间隔                                               |
| hidden属性                     | 隐藏，填写了hidden属性的标签会被隐藏                       |
| draggable属性                  | 元素是否能被拖动                                           |
| autofocus属性                  | 在页面加载时，域自动获得焦点                               |
| **地理定位**                   | navigator.geolocation.getCurrentPosition((地址)=>{})       |
| **Web Worker**                 | 创建一个独立工作的线程，在主线程之外运行，不影响主进程工作 |
| **Web Storage**                | localStorage、sessionStorage、indexDB、webSQL              |
| **WebSocket**                  | 客户端和服务端之间提供了一种全双工通信机制                 |
| **History**                    | 历史记录管理api                                            |



## iframe和frame区别

| 名称                | 区别                                                         |
| ------------------- | ------------------------------------------------------------ |
| iframe              | 嵌套在frameSet中的iframe必需放在body中,不嵌套在frameSet中的iframe可以随意使用<br>高度可以自己控制，不能通过frameSet控制<br>可以放到表格里面<br>会阻塞主页面的onload事件（等iframe全部加载完才加载onload时间）<br>搜索引擎的检索程序无法解读这种页面，不利于SEO<br>和主页面共享连接池，而浏览器对相同域的连接有限制，会影响页面的并行加载 |
| frame（不推荐使用） | HTML5不支持<br>不能脱离frameSet单独使用<br>不能放在body中，否则不能正常显示<br>高度只能通过frameSet控制<br>不可以可以放到表格里面 |



## html5中可以省略结束标记的元素有

dd、dt、li、p、optgroup、option、rt、rp、thread、tfoot、tr、td、th



## img标签title和alt区别

| 名称                | 区别                                       |
| ------------------- | ------------------------------------------ |
| title               | 因为某种原因不能加载时在页面显示的提示信息 |
| frame（不推荐使用） | 因为某种原因不能加载时在页面显示的提示信息 |



## Flex布局父元素和子元素属性

父元素

| 属性            | 含义                         | 值                                                           |
| --------------- | ---------------------------- | ------------------------------------------------------------ |
| flex-deirection | 设置主轴方向                 | row（默认）<br />row-reverse<br />column<br />column-reverse |
| Flex-wrap       | 设置子项是否折叠             | nowrap（默认）<br />wrap<br />wrap-reverse                   |
| justify-content | 设置子项在主轴的对齐方式     | flex-start（默认）<br />flex-end<br />center<br />space-between<br />space-around<br />space-evenly |
| align-items     | 设置子项在副轴的对齐方式     | stretch（默认）<br />center<br />flex-start<br />flex-end<br />baseline |
| Align-content   | 设置多行子项在副轴的对齐方式 | stretch（默认）<br />flex-start<br />flex-end<br />center<br />space-between<br />space-around<br />space-evenly |



子元素

| 属性        | 含义                                                        | 值                                                           |
| ----------- | ----------------------------------------------------------- | ------------------------------------------------------------ |
| Flex-       | 以主轴排序，设置数值越小越靠前                              | 0（默认）<br />整数                                          |
| flex-shrink | 以主轴方向，设置子项目被挤压时的收缩比例                    | 1（默认）<br />数值                                          |
| flex-grow   | 以主轴方向，设置子项目在有剩余地方时的扩张比例              | 0（默认）<br />数值                                          |
| flex-basis  | 替代子项目的width属性                                       | auto（默认）<br />数值                                       |
| flex        | flex-grow，flex-shrink，flex-basis的缩写                    | none<br />auto<br />数值，数值，数值                         |
| align-self  | 覆盖父元素的align-items，可单独设置子项目在副轴上的对齐方式 | auto（默认）<br />stretch<br />center<br />flex-start<br />flex-end<br />baseline |



## Gird布局父元素和子元素属性

父元素

| 属性                                          | 含义                                                         | 值                                                           |
| --------------------------------------------- | ------------------------------------------------------------ | ------------------------------------------------------------ |
| grid-template-columns<br />grid-template-rows | 设置行高和列宽                                               | **数值**，如100px,100px,100px,100px<br />**百分比（总100%）**，如25% 25% 25% 25%<br />**repeat (重复个数, 重复值)**，如repeat(3 , 33%)，repeat(2, 100px 100px)<br />**fr**，如50px 3fr 1fr 2fr，结合px使用，剩余空间按照fr进行分配<br />**minmax(最小值, 最大值)**，如150px 1fr 1fr minmax(50px, 150px)，该列/行的大小会在剩余空间的长度范围内。<br />**auto**，如100px auto 130px 100px，由浏览器自己决定长度<br />**指定网格线名字**，如[c1] 100px [c2] 100px [c1] ，使用方括号，指定每一根网格线的名字，方便以后的引用 |
| grid-gap                                      | 设置行/列间距<br />**grid-row-gap** 属性、**grid-column-gap** 属性的简写 | 单位数值，如grid-row-gap:10px、 grid-column-gap:20px 等价于grid-gap:10px 20px（最新标准可去掉gird字符） |
| grid-template-areas                           | 定义区域                                                     | 字符串，<br />如 'a a a a '   <br />     'b b b b ' <br />     'd e . g '（如果某些区域不需要利用，则使用" . "表示） |
| grid-auto-flow                                | 设置放置顺序                                                 | row（默认）<br />column                                      |
| place-items                                   | 设置子项目水平和垂直位置<br />**justify-items（水平位置）** 属性、**align-items（垂直位置）** 属性的合并缩写 | start：对齐单元格的起始边缘<br />end：对齐单元格的结束边缘<br />center：单元格内部居中 <br />stretch：拉伸，项目大小没有指定时-占满单元格的整个宽度（默认值） |
| place-content                                 | 设置整个内容在容器中的位置                                   | start - 对齐容器的起始边框<br />end - 对齐容器的结束边框<br />center - 容器内部居中<br />stretch - 项目大小没有指定时，拉伸占据整个网格容器<br />space-around - 每个项目两侧的间隔相等。所以，项目之间的间隔比项目与容器边框的间隔大一倍<br />space-between - 项目与项目的间隔相等，项目与容器边框之间没有间隔<br />space-evenly - 项目与项目的间隔相等，项目与容器边框之间也是同样长度的间隔。 |
| grid-auto-columns<br />grid-auto-rows         | 设置超出部分单元格的大小                                     | 单位数值、百分比或网格可用空间的一部分（单位是fr）           |



子元素

| 属性                      | 含义                                                         | 值                                                           |
| ------------------------- | ------------------------------------------------------------ | ------------------------------------------------------------ |
| grid-column<br />grid-row | 设置项目在容器中的位置<br />grid-column是**grid-column-start**（左边框所在的垂直网格线）、grid-column-end（右边框所在的垂直网格线）的缩写<br />grid-row是**grid-row-start**（上边框所在的水平网格线）、**grid-row-end**（下边框所在的水平网格线）的缩写 | grid-column: 1 / 3;  <br /> grid-row: 1 / 2<br />等于<br />grid-column-start: 1;<br />grid-column-end: 3; <br />grid-row-start: 1; <br />grid-row-end: 2;            ——————————————— |
| grid-area                 | 设置项目在**容器**中的区域位置                               | 字符                                                         |
| place-self                | 设置项目**在单元格内的位置**，只作用于单个项目,能覆盖place-items的值 | start：对齐单元格的起始边缘<br />end：对齐单元格的结束边缘<br />center：单元格内部居中 <br />stretch：拉伸，项目大小没有指定时-占满单元格的整个宽度（默认值） |

