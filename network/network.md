##	网络硬件
###	传输技术
+	点到点链路
+	广播式链路
###	网路尺度
+	个域网 PAN 1米
	+	计算机通过无线网络与其外围设备连接
	+	蓝牙，RFID（射频识别）
+	局域网 LAN 10~1000米
	+	家庭网络，企业网络
	+	无线局域网
		+	计算机、无线调制解调器、天线 ---- 接入点（AP）、无线路由器、基站
		+	IEEE 802.11 WiFi
	+	有线局域网
		+	拓扑结构 以点到点链路为基础
		+	IEEE 802.3 以太网（Ethernet）
		+	交换式以太网（switched Ethernet） 计算机 ---- 交换机
	+	虚拟局域网 （Virtual LAN）
+	城域网 MAN 10千米
	+	有线电视网
	+	IEEE 802.16 WiMAX 
+	广域网 WAN 100~1000千米
	+	主机
	+	子网
		+	将数据包从源主机移动的目标主机、网络寻址
		+	传输路线、交换元素（交换机/路由器）
		+	使用Internet 虚拟专用网络（VPN Virtual Private Network）
		+	租赁线路 ISP网络（Internet Service Provider network）
+	互联网 internet
	+	全球范围的因特网Internet、
	+	不同的网络（运营归属不同、底层技术不同）相互连接在一起
	+	网关 gateway
+	星际互联网络 Interplanetary Internet
	+	Burleigh
		

##	网络软件
###	网络体系结构
+	层次栈：通过接口，每层向上层提供特定服务，并屏蔽实现细节
+	协议：相应层次的实体（对等体，对等进程）通过协议通信
+	上层-->(接口)-->下层-->物理介质-->下层-->上层
###	层次设计问题
+	可靠性：数据包正确、路由
+	网络演进
+	资源分配
+	安全性
### 面向连接和无连接服务
+	面向连接
	+	可靠的报文流
	+	可靠的字节流
	+	不可靠的连接
+	无连接
	+	不可靠的数据报
	+	有确认的数据报
	+	请求-应答
###	服务与协议
+	服务：某一层向它上一层提供的一组原语（操作）
+	协议：规定同层上对等实体之间所交换的数据包或者报文的格式与含义

##	参考模型
###	OSI参考模型 （Open System Interconnection）
+	物理层
	+	传输原始比特
+	数据链路层
	+	没有漏检传输错误、流量调节、共享信道
+	网络层
	+	控制子网运行、如何将数据包从源端路由到接收方
	+	拥塞、服务质量、异构网络互连
+	传输层
	+	端对端、隔离上下层，确保上层数据通过下层到达接收方
+	会话层
	+	允许不同机器上的用户建立会话、对话控制、令牌管理、同步功能
+	表示层
	+	传递信息的语法和语义、标准编码方法
+	应用层
	+	用户协议

###	TCP/IP参考模型
+	链路层
	+	DSL、SONET、802.11、Ethernet
+	互联网层
	+	IP、ICMP
+	传输层
	+	TCP、UDP
+	应用层
	+	DNS、TELNET、FTP、SMTP、HTTP、RTP


