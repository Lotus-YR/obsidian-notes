# 2.1 principles of network applications
### Network Application Architectures
- the client-server (cs)
- the peer-to-peer (P2P)

### Processes Communicating
message

##### Client and Server Processes

##### The Interface Between the Process and the Computer Network

##### Addressing Process
常用端口

### What Transport Service dose an App Need?
- data integrity
- timing
- throughput
- security

### Transport Services Provided by the Internet
##### TCP Services
- reliable transport
- flow control
- congestion control

##### UDP Services
- unreliable data transfer
- 可以以任意大的数据进行传输
##### Services Not Provided by Internet Transport Protocols

### Application-Layer Protocols


### Network Applications Covered in This Book


# 2.2 the web and HTTP
### Overview of HTTP
The **Hyper Text Transfer Protocol**(HTTP), the Web's application-layer protocol
client/server model

each object is addressed by a URL(unverisal resource location)
e.g. www.someschool.edu/someDept/pic.gif (host name + path name)

默认80端口
无状态的协议（记性差，不记事
基于对象传输（每次只传一个对象

###### connections
- non-persistent HTTP（每次回复后关闭连接）
- persistent HTTP (持久连接：连接保持到对象传输结束，对所有的参考对象，不包括起始base？)

RTT（return travel time？）

### HTTP传输模式
e.g. 4个对象（三个图片）计算⭐
1. 非持久
	- 串行（非流水）2RTT+3 * 2RTT = 8RTT
	- 并行（流水）2RTT + 2RTT = 4RTT
2. 持久
	- 串行 2RTT + 3RTT = 5RTT
	- 并行 2RTT + RTT = 3RTT
（再多想想......

### HTTP Request Message
![[Pasted image 20240924110251.png|400]]

### HTTP Response Message
![[Pasted image 20241008082536.png|400]]

### User-server state: cookies
记录用户喜好，记录状态

### Web caches (proxy server)


---
## 补充
### FTP
文件传输协议
21端口

过程：
控制连接（out of band 带内传输），数据连接

---

# 2.3 electronic mail in the Internet
### Electronic Mail: SMTP 
SMTP (Simple Mail Transport Protocal)
组成部分：用户代理、邮件服务器和简单邮件传输协议
25端口

持久连接
报文采用7比特ASCII码格式
push protocol 推协议

### 补充内容
MIME: Multimedia mail extension
MIME-Version
Content-Transfer-Encoding
Content-Type
解决非ASCII编码传送问题

### Mail access protocols
收邮件
SMTP
	POP3 无状态
	IMAP 有状态
	HTTP

# 2.4 DNS-the Internet's directory service
### DNS：services, structure
分布式数据库


主机别名
邮件服务器别名
负载均衡

集中缺点：
单点失效
流量
距离
维护

### 补充内容
DNS最高层域名允许按照地理、组织进行划分

根、顶层域、子域、树叶（主机）

域名服务器
在哪个服务器注册 在哪个服务器解析

 root name servers
TLD (top-level domain)
authoritative DNS (organization's own DNS servers)
Local DNS name servers

DHCP

迭代（给线索
递推（帮忙问

##### DNS记录
DNS: distributed database storing resource records (RR)
RR format: (name, value, type, ttl)


##### insert record



# 2.5 peer-to-peer applications
（考试不做要求)
peer (server and host)

一个peer作为客户端接收数据后也可以作为终端发送数据

BitTorrent
碟中谍 别只有一个接头的
传的越多，下的越快


CDN内容分发网络
镜像 缓存 连锁店



### 补充内容
浏览器/服务器
B/S
C/S


服务器工作模式
循环 UDP
并发 TCP
（只是通常情况下.....



