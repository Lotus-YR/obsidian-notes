50 (期末成绩) : 50 (课前测、课后作业、每章课堂测试、签到)

缩写

---
# 1.1 what is the Internet?
![[Pasted image 20240903090006.png|300]]
### A Nut-and-Bolts Description
1. end system(host), router
2. client/server
3. communication link
	transmission rate (bit/second, bps)
4. protocol (**TCP**(Transmission Control Protocol)/**IP**(Internal Protocol))
5. packet switching (spilt the big message)
	message switching(switch the whole message)
6. Internet Standards - **RFC**(Requests for Comments) and **IETF**(Internet Engineering Task Force)
7. **ISP**(Internet Service Provider)
![[Pasted image 20240903095215.png|300]]
### A Service Description
分布式应用程序（distributed application）

套接字（socket interface）

### What's a Protocol
**protocols** define ==format, order== of msgs sent and received among network entities, and actions taken on msg transmission, receipt

# 1.2 network edge
end systems(host)
client/server model
peer-peer model(p2p)

 Networks Structure：
- access networks, physical media: wired, wireless communication links
- network core: interconnected routers, network of networks

### Access Networks and Physical Media
Connecting end systems to edge router:
- residential access nets
- institutional access networks(school, company)
- mobile access networks(wireless access)
#### access networks
**DSL**(Digital Subcriber Line)
cable network:
	**FDM**(Frequency Division Multiplexing)频分多路复用
	**HFC**(Hybrid Fiber Coax)混合光纤同轴
	**FTTH**(Fiber To The Home)光纤到户
**Ethernet**(enterprise access networks)
LAN
3G
**LTE**(Long Term Evolution)

#### physical media
###### guided media:
- **TP**(twisted pair): **UTP**(Unshielded Twisted Pair) STP
- coaxial cable
- fiber optic cable
###### unguided media:
radio

# 1.3 network core
### Packeting-switching: store-and-forward
message
packet
paclet switch:
	router
	link-layer switch
#### queueing delay and loss

统计复用？
#### two key network-core functions
- routing
- forwarding

占线？
程控交换机？
### alternative core: circuit switching
电路交换（按时间计费）
IP电话（可以按流量计费）
???

#### FDM versus TDM
**FDM**(Frequency Division Multiplexing)频分复用
**TDM**(Time Division Multiplexing)时分复用
![[Pasted image 20240903105338.png|300]]

#### packet switching versus circuit switching
packet switching allows **more users** to use network

![[Pasted image 20240910082016.png|400]]

# 1.4 Delay, Loss, and Throughput in Packt-Switched Networks

- 速率
	单位：bps或bit/s
	速率往往指额定速率或标称速率
- 带宽bandwidth
	频带宽度
	单位：赫

### Overview of Delay in Packet-Switched Networks
node(host or router)
four sources of packet delay:
- nodal processing delay
- queuing delay
- transmission delay(有长度)
- propagation delay(点)
![[Pasted image 20240910083636.png|400]]
节点总时延：$d_{nodal} = d_{proc} + d_{queue} + d_{trans} + d_{prop}$


### Queuing Delay and Packet Loss
traffic intensity(流量密度): $La/R$
	R: link bandwidth
	L: packet length
	a: average packet arrival rate


### End-to-End Delay
suppose there are N-1 routers between the source host and the destination host, the nodal delays:
$$d_{end-end} = N (d_{proc} + d_{trans} + d_{prop})$$
终端命令：tracert？？


### Throughput in Computer Networks
throughtput: rate(bits/time unit) at which bits transferred between sender/receiver
	instantanrous即时吞吐量
	average平均吞吐量: $min(R_1, R_2,..., R_n)$

![[Pasted image 20240910092024.png|300]]
per-connection end-end throughtput: $min(R_c, R_s, R/10)$

##### 补充知识点
###### 时延带宽积
链路的时延带宽积又称为以比特为单位的链路长度

###### 往返时间 RTT
往返时间表示从发送方发送数据开始，到发送方收到来自接收方的确认，总共经历的时间

###### 利用率
分为信道利用率和网络利用率

时延与网络利用率的关系


# 1.5 Protocol Layers and Their Service Models
### Layered Architecture
![[Pasted image 20240910093544.png|400]]

##### 多层通信
![[Pasted image 20240910094936.png|300]]
entity(实体): 每一次的活动元素
peer(对等实体): 不同机器上同一层的实体

##### Protocol layering and data
each layer takes data from above:
- adds header information to create new data unit
- passes new data unit to layer below
![[Pasted image 20240910101621.png|400]]

##### 网络的标准协议
- ISO提出OSI(open system interconnection reference model, OSI/rm)（开放系统互连参考模型）协议体系 7层
- TCP/IP协议体系 5层

###### ISO/OSI reference model
![[Pasted image 20240910102003.png|300]]

data是透明的，无法知道具体内容
massage=head+data

##### The Internet Protocol Stack
PDU?
![[Pasted image 20240910102702.png|400]]

- application: supporting network applications
	**FTP, SMTP, HTTP**
- transport: process-process data transfer
	提供端口号  保证进程之间的通信？   （一个主机内有多个端口号？？why？？端口号有啥用？？？？
	**TCP, UDP**
- network: routing of datagrams from source to destination 保证主机和主机之间的通信
	**IP, routing protocols**
- link: data transfer between neighboring network elements 保证一段链路上的通信 node和node之间的通信
	**Ethernet, 802.111(WiFi), PPP**
- physical: bits "on the wire"

### Encapsulation
![[Pasted image 20240910103905.png|400]]
交换机没有网络层，不能基于路由进行通信，只能在同网络中进行通信
（根据设备所有的层次可分析功能）

end-to-end端到端:源实体与目的实体好像直接连接，进行通信 路由器不参与？？？
point-to-point点到点: 对等实体间的通信由一段一段的直接相连机器间通信组成 路由器完全参与

##### 补充知识点
WAN(Wide Area Network)
LAN
MAN
PAN

# 1.6 Network Under Attack
##### The Bad Guys Can Put Malware into Your Host Via the Internet


##### The Bad Guys Can Attack Servers and Network Infrastructure
Denial of Service(DoS)


##### The Bad Guys Sniff Packets
wireshark


##### The Bad Guys Can Masquerade as Someone You Trust
IPv4不能识别来源IP
会被骗


# 1.7 History of Computer Networking and the Internet




---


