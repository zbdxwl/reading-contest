## 2.1 应用层协议原理
研发网络应用程序的核心是写出能够运行在不同的终端系统并能通过网络彼此通信的程序。
***需要***编写在多台终端系统（end system）上运行的网络应用程序。
***不需要***编写写在网络核心（network core）设备如路由器或链路层交换机上运行的软件。

### 2.1.1 网络应用程序的体系结构（Architecture）
应用程序体系结构（applictation architecture）规定了如何在各种终端系统上组织该应用程序，两种主流体系结构：
  1. 客户端 - 服务器体系结构 （**client - server architecture**）
  2. P2P 体系结构 （**Peer-to-Peer architecture**）
![client-server and P2P architecture.png](https://upload-images.jianshu.io/upload_images/3515839-6b8f76e5066f64e1.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

### 2.1.2 进程通信
在两个不同的终端系统，通过跨越计算机网络来交换报文（message）进行相互通信。
1. 客户端和服务器端进程
网络应用程序由成对的进程组成，通常将发起通信的进行标识为客户端，将等待联系的进程标识为服务器，这些进程通过网络互相发送报文。

2. 进程与计算机网络之间的接口
进程通过一个称为套接字（socket）的软件接口向网络发送报文和从网络接收报文。
套接字是同一台主机内应用程序和运输层之间的接口。该套接字也成为应用程序和网络之间的应用程序编程接口（Application Programming Interface, API）

3. 进程寻址
在一台主机上的进程为了向另一台主机上运行的进程发送分组数据包，接收进程需要有一个唯一标识地址。
  - 主机由IP地址（IP address）标识
  - 接收进程由端口号（port number）来标识

常见的流行应用分配了特定的端口号：如Web服务器用端口号80来标识， 邮件服务应用（使用SMTP协议）用端口号25来标识。

### 2.1.3 可供应用程序使用的运输层服务
 1. 可靠数据传输
  确保有应用程序的一端发送的数据正确、完全地交付给应用程序的另一端。
  2. 吞吐量
  可用吞吐量就是发送进程能够向接收进程交付比特的速率。
  3. 时效性
   要求数据交付有严格的时间限制
  4. 安全性
  运输层协议为应用程序提供一种或多种安全性服务。例如，在发送主机中，运输协议能够加密由发送进程传输的所有数据，在接收主机中，运输层协议能够将解密数据并交付给接收进程。

### 2.1.4英特网提供的运输层服务
TCP/IP网络为应用程序提供了两个运输层协议，即TCP和UDP。
当编写网络应用程序时，首先要做出的决定是，选择TCP还是UDP作为传输层协议。

1. TCP服务
- 面向连接的服务：在应用层数据报文开始传输前，TCP让客户端和服务器相互交换运输层控制信息，这个过程称为握手。在握手阶段后，一个TCP连接就在两个进程的套接字之间建立了。
- 可靠数据传输服务：通信进程能够依靠TCP，无差错、按适当顺序交付所有发送的数据，不会有字节的丢失和冗余。
- 拥塞控制机制

2. UDP服务
UDP协议是无连接的，进程通信前没有握手过程。
UDP协议并不保证报文将送达接收进程，到达接收进程的报文也可能是乱序的。
UDP协议没有拥塞控制机制。

### 2.1.5 应用层协议
1. 公共开放协议（open protocols）
如 HTTP，SMTP，FTP等
2. 专有协议（proprietary protocol）
如 Skype应用所使用的协议

### 2.1.6 本书涉及的网络应用
本章主要讨论5种重要的应用： Web、电子邮件、目录服务（DNS）、流式视频、P2P