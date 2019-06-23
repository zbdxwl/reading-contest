## 3.5 面向连接的运输：TCP
TCP是英特网运输层的面向连接的可靠的运输协议。
TCP定义在 RFC 793、RFC 1122、RFC 1323、RFC 2018 以及 RFC 2581中。

### 3.5.1 TCP 连接
TCP被称为是**面向连接的**（connection-oriented），这是因为在一个应用进程可以开始向另一个应用进程发送数据之前，这两个进程必须先相互“握手”，即它们必须相互发送某些预备报文段，以建立确保数据传输的参数。

中间路由器对TCP连接完全视而不见，它们看到的是数据报，而不是连接。

TCP连接提供的是**全双工服务**（full-duplex service）。TCP连接也总是**点对点**（point-to-point）的，即在单个发送方和单个接收方之间的连接。

TCP为每块客户数据配上一个TCP首部，从而形成多个**TCP报文段**（TCP segment）。

TCP的连接的组成包括：一台主机上的缓存、变量和与进程连接的套接字，以及另一台主机上的另一种缓存、变量和与进程连接的套接字。

### 3.5.2 TCP 报文段结构
TCP报文段由首部字段和一个数据字段组成。

![TCP segment structure.png](https://upload-images.jianshu.io/upload_images/3515839-d628b519aa3b117b.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)


### 3.5.4 可靠数据传输
TCP 在 IP 不可靠的尽力而为服务之上创建了一种**可靠数据传输服务**（reliable transfer service）。TCP的可靠数据传输服务确保了一个进程从其接收缓存中读出的数据流是无损坏、无间隙、非冗余和按序的数据流，即该字节流与连接的另一端系统发送出的字节流是完全相同的。

### 3.5.5 流量控制
TCP 为它的应用程序提供**流量控制服务**（flow-control service），以消除发送方使接收方缓存移除的可能性。
流量控制是一个速度匹配服务，即发送方的发送速率与接收方应用程序的读取速率相匹配。
TCP 通过让发送方维护一个称为**接收窗口**（receive window）的变量来提供流量控制。通俗地说，接收窗口用于给发送方一个指示-该接收方还有多少可用的缓存空间。

TCP发送方也可能应为IP网络的拥塞而被遏制，这种形式的发送方控制被称为**拥塞控制**（congestion control）。

### 3.5.6 TCP 连接管理
客户端的TCP应用会用以下方式与服务器中的TCP建立一条TCP连接：
第一步：客户端的TCP首先向服务器端的TCP发送一个特殊的报文段（SYN 报文段）。
第二步：服务器从数据报中提取出TCP SYN 报文段，为该TCP连接分配缓存和变量，并向该客户TCP发送允许连接的报文段（SYNACK 报文段）。
第三步：在收到SYNACK 报文段后，客户端也要给该连接分配缓存和变量。客户主机向服务器发送另外一个报文段。
一旦完成这3个步骤，客户和服务器主机就可以相互发送包含数据的报文段了。
为了创建TCP连接，在两台主机之间发送了3个packet，这种连接创建过程通常被称为3次握手（three-way handshake）。

TCP连接关闭方法：
参与一条TCP连接的两个进程中的任何一个都能终止该连接。当连接关闭后，注解中的“资源”（即缓存和变量）将被释放。

在一个TCP连接的生命周期内，运行在每台主机中的TCP协议在各种TCP状态（TCP state）之间变迁。
![A typical sequence of TCP states visited by a client TCP.png](https://upload-images.jianshu.io/upload_images/3515839-6ea6fae087cb941f.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

![A typical sequence of TCP states visited by a server-side TCP.png](https://upload-images.jianshu.io/upload_images/3515839-acd9d3455e375afb.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)




