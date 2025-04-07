# 第1章 了解Web及网络基础
### 1.1 使用HTTP协议访问Web
Web使用一种名为HTTP（HyperText Transfer Protocol，超文本传输协议）的协议作为规范，完成从客服端到服务器端等一系列运作流程

### 1.2 HTTP的诞生
##### 为知识共享而规划web
借助多文档之间相互关联形成的超文本（HyperText），连成可相互参阅的WWW（World Wide Web，万维网）

现在已提出了3 项WWW 构建技术，分别是：把SGML（Standard Generalized Markup Language，标准通用标记语言）作为页面的文本标记语言的**HTML**（HyperText Markup Language，超文本标记语言）；作为文档传递协议的**HTTP** ；指定文档所在地址的**URL**（Uniform Resource Locator，统一资源定位符）
##### web成长时代
CERN 成功研发了世界上第一台Web 服务器和Web浏览器
现代浏览器的祖先NCSA（National Center for Supercomputer Applications，美国国家超级计算机应用中心）研发的Mosaic 问世了
....
##### 驻足不前的HTTP
....
### 1.3 网络基础TCP/IP
通常使用的网络（包括互联网）是在TCP/IP 协议族的基础上运作的。而HTTP 属于它内部的一个子集。

##### TCP/IP协议族
不同的硬件、操作系统之间的通信，所有的这一切都需要一种规则。而我们就把这种规则称为**协议（protocol）**。
![[Pasted image 20240908094025.png|300]]

##### TCP/IP的分层管理
TCP/IP 协议族里重要的一点就是分层。TCP/IP 协议族按层次分别分为以下4 层：**应用层、传输层、网络层和数据链路层**。

- 应用层
	决定向==用户提供应用服务==时通信的活动
	提供**FTP**（File Transfer Protocol，文件传输协议）和 **DNS**（Domain Name System，域名系统）服务。**HTTP** 协议也处于该层。
- 传输层
	对上层应用层提供处于网络连接中的==两台计算机之间的数据传输==
	有两个性质不同的协议：**TCP**（Transmission ControlProtocol，传输控制协议）和 **UDP**（User Data Protocol，用户数据报协议）。
- 网络层（网络互连层）
	处理在网络上流动的数据包
	**IP**协议
- 链路层（数据链路层，网络接口层）
	处理连接网络的硬件部分

##### TCP/IP通信传输流
![[Pasted image 20240908095026.png|400]]
![[Pasted image 20240908102900.png|400]]


### 1.4 与HTTP关系密切的协议：IP、TCP和DNS
##### 负责传输的IP协议
IP（Internet Protocol）网络协议位于网络层
作用：把各种数据包传送给对方
条件：IP地址和MAC地址（Media Access Control Address）
	IP地址：节点被分配到的地址，可变换
	MAC地址：网卡所属的固定地址，基本不更改

ARP（Address Resolution Protocol）是一种用以解析地址的协议，根据通信方的IP地址就可以反查出对应的MAC地址
![[Pasted image 20240908103744.png|400]]

##### 确保可靠性的TCP协议
TCP位于传输层，提供可靠的字节流服务
	字节流服务指将大块数据分割成以**报文段segment**为单位的数据包进行管理
	可靠的传输服务指能够把数据准确可靠地传给对方

TCP协议采用了三次握手（three-way handshaking）策略
	握手过程中使用了TCP 的标志（flag）——**SYN**（synchronize）和**ACK**（acknowledgement）
![[Pasted image 20240908105449.png|400]]

### 1.5 负责域名解析的DNS服务
**DNS**（Domain Name System）服务是和HTTP协议一样位于应用层的协议，提供==域名到IP地址之间的解析服务==

计算机可以被赋予IP地址（计算机容易理解），也可以被赋予主机名和域名（用户容易记忆）
![[Pasted image 20240908105912.png|400]]

### 1.6 各种协议与HTTP协议的关系
![[Pasted image 20240908110448.png|400]]

### 1.7 URI和URL
URI（Uniform Resource Identifier，统一资源标识符）
URL（Uniform Resource Locator，统一资源定位符）

##### 统一资源标志符
Uniform：规定统一的格式
Resource：可标识的任何东西
Identifier：可标识的对象，也称为标识符

URI就是由某个协议方案表示的资源的定位标识符
	协议方案：访问资源所使用的协议类型名称（http、ftp、mailto、telnet、file等）

URI用字符串标识某一互联网资源，而URL表示资源的地点（互联网上所处的位置），==URL是URI的子集==

