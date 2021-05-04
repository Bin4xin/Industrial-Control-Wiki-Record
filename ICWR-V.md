# *Industrial Control Wiki Record* 

## 五：常见工业协议解读



### 5x01 工业协议分析

#### WAIT PLZ...

### 5x02 OpenPCL环境仿真与搭建

环境拉取即可。

### 工控常见端口、服务以及协议

常见的渗透中的利用端口如21、22端口，在我看来，均没有必要花大量时间去探测服务，应当将更多时间来针对个性化端口上的突破；

- 而由于第一章谈到的不同厂商之间通讯硬件、协议之间的差距，我们应做到的是对于常见端口的熟悉：

	- _表5-1 工控常见PLC通讯端口_

 常见端口号  |  协议 | 代表产品 | 厂商
 -----------|-----------|----------------------|-----------
 TCP/44818	| Ethernet/IP | Control Logix | AB 罗克韦尔
 TCP/44818	| Ethernet/IP | Compact Logix | AB 罗克韦尔
 TCP/44818	| Ethernet/IP | - 				| OPTO 22 奥普图
 TCP/44818	| Ethernet/IP | CJ2				| OMRON 欧姆龙
 TCP/18245	| GE SRTP	  | RX3i			| GE通用电气
 TCP/5007	| MELSOFT Protocol | Q series 		| ME 三菱电机
 UDP/5006	| MELSOFT Protocol | - 				| -
 TCP/2001	| OPTO 22 Ethernet | - 				| -
 UDP/9600	| OMRON FINS
 TCP/1962	| -			  | Inlines series      | 菲尼克斯
 TCP/20547	| - 		  | - 					| -
 TCP/502	| Modbus/TCP  | Quantum				| 施耐德
 TCP/102	| ISO-TSAP	  | s7 series			| Siemens西门子

 文件共享服务、连接服务、WEB应用服务等可以参考以下链接，和WEB渗透中常见端口基本一致。
 - [*点击已了解文件共享服务、连接服务、WEB应用服务常用端口及利用方式*](https://www.yuque.com/tidesec/ics/dca86987e7f1058d4a30fc5813cb2f2d#469c29e8)


