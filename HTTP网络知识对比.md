## HTTP1.0、1.1、2.0区别

| 版本     | 特性                                                         |
| -------- | ------------------------------------------------------------ |
| HTTP 1.0 | 1、使用header里的**If-Modified-Since,Expires**来做为缓存判断的标准<br>2、**不支持断点续传功能**（部分内容传输）<br>3、请求消息中的URL并**没有传递主机名**（hostname）<br>4、只支持GET HEAD POST |
| HTTP 1.1 | 1、**支持长连接和请求的流水线处理，连接可以复用**，在一个TCP连接上可以传送多个HTTP请求和响应，减少了建立和关闭连接的消耗和延迟，默认开启Connection： keep-alive，一定程度上弥补了HTTP1.0每次请求都要创建连接的缺点<br>2、引入了**更多的缓存控制策略**例如Entity tag，If-Unmodified-Since, If-Match, If-None-Match等更多可供选择的缓存头来控制缓存策略<br>3、**请求头引入了range头域**，它允许只请求资源的某个部分，即返回码是206（Partial Content）<br>4、**新增了24个错误状态响应码**<br>5、**请求消息和响应消息都应支持Host头域**，且请求消息中如果没有Host头域会报告一个错误（400 Bad Request）<br>6、支持OPTIONS，PUT，DELETE，TRACE，CONNECT请求方式 |
| HTTP 2.0 | 1、**新的二进制格式**，HTTP1.x的解析是基于文本。基于文本协议的格式解析存在天然缺陷，文本的表现形式有多样性，要做到健壮性考虑的场景必然很多，二进制则不同，只认0和1的组合。基于这种考虑HTTP2.0的协议解析决定采用二进制格式，实现方便且健壮。<br>2、**多路复用**，即连接共享，即每一个request都是是用作连接共享机制的。一个request对应一个id，这样一个连接上可以有多个request，每个连接的request可以随机的混杂在一起，接收方可以根据request的 id将request再归属到各自不同的服务端请求里面。<br>3、**header压缩**，如上文中所言，对前面提到过HTTP1.x的header带有大量信息，而且每次都要重复发送，HTTP2.0使用encoder来减少需要传输的header大小，通讯双方各自cache一份header fields表，既避免了重复header的传输，又减小了需要传输的大小。<br>4、**服务端推送**，同SPDY一样，HTTP2.0也具有server push功能。<br> |

<br>

## HTTP2.0多路复用、HTTP1.x长连接区别

| 名称            | 区别                                                         |
| --------------- | ------------------------------------------------------------ |
| HTTP1.x长连接   | 打开一次tcp连接，请求就复用此连接，但是得排队，若干个请求排队串行化单线程处理，后面的请求等待前面请求的返回才能获得执行机会，一旦有某请求超时等，后续请求只能被阻塞，毫无办法，也就是人们常说的线头阻塞。<br>**减少TCP连接耗时** |
| HTTP2.0多路复用 | 打开一次tcp连接，请求就复用此连接，不同排队，多个请求可同时在一个连接上并行执行。某个请求任务耗时严重，不会影响到其它连接的正常执行<br>**减少TCP连接耗时，优化请求阻塞情况** |

![区别图](/Users/feziro/Desktop/前端学习对比手册/images/http长连接和多路复用区别.png)

<br>

## HTTP状态码区别