##### URI格式
表示指定的URI，要使用**涵盖全部必要信息**的绝对URI、绝对URL以及相对URL
![[Pasted image 20240908111856.png|400]]
- 协议方案名：不区分大小写，最后加冒号
- 登录信息：可选
- 服务器地址：名称、IPv4地址名、IPv6地址名
- 服务器端口号：可选
- 文件路径：类似UNIX
- 查询字符串：可选，可传入参数
- 片段标识符：可选，标记出已获取资源中的子资源

有一些用来制定HTTP 协议技术标准的文档， 它们被称为**RFC**（Request for Comments，征求修正意见书）
并不是所有的应用程序都符合RFC

# 第2章 简单的HTTP协议
### 2.1 HTTP协议用于客户端和服务器之间的通信
仅从一条通信路线来说，服务器端和客户端的角色是确定的，而用HTTP 协议能够明确区分哪端是客户端，哪端是服务器端


### 2.2 通过请求和响应的交换达成通信
HTTP 协议规定，请求从客户端发出，最后服务器端响应该请求并返回

![[Pasted image 20241013102310.png|400]]

![[Pasted image 20241013102612.png|400]]

### 2.3 HTTP是不保存状态的协议
HTTP 协议自身不对请求和响应之间的通信状态进行保存，是无状态协议

为了实现保证状态功能，引入了cookie技术

### 2.4 请求URI定位资源
当客户端请求访问资源而发送请求时，URI 需要将作为请求报文中的请求URI 包含在内


### 2.5 告知服务器意图的HTTP方法
##### GET：获取资源
指定的资源经服务器端解析后返回响应内容

如果请求的资源是文本，那就保持原样返回；
如果是像**CGI**（Common Gateway Interface，通用网关接口）那样的程序，则返回经过执行后的输出结果。

![[Pasted image 20241013105025.png|400]]
##### POST：传输实体主体
![[Pasted image 20241013105159.png|400]]
##### PUT：传输文件
HTTP/1.1 的PUT 方法自身不带验证机制，任何人都可以上传文件, 存在安全性问题，因此一般的Web 网站不使用该方法
配合Web 应用程序的验证机制，或架构设计采用**REST**（REpresentationalState Transfer，表征状态转移）标准的同类Web 网站，就可能会开放使用PUT 方法

![[Pasted image 20241013105356.png|400]]
##### HEAD：获得报文首部
和GET方法一样，只是不返回报文主体部分
用于确认URI的有效性及资源更新的日期时间等
![[Pasted image 20241013105619.png|400]]
##### DELETE：删除文件
与PUT相反，一般也不使用
![[Pasted image 20241013105945.png|400]]
##### OPTIONS：询问支持的方法
![[Pasted image 20241013105959.png|400]]

##### TRACE：追踪路径
TRACE方法是让Web服务器端将之前的请求通信环回给客户端的方法
？？？

发送请求时，在Max-Forwards 首部字段中填入数值，每经过一个服务器端就将该数字减1，
当数值刚好减到0 时，就停止继续传输，
最后接收到请求的服务器端则返回状态码200 OK 的响应。

TRACE方法不常用，而且容易引发XST（Cross-Site Tracing，跨站追踪）攻击

![[Pasted image 20241013110744.png|400]]
##### CONNECT：要求用隧道协议连接代理
CONNECT 方法要求在与代理服务器通信时==建立隧道==，实现用隧道协议进行TCP 通信
主要使用**SSL**（Secure Sockets Layer，安全套接层）和**TLS**（Transport Layer Security，传输层安全）协议把通信内容加密后经网络隧道传输

![[Pasted image 20241013111049.png|400]]

### 2.6 使用方法下达命令
![[Pasted image 20241013111228.png|500]]

### 2.7 持久连接节省通信量
HTTP协议初始版本中，每进行一次HTTP通信就要断开一次TCP连接
![[Pasted image 20241013111315.png|400]]
##### 持久连接
持久连接（HTTP Persistent Connections, 也称为HTTP keep-alive或HTTP connection reuse）

![[Pasted image 20241013111544.png|400]]

##### 管线化
管线化（pipelining） 多线程....?
![[Pasted image 20241013111858.png|400]]

### 2.8 使用Cookie的状态管理
Cookie 技术通过在请求和响应报文中写入Cookie 信息来控制客户端的状态

？？？为啥我抓的没有cookie
![[Pasted image 20241013112435.png|400]]

# 第3章 HTTP报文内的HTTP信息




# 第4章 返回结果的HTTP状态码




# 第5章 与HTTP协作的Web服务器




# 第6章 HTTP首部





# 第7章 确保Web安全的HTTPS




# 第8章 确认访问用户身份的认证





# 第9章 基于HTTP的功能追加协议




# 第10章 构建Web内容的技术





# 第11章 Web的攻击技术




