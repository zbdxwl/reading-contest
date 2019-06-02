## 2.2 Web 和 HTTP
### 2.2.1 HTTP概况
Web的应用层协议是超文本传输协议（HyperText Transfer Protocol，HTTP）。
HTTP使用TCP作为它的运输层协议，TCP为HTTP提供可靠的数据传输服务。
HTTP是一个无状态的协议（stateless protocol）, HTTP服务器并不保存客户的任何信息。

### 2.2.2 非持续连接和持续连接
在许多网络应用程序中，客户和服务器在一个相当长的时间范围内通信，客户发出一系列的请求并且服务器对每个请求进行响应。
 - 非持续连接（non-persistent connection）: 每个请求/响应是经各自单独的TCP连接发送。
 - 持续连接（persistent connection）：所有的请求极其响应都是经相同的TCP连接发送。
HTTP在其默认方式下使用持续连接

### 2.2.3HTTP 报文格式
HTTP报文有两种：请求报文和响应报文
1.HTTP请求报文
HTTP请求报文的第一行叫请求行( request line )，紧接着是多个首部行（header line）
注：根据请求方法不同，决定请求报文中是否包含实体体（entity body）, GET请求方法没有实体体，POST请求方法则包含实体体。
![HTTP request message.png](https://upload-images.jianshu.io/upload_images/3515839-d3bfb60b0b0720fa.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

2. HTTP响应报文
HTTP响应报文包含3个部分：第一行是响应状态行（status line）, 紧接着是多少个首部行（header line）, 然后是实体体（entity body）,实体体即为响应内容。
![HTTP response message.png](https://upload-images.jianshu.io/upload_images/3515839-0710dbf76dc9b9f2.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

### 2.2.4 用户与服务器的交互：cookie
cookie允许站点对用户进行跟踪。
cookie可以在无状态的HTTP之上建立一个用户会话层。
cookie技术中有4个组件：
 1. 在HTTP响应报文中的一个cookie首部行
 2. 在HTTP请求报文中的一个cookie首部行
 3. 在用户终端系统中保留一个cookie文件，并由用户的浏览器进行管理
 4. 位于Web站点的一个后端数据库。
![Keeping user state with cookies.png](https://upload-images.jianshu.io/upload_images/3515839-149aa20c933bf888.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)


### 2.2.5 Web 缓存
Web缓存器（Web cache）也叫代理服务器（proxy server）。
Web缓存器有自己的磁盘存储空间，并在其中保存最近请求过的对象的副本。
Web缓存器可以大大减少对客户端请求的响应时间。
Ｗeb缓存器能大大减少一个机构的接入链路到英特网的通信量。
![Adding a cache to the institutional network.png](https://upload-images.jianshu.io/upload_images/3515839-f6d1f7d721c253d7.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)


## 2.3 英特网中的电子邮件
电子邮件是一种一部通信媒介，英特网电子邮件系统主要包含3个组成部分：
 1. 用户代理（user agent）
 2. 邮件服务器（mail server）
 3. 简单邮件传输协议（Simple Mail Transfer Protocol, SMTP）

### 2.3.1 SMTP
SMTP 是英特网电子邮件中主要的应用层协议，它使用TCP可靠数据传输服务，从发送方的邮件服务器向接收方邮件服务器发送邮件。
由于历史遗留技术的原因，SMTP限制所有邮件报文的体部分只能采用简单的7bit ASCII表示。

### 2.3.2 与HTTP的对比
HTTP主要是一个拉协议（pull protocol），TCP连接是由想要接收文件的机器发起的。
SMTP则是一个推协议（push protocol）, TCP连接是由要发送文件的机器发起的。

### 2.3.3 邮件报文格式
首部行
空行
报文体（ASCII格式表示的）

### 2.3.4 邮件访问协议
为解决收件人的用户代理从邮件服务器获取邮件内容的问题，引入了特殊的邮件访问协议，如 POP3， IAMP， HTTP
![E-mail protocols.png](https://upload-images.jianshu.io/upload_images/3515839-a1de55179cc846fb.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)


## 2.4 DNS : 英特网的目录服务
英特网上的主机由多种标识方法，一种标识方法是主机名（hostname）, 如www.google.com. 另一种标识方法是使用IP地址（IP address）进行标识。
人们喜欢便于记忆的主机标识方式，而路由器则喜欢定长的、有着层次结构的IP地址。因此需要一种能进行主机名到IP地址转换的目录服务。
域名系统（Domain Name System，DNS）提供了这种服务。
DNS是：
  1. 一个由分层的DNS服务器（DNS server）实现的分布式数据库
  2. 一个使得主机能够查询分布式数据库的应用层协议。

DNS服务器通常是运行BIND(Berkeley Internet Name Domain) 软件的UNIX机器。
DNS协议运行在UDP运输层协议之上，使用53号端口号。
![Hierarchy of DNS servers.png](https://upload-images.jianshu.io/upload_images/3515839-8a32a12c34bdf607.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)


## 2.5 P2P 应用
使用 P2P 体系结构，对总是打开的基础设施服务器有最小（或者没有）依赖，成对间歇性连接的主机（称为对等方）彼此直接通信。
在 P2P 文件分发中，每个对等方能够向任何其他对等方重新分发他已经收到的该文件的任何部分，从而在分发过程中协助该服务器。
目前，最为流行的P2P文件分发协议是BitTorrent。

![File distribution with BitTorrent.png](https://upload-images.jianshu.io/upload_images/3515839-edc74bf19f980022.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

在文件分发环境中的P2P体系结构具有自扩展性。


### 2.6.3 内容分发网（CDN）
为了应对向分布于全世界的用户分发巨量视频数据的挑战，几乎所有主要的视频流公司都利用内容分发网（Contenet Distribution Network, CDN）.
CDN管理分布在多个地理位置上的服务器，在他的服务器中存储视频的副本，并且试图将每个用户请求定向到一个能提供最好用户体验的CDN位置。
CDN分类：
  1. 专用CDN（private CDN）
  2. 第三方CDN（third-party CDN）

CDN 通常采用两种不同的服务器安置原则：
  - Enter Deep
  - Bring Home

大多数CDN利用DNS截获和重定向请求。