| 状态码类别 | 具体状态码                                                   |
| ---------- | ------------------------------------------------------------ |
| 100        | <u>**100 Continue**</u>  <br/>表示目前为止一切正常, 客户端应该继续请求, 如果已完成请求则忽略 <br><u>**101 Switching Protocol**</u>  <br/>表示服务器应客户端升级协议的请求（`Upgrade`请求头）正在进行协议切换 |
| 200        | <u>**200 OK**</u> <br/>请求已经成功，默认情况下状态码为200的响应可以被缓存<br/><u>**201 Created**</u>  <br/>表示请求已经被成功处理，并且创建了新的资源<br><u>**202 Accepted**</u> <br/>表示服务器端已经收到请求消息，但是尚未进行处理<br/><u>**203 Non-Authoritative Information**</u>  <br/>表示请求已经成功被响应，但是获得的负载与源头服务器的状态码为 200的响应相比，经过了拥有转换功能的 代理服务器的修改<br/><u>**204 No Content**</u>  <br/>成功状态响应码，表示该请求已经成功了，但是客户端客户不需要离开当前页面。默认情况下 204 响应是可缓存的。一个 ETag标头包含在此类响应中<br/><u>**205 Reset Content**</u> <br/>用来通知客户端重置文档视图，比如清空表单内容、重置 canvas 状态或者刷新用户界面。<br/><u>**206 Partial Content**</u> <br/>成功状态响应代码表示请求已成功，并且主体包含所请求的数据区间，该数据区间是在请求的 Range首部指定的。 |
| 300        | <u>**300 Multiple Choices**</u> <br/>表示该请求拥有多种可能的响应<br/><u>**301 Moved Permanently (永久重定向)**</u> <br/>说明请求的资源已经被移动到了由 Location 头部指定的url上，是固定的不会再改变。搜索引擎会根据该响应修正，*请求方法有时候会被客户端错误地修改为 GET 方法*<br/><u>**302 Found （临时重定向）**</u> <br/>表明请求的资源被暂时的移动到了由Location 头部指定的 URL 上。浏览器会重定向到这个URL， 但是搜索引擎不会对该资源的链接进行更新，*请求方法有时候会被客户端错误地修改为 GET方法*<br/><u>**303 See Other**</u><br/>通常作为 PUT或 POST 操作的返回结果，它表示重定向链接指向的不是新上传的资源，而是另外一个页面，比如消息确认页面或上传进度页面。而请求重定向页面的方法要总是使用 GET<br/><u>**304 Not Modified**</u> <br/>说明无需再次传输请求的内容，可以使用缓存的内容<br/><u>**307 Temporary Redirect（临时重定向）<br/>**</u>是表示重定向的响应状态码，说明请求的资源暂时地被移动到  Location 之间的唯一区别在于，当发送重定向请求的时候，*可以确保请求方法和消息主体不会发生变化。*<br/><u>**308 Permanent Redirect（永久重定向）<br/>**</u>是表示重定向的响应状态码，说明请求的资源已经被永久的移动到了由 Location首部指定的 URL 上。浏览器会进行重定向，同时搜索引擎也会更新其链接，<u>可以确保请求方法和消息主体不会发生改变 |
| 400        | <u>**400 Bad Request**</u> <br>表示由于语法无效，服务器无法理解该请求。 客户端不应该在未经修改的情况下重复此请求。<br/><u>**401 Unauthorized**</u> <br>代表客户端错误，指的是由于缺乏目标资源要求的身份验证凭证，发送的请求未得到满足。<br/><u>**402 Payment Required**</u> <br/>（实验功能）是一个被保留使用的非标准客户端错误状态响应码<br/><u>**403 Forbidden**</u> <br/>代表客户端错误，指的是服务器端有能力处理该请求，但是拒绝授权访问。<br/><u>**404 Not Found**</u> <br/>代表客户端错误，指的是服务器端无法找到所请求的资源，不能说明请求的资源是临时还是永久丢失。如果服务器知道该资源是永久丢失，那么应该返回 [`410`](https://developer.mozilla.org/zh-CN/docs/Web/HTTP/Status/410) (Gone) 而不是 404<br/><u>**405 Method Not Allowed**</u> <br/>表明服务器禁止了使用当前 HTTP 方法的请求<br/><u>**406 Not Acceptable**</u> <br/>状态码表示客户端错误，指代服务器端无法提供与 Accept-Charset 以及 Accept-Language消息头指定的值相匹配的响应。<br/><u>**407 Proxy Authentication Required**</u><br/>代表客户端错误，指的是由于缺乏位于浏览器与可以访问所请求资源的服务器之间的代理服务器proxy server要求的身份验证凭证，发送的请求尚未得到满足。<br/><u>**408 Request Timeout**</u> <br/>表示服务器想要将没有在使用的连接关闭。一些服务器会在空闲连接上发送此信息，即便是在客户端没有发送任何请求的情况下。<br/><u>**409 Conflict**</u> <br/>表示请求与服务器端目标资源的当前状态相冲突。<br/><u>**410 gone（丢失）**</u> <br/>说明请求的内容在服务器上不存在了，同时是永久性的丢失。如果不清楚是否为永久或临时的丢失，应该使用404<br/><u>**411 Length Required**</u> <br/>属于客户端错误，表示由于缺少确定的Content-Length首部字段，服务器拒绝客户端的请求。<br/><u>**412 Precondition Failed**</u><br/>（先决条件失败）表示客户端错误，意味着对于目标资源的访问请求被拒绝。这通常发生于采用除 GET和 HEAD 之外的方法进行条件请求时，由首部字段 if-Unmodified-Since或 If-None-Match规定的先决条件不成立的情况下。这时候，请求的操作——通常是上传或修改文件——无法执行，从而返回该错误状态码。<br/><u>**414 URI Too Long**</u> <br/>表示客户端所请求的 URI 超过了服务器允许的范围。<br/><u>**415 Unsupported Media Type**</u><br/>是一种HTTP协议的错误状态代码，表示服务器由于不支持其有效载荷的格式，从而拒绝接受客户端的请求。<br/><u>**416 Range Not Satisfiable**</u> <br/>错误状态码意味着服务器无法处理所请求的数据区间。最常见的情况是所请求的数据区间不在文件范围之内，也就是说，Range首部的值，虽然从语法上来说是没问题的，但是从语义上来说却没有意义。<br/><u>**417 Expectation Failed**</u> <br/>状态码表示客户端错误，意味着服务器无法满足 Expect请求消息头中的期望条件。<br/><u>**425 Too Early**</u> <br/>代表服务器不愿意冒风险来处理该请求，原因是处理该请求可能会被“重放”，从而造成潜在的重放攻击<br/><u>**426 Upgrade Required**</u> <br/>是一种HTTP协议的错误状态代码，表示服务器拒绝处理客户端使用当前协议发送的请求，但是可以接受其使用升级后的协议发送的请求<br/><u>**428 Precondition Required**</u> <br/>表示服务器端要求发送条件请求。<br/><u>**429 Too Many Requests**</u><br/>表示在一定的时间内用户发送了太多的请求，即超出了“频次限制”。<br><u>**431 Request Header Fields Too Large**</u><br/>表示由于请求中的首部字段的值过大，服务器拒绝接受客户端的请求。客户端可以在缩减首部字段的体积后再次发送请求<br><u>**451 Unavailable For Legal Reasons （因法律原因不可用）<br/>**</u>是一种HTTP协议的错误状态代码，表示服务器由于法律原因，无法提供客户端请求的资源，例如可能会导致法律诉讼的页面。 |
| 500        | <u>**500 Internal Server Error**</u>  <br/>意味着所请求的服务器遇到意外的情况并阻止其执行请求。<br/><u>**501 Not Implemented**</u> <br/>服务器错误响应码表示请求的方法不被服务器支持，因此无法被处理，响应默认是可缓存的<br/><u>**502 Bad Gateway**</u> <br/>它表示作为网关或代理角色的服务器，从上游服务器（如tomcat、php-fpm）中接收到的响应是无效的<br/><u>**503 Service Unavailable**</u> <br/>它表示服务器尚未处于可以接受请求的状态。<br/><u>**504 Gateway Timeout**</u> <br/>表示扮演网关或者代理的服务器无法在规定的时间内获得想要的响应<br/><u>**505 HTTP Version Not Supported**</u> <br/>表示服务器不支持请求所使用的 HTTP 版本<br/><u>**506 Variant Also Negotiates**</u> <br/>响应状态码可以在TCN（透明内容协商，见RF2295）上下文给出。TCN协议允许客户端取回给定资源的最佳变量/变元，这里服务器支持多个变量/变元。<br/><u>**507 Insufficient Storage**</u> <br/>响应状态码 可以在WebDAV协议（基于web的分布式创作和版本控制，参见[RFC 4918](https://tools.ietf.org/html/rfc4918)）中给出。<br/><u>**508 Loop Detected**</u> <br/>状态码可以在WebDAV协议（基于Web的分布式创作和版本控制）中给出，表示服务器中断一个操作<br/><u>**510 Not Extended**</u> <br/>响应状态码在HTTP扩展框架协议（参见[RFC 2774](https://tools.ietf.org/html/rfc2774)）中发送。<br/><u>**511 Network Authentication Required**</u> <br/>表示客户端需要通过验证才能使用该网络。该状态码不是由源头服务器生成的，而是由控制网络访问的拦截代理服务器生成的。 |

<br>

## HTTP请求头区别

幂等性：连续调用一次或者多次的效果相同（无副作用）

安全性：这里指的安全指的是不会修改服务器数据、对服务器只读操作的方法（不是加密传输）。

| 请求头  | 含义                                                         |
| ------- | ------------------------------------------------------------ |
| CONNECT | **可以开启一个客户端与所请求资源之间的双向沟通的通道。它可以用来创建隧道（tunnel），可以用来访问采用了SSL（HTTPS） 协议的站点**<br>请求主体 NO<br>响应主体 YES<br>安全性 NO<br/>幂等性 NO<br/>可缓存 NO<br/>HTML 表单支持  NO |
| DELETE  | **用于删除指定的资源，可能返回的状态码200，202，204**<br>请求主体 May 可以有<br/>响应主体 May 可以有<br/>安全性 NO<br/>幂等性 YSE<br/>可缓存 NO<br/>HTML 表单支持  NO |
| GET     | **用于求指定的资源**<br>请求主体 NO<br/>响应主体 YES<br/>安全性 YES<br/>幂等性 YES<br/>可缓存 YES<br/>HTML 表单支持 YES |
| POST    | **发送数据给服务器. 请求主体的类型由 Content-Type首部指定**<br>请求主体 YES<br/>响应主体 YES<br/>安全性 NO<br/>幂等性 NO<br/>可缓存 只有是新鲜的信息才可被缓存<br/>HTML 表单支持  YES |
| OPTIONS | **用于获取目的资源所支持的通信选项**<br>请求主体 NO<br/>响应主体 NO<br/>安全性 YES<br/>幂等性 YES<br/>可缓存 NO<br/>HTML 表单支持  NO |
| PATCH   | **用于对资源进行部分修改**<br>请求主体 YES<br/>响应主体 NO<br/>安全性 NO<br/>幂等性 NO<br/>可缓存 NO<br/>HTML 表单支持  NO |
| PUT     | **用于整体替换目标资源**<br>请求主体 YES<br/>响应主体 NO<br/>安全性 NO<br/>幂等性 YES<br/>可缓存 NO<br/>HTML 表单支持  NO |
| TRACE   | **实现沿通向目标资源的路径的消息环回（loop-back）测试 ，提供了一种实用的 debug 机制**<br>请求主体 NO<br/>响应主体 NO<br/>安全性 NO<br/>幂等性 YES<br/>可缓存 NO<br/>HTML 表单支持  NO |
| HEAD    | **请求资源的头部信息, 并且这些头部与 HTTP GET方法请求时返回的一致. 该请求方法的一个使用场景是在下载一个大文件前先获取其大小再决定是否要下载, 以此可以节约带宽资源**<br>请求主体 NO<br/>响应主体 NO<br/>安全性 YES<br/>幂等性 YES<br/>可缓存 YES<br/>HTML 表单支持  NO |

<br>

## POST请求主体格式区别

| 格式                              | 区别                                                         |
| --------------------------------- | ------------------------------------------------------------ |
| application/x-www-form-urlencoded | **浏览器默认的编码格式，将键值对的参数用&连接起来，如果有空格，将空格转换为`+`加号；有特殊符号，将特殊符号转换为`ASCII HEX`值，只适合传输键值对参数，不支持二进制数据** |
| multipart/form-data               | **不会对参数编码，使用的`boundary`(分割线)，相当于`&`，`boundary`的值是`----Web\**AJv3，适合用于上传文件（二进制数据）和键值对参数`** |

<br>

## DNS的迭代查询、递归查询区别

| 名称     | 概念                                                         | 途径                                |
| -------- | ------------------------------------------------------------ | ----------------------------------- |
| 递归查询 | 用户只向本地DNS服务器发出请求，然后等待肯定或否定答案        | 用户 -> 本地DNS服务器查询           |
| 迭代查询 | （反复查询）本地服务器向根DNS服务器发出请求，而根DNS服务器只是给出下一级DNS服务器的地址，然后本地DNS服务器再向下一级DNS发送查询请求直至得到最终答案 | 本地DNS服务器 -> 各种域名服务器查询 |

<br>

## TCP、UDP区别

|              | TCP                                    | UDP                                        |
| ------------ | -------------------------------------- | ------------------------------------------ |
| 是否连接     | 面向连接                               | 无连接                                     |
| 是否可靠     | 可靠传输，使用流量控制和拥塞控制       | 不可靠传输，不使用流量控制和拥塞控制       |
| 连接对象个数 | 只能是一对一通信                       | 支持一对一，一对多，多对一和多对多交互通信 |
| 传输方式     | 面向字节流                             | 面向报文                                   |
| 首部开销     | 首部最小20字节，最大60字节             | 首部开销小，仅8字节                        |
| 适用场景     | 适用于要求可靠传输的应用，例如文件传输 | 适用于实时应用（IP电话、视频会议、直播等） |

**问：为什么 TCP 建立连接需要三次握手，而不是两次？**

答：1、为了防止出现失效的连接请求报文段被服务端接收的情况，从而产生错误。

​		2、为了确保在请求发送前让双方都知道彼此的发送和接收功能都正常。

<br>

**问：为什么 TCP 关闭连接需要四次握手？**

答：1、为了防止在客户端发送关闭信号的时候后端仍然存在未发送完毕的数据。

​		2、为了确保服务端在准备好关闭的情况下关闭连接，避免发生错误。

<br><br>


## OSI七层网络模型对比图

"如图片无法加载请在images文件夹下查看"
![](/Users/feziro/Desktop/前端学习对比手册（冯梓荣）的副本/images/OSI七层网络模型对比图.png)