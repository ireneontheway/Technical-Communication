## API 相关的那些事儿 

### [什么是 SDK 和 API、RESTful API](https://blog.csdn.net/hjc1984117/article/details/77334616)

- API (Application Programming Interface) 应用程序编程接口 --- 买面包
- RESTful API (Representational State Transfer)：REST 风格的API。URL定位资源，用HTTP动词（GET,POST,DELETE,DETC）描述操作，资源在网络中以某种表现形式进行状态转移

- SDK (Software Development Kit) 软件开发工具包 --- 面包机和配料

sdk是整个开发工具包，api是sdk里一个一个的给你调用的方法。可以把SDK想象成一个虚拟的程序包，在这个程序包中有一份做好的软件功能，这份程序包几乎是全封闭的，只有一个小小接口可以联通外界，这个接口就是API。API＝SDK上唯一的接口。

**SDK和API都是服务的消费者，提供SDK和API的都是服务的提供者。**
信息化时代，为了让使用者高效的来使用厂商提供的功能、系统或平台，需要大量的API/SDK对接。

|      | 优势                                                         | 劣势                                           |
| ---- | ------------------------------------------------------------ | ---------------------------------------------- |
| API  | 开发成本低，对接比较简单，可以快速验证商业模式和用户体验     | 经过对接平台，厂商可以获取对接平台相关数据信息 |
| SDK  | 对接后的功能比较稳定，响应速度快，而且对接平台相关数据不会被获取 | 需要开发的环节较多，开发工作量大，对接周期略长 |

在当今的互联网应用的前端展示媒介很丰富。有手机、有平板电脑还有PC以及其他的展示媒介。那么这些前端接收到的用户请求统一由一个后台来处理并返回给不同的前端肯定是最科学和最经济的方式，RESTful API就是一套协议来规范多种形式的前端和同一个后台的交互方式。。资源是 REST 的基础，所有操作通过资源增删改查（POST\DELET\PUT\GET）实现。无状态。

POST/authorization 登录

DELET/authorization 登出

URL命名： /资源名称/{资源ID}/子资源名称/{子资源ID}

1. REST描述的是在网络中client和server的一种交互形式；REST本身不实用，实用的是如何设计 RESTful API（REST风格的网络接口）；

2. Server提供的RESTful API中，URL中只使用名词来指定资源，原则上不使用动词。“资源”是REST架构或者说整个网络处理的核心。

3. 用HTTP协议里的动词来实现资源的添加，修改，删除等操作。即通过HTTP动词来实现资源的状态扭转：
   GET 用来获取资源，
   POST 用来新建资源（也可以用于更新资源），
   PUT 用来更新资源，
   DELETE 用来删除资源。

4. Server和Client之间传递某资源的一个表现形式，比如用JSON，XML传输文本，或者用JPG，WebP传输图片等。当然还可以压缩HTTP传输时的数据（on-wire data compression）。
5. 用 HTTP Status Code传递Server的状态信息。比如最常用的 200 表示成功，500 表示Server内部错误等。

[OpenAPI 和 Swagger 是什么](https://www.breakyizhan.com/swagger/2806.html)

OpenAPI: 是REST API 的 API 描述格式

- 每个端点上的可用端点（/users）和操作（GET /users，POST /users）
- 操作参数每个操作的输入和输出
- 认证方法
- 联系信息，许可证，使用条款和其他信息。
- API规范可以用YAML或JSON编写。该格式对人和机器都很容易学习和阅读。

Swagger: Swagger是一套围绕OpenAPI规范构建的开源工具，可以帮助您设计，构建，编写和使用REST API。

- Swagger编辑器 - 基于浏览器的编辑器，您可以在其中编写OpenAPI规范。
- Swagger UI - 将OpenAPI规范呈现为交互式API文档。
- Swagger Codegen - 根据OpenAPI规范生成服务器存根和客户端库。

设计优先用户：

- 使用Swagger Codegen为您的API生成**服务器存根**。剩下的唯一事情就是实现服务器逻辑 - 而且你的API已经准备好了！
- 使用Swagger Codegen以**超过40种语言**为您的API生成客户端库。
- 使用Swagger UI生成交互式API文档，让用户**直接在浏览器中**尝试API调用。
- 使用该规范将API相关工具**连接到您的API**。例如，将规范导入到SoapUI来为您的API创建自动化测试。
  查看与Swagger集成的开源和商业工具。

![API](https://github.com/ireneontheway/Technical_Communication/blob/master/Picture/API.png)

> 版权声明： 本文资源均来自网络，仅为个人学习所用，如需转载请联系我并标明来源。
