## 6.7 回顾: Web请求的历程
场景： 一名学生Bob将他的便携机与学校的以太网交换机相连，下载一个Web页面（比如www.google.com主页）
![Web请求的历程：网络环境和动作.png](https://upload-images.jianshu.io/upload_images/3515839-98a99aaf29d5de1a.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

### 6.7.1 准备： DHCP、UDP、IP 和 以太网
Bob的便携机所采取的一个网络相关的动作是运行DHCP协议，以从本地DHCP服务器获得一个IP地址及其他信息。

### 6.7.2 仍在准备： DNS 和 ARP
Bob的便携机需要知道www.google.com的IP地址，使用DNS协议提供域名到IP地址的转换服务。
Bob的便携机最终能够使包含DNS查询的以太网帧寻址到网关路由器的MAC地址。向交换机发送该帧，交换机将该帧交付给网关路由器。

### 6.7.3 仍在准备： 域内路由选择到 DNS 服务器
网关路由器接收该帧并抽取包含DNS 查询的IP 数据报。 
最终包含DNS查询的IP数据报到达DNS服务器。
Bob便携机从DNS报文抽取出服务器www.google.com的IP地址。完成准备工作。

### 6.7.4 Web客户 - 服务器交互： TCP 和 HTTP
Bob便携机利用www.google.com的IP地址，生成TCP套接字，该套接字将用于向www.google.com发送HTTP GET 报文。
当Bob生成套接字时，在Bob便携机中的TCP必须首先与www.google.com中的TCP执行三次握手。
Bob的浏览器生成包含要获取的URL的HTTP GET 报文，并向www.google.com发送该报文。
在www.google.com的HTTP服务器从TCP套接字读取HTTP GET报文，生成一个HTTP响应报文，将请求的Web页面的内容放入HTTP响应体中，并将报文发送进HTTP套接字中。
Bob的Web 浏览器程序从套接字中读取HTTP响应，从HTTP响应体中抽取Web网页的html,并显示该Web网页。
