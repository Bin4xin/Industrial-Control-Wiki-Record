# *Industrial Control Wiki Record* 

## 一：工控安全基础

工业控制系统(*Industrial Control Systems,ICS* 简称：工控系统)，是由各种自动化控制组件以及对实时数据进行采集、监测的过程控制组件共同构成的确保工业基础设施自动化运行、过程控制与监控的业务流程管控系统。其核心组件包括：


- 1.可编程控制器
	- i.Programmable Logic Controller(PLC)
- 2.数据采集与监控系统
	- ii.Supervisory Control and Data Acquisition(SCADA)
- 3.分布式控制系统
	- iii.Distributed Control Systems(DCS)
- 4.远程终端
	- iv.Remote Terminal Unit(RTU)
- 5.人机交互界面设备
	- v.Human Machine Interface(HMI)
- 确保各组件通信的接口技术。
	- Interface technology for communication between components...

### 1x01 工控系统和传统网络的区别

> 工业控制网络安全问题与传统IT系统的网络安全问题有着很大的区别。

- 网络边缘不同
	- 工控系统在地域上分布广阔，其边缘部分是智能程度不高的含传感和控制功能的远动装置
	- 与IT系统边缘的通用计算机，两者之间在物理安全需求上差异很大。

- 体系结构不同
	- 工业控制网络的结构纵向高度集成，主站节点和终端节点之间是主从关系。
	- 传统IT信息网络则是扁平的对等关系，两者之间在脆弱节点分布上差异很大。

- 传输内容不同：
	- 工业控制网络传输的是工业设备的“四遥信息”，即遥测、遥信、遥控、遥调。此外，还可以从性能要求、部件生命周期和可用性要求等多方面，进一步对二者进行对比，详细内容如下表1所示。
		- _表1-1 工控与传统网络之间传输区别_

 两者传输区别 | 工业控制网络 | 传统IT信息网络
----------|---------------------------|---------------------------
性能要求 | 实时通信、高响应、限定延迟及抖动、适度吞吐 | 无响应、时延要求、高吞吐
生命周期 | 15-20年 | 3-5年 
可用性要求 | 高可用、连续工作 | 可重启系统、可存在可用性缺陷
风险管理要求 | 员工人身安全 > 保护生产过程及提高容错率 | 数据机密性&完整性 > 系统容错率
系统操作 | 操作复杂，修改升级系统需专业知识 | 操作可利用自动化部署工具进行
资源限制 | 多数不允许第三方信息安全解决方案 | 存在足够资源包括第三方开源程序
技术支持 | 专用协议:`ModBus、Profibus、CC-Link...` | TCP/IP等通用协议
通信方式 | 不同供应商协议不一，包括专线、无线 | 标准通信协议，如LAN区、WIFI等均可通信
变更管理 | 需暂停生产；变更前需完全测试、部署 | 自适应软件更新、及时变更

**工控系统网络安全是要防范和抵御攻击者通过恶意行为人为制造生产事故、损害或伤亡。**

### 1x02 工控系统常见威胁

工控网络中大量采用TCP/IP技术，工控网和企业管理网的联系越来越紧密，由于:

- 1、工控系统也由封闭演变成现在的开放系统，其设计上基本没有考虑互联互通所必须考虑的通信安全问题。

- 2、企业管理网与工控网的防护功能都很弱，甚至几乎没有隔离功能；


> 因此，在工控系统开放的同时，也减弱了工控系统与外界的隔离，工控系统
> 的安全隐患问题日益严峻。

**工控系统中任何一点受到攻击都有可能导致整个系统的瘫痪。**


- _表1-2 工控前中后期的发展_

 前期 | 现在及将来
--------------------|-----------------------
封闭、专门系统			| 开放系统、大规模采用IT技术
独立的通讯解决方案		| 集成化、互联化、相互操作
生产部门负责工业通信运营| IT部门、生产部门共同负责
极少安全机制			| 综合全面的安全防护解决方案
服务面向产品			| 服务面向解决方案

#### # 技术对比分析

工控系统的信息技术来源于传统信息技术，但是又不同于传统信息技术，这是因为：

- 1、传统信息技术是以传递信息为最终目的；
	- 众所周知，在办公应用环境中，计算机病毒和蠕虫往往会导致公司网络故障，因而办公网络的信息安全越来越受到重视，通常采用杀毒软件和防火墙等软件方案解决安全问题；

- 2、而工控系统网络传递信息时以引起物质或能量的转移为最终目标；
	- 在工控系统中，恶意入侵软件，将会造成生产线停顿，导致严重后果。因此，工控系统安全有更高的要求，传统信息技术的解决方案已不能满足这些需求。

- 所以两者间存在的明显差距，可以通过下表1-3来表示：

	- _表1-3 传统网络与工控间的对比_

 对比项  | 传统IT网络 | 工控网络
----------------|---------------|----------------------------
系统架构		| TCP/IP协议		| 传感器、PLC、RTU、DCS、SCADA......
操作系统 		| WIN、Linux.. 	| 嵌入式系统：Vxworks、WinCE等可定制..
数据交换协议	| TCP/IP协议   	| 专用通信协议（规约）：OPC、ModBus、TCP、DNP3...
系统升级		| _见表1-2不再赘述_			
可用性要求	| _见表1-2不再赘述_
时间敏感性	| _见表1-2不再赘述_			
无线技术应用	| 较多			| 起步阶段


#### # 技术对比分析

- 本质问题
	- 1、安全设计不足：设计之初由于资源受限且未面向互联网，工控系统普遍缺乏安全性设计，产品形态多集中在网络安全防护层面。
	- 2、核心技术落后；
	- 3、缺乏动力：由于市场、技术、使用环境等方面的制约，工控生产普遍缺乏安全加固动力。
- 安全策略、管理流程问题
	- 工控从业人员安全意识欠缺，相关企业缺少规范安全流程、策略与灾难恢复计划、安全审计机制等。
- 工控平台问题
	- 1、平台硬件：
		- 缺少物理环境安全控制、不安全的远程访问组件...
	- 2、平台软件：
		- 通信协议依赖于RPC、DCOM等不安全工控协议，缺少入侵检测与防护措施，缺乏有效鉴权、访问控制等
	- 3、平台配置：
		- 系统、应用平台缺少运维、测试，多采用默认配置且关键配置未备份，缺少必要口令策略，不充分的访问控制规则等
	- 4、恶意代码：
		- 缺少恶意代码防护程序，或程序未及时更新、存在兼容性问题等。

### 1x03 工控系统网络问题

- （1） 网络结构：工控系统网络架构设计不合理，未进行VLAN 划分，未能有效防止广播风暴等。
- （2） 网络硬件：网络设备物理安全防护缺乏或不充分，物理端口缺少防护，环境控制缺失，非相关人员访问设备、连接网络，缺少关键设施的容错、冗余、备份。
- （3） 网络配置：网络安全设备配置不当，设备配置的关键信息无备份，设备口令策略不合理。
- （4） 网络边界：网络边界缺失或边界防护设备配置不当。
- （5） 网络通信：采用明文传输的协议，缺少对数据、设备、用户、实体等的规范的认证机制，通信完整性检查缺失。
- （6） 网络监控与日志：工控系统网络缺少安全监控审计，日志记录不充分。
- （7） 无线连接：缺少对无线 AP 与客户端间的数据保护或认证不充分。


## 参考

- [工控系统常见安全威胁](https://www.yuque.com/tidesec/ics/560d909f67a8006887f57b03fc624db2)
