数据分析平台开放API接口设计

<!-- TOC depthFrom:1 depthTo:6 withLinks:1 updateOnSave:1 orderedList:0 -->

- [1 概述](#1-概述)
- [2 开放API系统](#2-开放api系统)
	- [2.1 概述](#21-概述)
	- [2.2 套牌车服务(Fake Plate Vehicles Service)](#22-套牌车服务fake-plate-vehicles-service)
		- [2.2.1 概述](#221-概述)
		- [2.2.2 功能接口](#222-功能接口)
	- [2.3 相似文本服务(Similar text Service)](#23-相似文本服务similar-text-service)
		- [2.3.1 概述](#231-概述)
		- [2.3.2 功能接口](#232-功能接口)
			- [2.3.2.1 数据文件批量导入接口](#2321-数据文件批量导入接口)
			- [2.3.2.1 相似文本查询接口](#2321-相似文本查询接口)
	- [2.4 话单碰撞分析服务(Analysis of Telephone Call Records Service)](#24-话单碰撞分析服务analysis-of-telephone-call-records-service)
		- [2.4.1 概述](#241-概述)
		- [2.4.2 功能接口](#242-功能接口)
			- [2.4.2.1 数据文件批量导入接口](#2421-数据文件批量导入接口)
			- [2.4.2.2 话单查询接口](#2422-话单查询接口)
- [3 数据分析系统](#3-数据分析系统)
	- [3.1 概述](#31-概述)
	- [3.2 相似文本服务(Similar text Service)](#32-相似文本服务similar-text-service)
		- [3.2.1 相似文本分析任务启动接口](#321-相似文本分析任务启动接口)
	- [3.2 话单碰撞分析服务(Analysis of Telephone Call Records Service)](#32-话单碰撞分析服务analysis-of-telephone-call-records-service)
		- [3.2.1 话单碰撞分析任务启动接口](#321-话单碰撞分析任务启动接口)
- [4 后记](#4-后记)
- [5 参考文献](#5-参考文献)

<!-- /TOC -->

# 1 概述

　　数据分析服务平台是针对数据分析打造的一个业务服务平台，主要任务是完成以大数据为核心的各类数据分析服务。

　　目前，数据分析服务平台主要提供套牌车(Fake Plate Vehicles)、相似文本(Similar text)、话单碰撞分析(Analysis of Telephone Call Records)服务。

　　考虑到后续业务治理及维护的轻便，这里将整个数据分析服务平台划分为**数据采集系统**、**数据处理系统**、**开放API系统**。

　　其中，**数据采集系统**由其他研发团队完成，这里暂且不提。

　　**数据分析系统**是一个逻辑上的概念，具体由**套牌车分析系统**、**相似文本分析系统**、**话单分析系统**组成，后续根据业务需要再添加其他的系统到数据分析系统中来。

　　**开放API系统**在逻辑上属于数据分析系统的前端，主要任务是将数据分析系统可以提供的的服务有选择的开放给外部系统，方便他们使用。在整平台体系上，开放API系统属于一个应用网关系统。

# 2 开放API系统

## 2.1 概述

　　**开放API系统**封装数据分析系统可以提供的服务，有选择的外部系统提供基于Restful形式的服务。目前主要涉及**套牌车分析**、**相似文本分析**、**话单碰撞分析**三部分。

　　我们这里采用标准的Restful风格的接口定义方式。这里简要描述一下，其中的一些约定。

- API入口约定
　　我们约定Restful资源URL根路径如下
``` http
http://${ip}:${port}
```
　　其中，`${ip}`是服务器ip地址,`${port}`是服务器端口号。我们约定开放api子域名为api。

- 动作约定

　　我们约定Restful资源动作如下:

动作     | 方法修改词            | HTTP METHOD           | 示例
-------- | -------                |--------               |--------
增加 |  create        | POST       |POST:http://api.qwfys.org/users
删除    |  remove        |DELETE        |DELETE:http://api.qwfys.org/users?id=id
修改     |  update        | PUT       |PUT:http://api.qwfys.org/users
查询     |  find        |GET       |GET:http://api.qwfys.org/users?id=id


## 2.2 套牌车服务(Fake Plate Vehicles Service)
### 2.2.1 概述
　　套牌车服务这一块目前主要提供查询接口。
### 2.2.2 功能接口

获取套牌车记录列表接口
　　按入库时间起止范围获取套牌车记录列表。
- 资源路径

```http
/vehicles/fakeplates?startDataTime=${startDataTime}&endDataTime=${endDataTime}
```

- 方法类型
> - 方法类型为GET。

- 参数说明
> - `${startDataTime}`是入库时间起始时间。
> - `${endDataTime}`入库时间结束时间。

- 返回结果
> - `status`	结果，true代表成功，false代表失败。
> - `code`     返回码。
> - `message`     返回信息。
> - `data` 数据结果，仅在`result`为true的情况时有效，data代表了套牌车记录列表。

## 2.3 相似文本服务(Similar text Service)
### 2.3.1 概述
　　相似文本服务这一块目前主要提数据文件上传接口、信息查询接口。

### 2.3.2 功能接口
#### 2.3.2.1 数据文件批量导入接口
　　生成系统唯一业务编号，来标识本次数据文件提交接收任务，接收数据文件并告知数据相似文本分析系统启动相似文本分析程序处理导入的数据，之后返回数据文件提交返回信息给数据文件提交方，表明数据提示成功。
- 资源路径
```http
/text/similars/create
```
- 方法类型
> - 方法类型为POST。

- 参数说明
> - 数据文件集

- 返回结果
> - `status`	结果，true代表成功，false代表失败。
> - `code`     返回码。
> - `message`     返回信息。
> - `data` 数据结果，仅在`result` 为true的情况时有效，data代表了文件提交任务清单的编号。

#### 2.3.2.1 相似文本查询接口
　　根据任务编号查询话相似文本分析信息。
- 资源路径
```http
/text/similars?taskId=${taskId}
```
- 方法类型
> - 方法类型为GET。

- 参数说明
> - `${taskId}`相似文本任务ID。

- 返回结果
> - `status`	结果，true代表成功，false代表失败。
> - `code`     返回码。
> - `message`     返回信息。
> - `data` 数据结果，仅在`result`为true的情况时有效，data代表了文本相似度查询结果对象。

## 2.4 话单碰撞分析服务(Analysis of Telephone Call Records Service)
### 2.4.1 概述
　　话单碰撞分析服务这一块目前主要提数据文件上传接口、信息查询接口。
### 2.4.2 功能接口
#### 2.4.2.1 数据文件批量导入接口
　　生成系统唯一业务编号，来标识本次数据文件提交接收任务，接收数据文件并告知话单碰撞分析系统启动话单碰撞分析程序处理导入的数据，之后返回数据文件提交返回信息给数据文件提交方，表明数据提示成功。
- 资源路径
```http
/telephones/create
```
- 方法类型
> - 方法类型为POST。

- 参数说明
> - 数据文件集

- 返回结果
> - `status`	结果，true代表成功，false代表失败。
> - `code`     返回码。
> - `message`     返回信息。
> - `data` 数据结果，仅在`result`为true的情况时有效，data代表了文件提交任务清单的编号。

#### 2.4.2.2 话单查询接口
　　根据任务编号查询话单分析信息。

- 资源路径
```http
/telephones?taskId=/${taskId}
```
- 方法类型
> - 方法类型为GET。

- 参数说明
> - `${taskId}`    相似文本任务ID。

- 返回结果
> - `status`	结果，true代表成功，false代表失败。
> - `code`     返回码。
> - `message`     返回信息。
> - `data` 数据结果，仅在`result`为true的情况时有效，data代表了话单分析信息查询结果对象。


# 3 数据分析系统
## 3.1 概述

　　开发API系统完成了相似文本、话单数据文件的接收工作，数据文件接收到以后，通知数据相似文本分析系统、话单碰撞分析系统启动相应的分析程序完成数据的分析工作，故而，数据分析系统这边要提供相应的服务接口，以便开放API系统能将消息通知给数据分析系统。

　　**数据分析系统**为了方便后续文档的编写，这里做一些约定其子域名为analysisapi。

## 3.2 相似文本服务(Similar text Service)
### 3.2.1 相似文本分析任务启动接口
　　根据任务编号查找已经接收到数据文件，调用文本相似度分析程序分析数据。

- 资源路径
```http
/text/similar/start/${taskid}
```
- 方法类型
> - 方法类型为POST。

- 参数说明
> - `${taskid}`任务编号。

- 返回结果
> - `status`	结果，true代表成功，false代表失败。
> - `code`     返回码。
> - `message`     返回信息。

## 3.2 话单碰撞分析服务(Analysis of Telephone Call Records Service)
### 3.2.1 话单碰撞分析任务启动接口
　　根据任务编号查找已经接收到数据文件，调用话单碰撞分析程序分析数据。
- 资源路径
```http
/telephone/start/${taskid}
```
- 方法类型
> - 方法类型为POST。

- 参数说明
> - `${taskid}`任务编号。

- 返回结果
> - `status`	结果，true代表成功，false代表失败。
> - `code`     返回码。
> - `message`     返回信息。

# 4 后记
　　考虑到开放API系统是Java系统，数据分析系统以Python为主，这里采用基于Restful方式完成开放API系统与数据分析系统之间的交互。
　　Restful方式在性能上不及Thrift性能高，后续如果压力测试达不到要求的时候，可以考虑用Thrift做为备选方案完成开放API系统与数据分析系统之间的交互的替代方案。


# 5 参考文献
>
1. [理解RESTful架构](http://www.ruanyifeng.com/blog/2011/09/restful.html)
2. [RESTful API 设计指南](http://www.ruanyifeng.com/blog/2014/05/restful_api.html)
