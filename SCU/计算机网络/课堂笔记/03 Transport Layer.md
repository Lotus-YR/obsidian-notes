# 3.1 transport-layer services
### transport services and protocols
小娃送信
network layer
transport layer

TCP靠谱小娃
UDP心大小娃

# 3.2 multiplexing and demultiplexing

### Multiplexing
复用
加头部信息
### Demultiplexing
分用
根据目的端口号分发数据
	端口号：
	1~1023
	1023~65535

##### Connection-oriented demux
TCP: s_IP+s_port+ d_IP+d_port 套接字连接 管道
UDP: 不连接

# 3.3 connectionless transport: UDP
### User Datagram Protocol
流媒体
DNS
SNMP

##### why is there a UDP?
- no connection establishnment, without delay
- simple
- small header size
- no congestin control: can blast away as fast as desired

##### UDP checksum
计算
16bits

# 3.4 principles of reliable data transfer
rdt

2.0 比特位错： 校验 确认 重传
2.2 ACK错：序号
2.3 丢包：定时器

3.0 五种方法

..............（没好好听啊

GBN (Go back N)
SR (Selection Repeat)
接收窗口大小不同
定时器个数
累计/独立ACK

# 3.5  connection-oriented transport: TCP



# 3.6 principles of congestion control
### causes/costs of congestion: scenario 1
增加buffers
不可行，队列时延太大

### causes/costs of congestion: scenario 2
不增加buffers 
重传了没必要的包

### causes/costs of congestion: scenario 3
控制速率


# 3.7 TCP congestion control
**AIMD** (additive increase multiplicative decrease)
发现有点堵 减小速率
堵：超时、重复ACK

CWND () 最大拥塞窗口

### TCP Slow Start
**SS** (slow start)

收到一个ACK就+1（double）
指数变换，慢慢加速，直到阈值ssthresh

**CA** (congestion aviodance)
收到一个ACK就+1/N （+1）
线性变换，没有阈值
直到：timeout（很严重）
		ssthresh=cwnd/2
		cwnd = 1
	   3 dup ACK（不是很严重）Reno算法
		ssthresh = cwnd/2
		cwnd = ssthresh 
	   Tahoe算法
		timeout or 3 dup ACK 都把cwnd = 1
	
什么东西啊
快速恢复 恢复原来的状态
控制速率？？？

TCP thruput = 3/4 * W/RTT


ECN (Explicit Congestion Notification)


RCVwin（流量控制）

piggyback（捎带技术：发数据的时候把OK也捎带发了）

