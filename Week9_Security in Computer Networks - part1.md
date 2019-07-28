## 8.1 什么是网络安全
安全通信（secure communication）具有下列所需要的特性
- 机密性（confidentiality）
仅有发送方和希望的接收方能够理解传输报文的内容。这必须要求报文在一定程度上加密，使被截取的报文无法被窃听者理解。
- 报文完整性（message integrity）
确保通信的内容在传输过程中未被改变 - 或者恶意篡改或者意外改动。
- 端点鉴别（end-point authenticaiton）
发送方和接收方都应该能证实通信过程所涉及的另一方，以确信通信的另一方具有其所声称的身份。
- 运行安全性（operational security）
诸如防火墙和入侵检测系统等运行设备被用于对机构网络的攻击。

## 8.2 密码学的原则
密码学已经成为网络安全的基石
![密码学组件.png](https://upload-images.jianshu.io/upload_images/3515839-b29c9952b3884667.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

报文的最初形式成为明文（plaintext）。
使用加密算法（encryption algorithm）加密其明文报文，生成的加密报文成为密文（ciphertext）
Alice提供一个密钥（key）KA, 加密算法以密钥和明文m为输入，生成的密文作为输出。
Bob提供密钥KB，解密算法（decryption algorithm）将密文和密钥作为输入，输出原始明文。
密钥系统可分为：
- 对称密钥系统（symmetric key system）
- 公开密钥系统（public key system）

## 8.3 报文完整性和数字签名
报文完整性（message integrity）问题在所有安全网络协议中都是至关重要的。
假定Bob接收到一个报文，并且他认为这个报文是由Alice发送的。为了鉴别这个报文，Bob需要证实：
1）该报文的确源自Alice。
2）该报文在到Bob的途中没有被篡改。

## 8.4 端点鉴别
端点鉴别（end-point authentication）就是一个实体经过计算机网络向另一个实体证明其身份的过程，例如一个人向某个点子邮件服务器证明其身份。

鉴别协议通常在两个同心实体运行其他协议之前运行。
鉴别协议首先建立相互满意的各方的标识；仅当鉴别完成之后，各方才继续下面的工作。
