# CatMicro介绍

CatMicro是基于Swoole开发的微服务框架，框架的服务基于Thrift格式实现，提供Thrift序列化、Hprose序列化、Swoole序列化三种模式，可通过配置文件，在同一服务内的不同端口上提供不同协议、不同序列化方式的服务，便于扩展开发。

框架内置多种Swoole组件封装，并内置协程支持，可使用同步化代码实现异步调用、并行调用。

框架提供如下特性：

* 基于Thrift文件定义服务接口及数据结构
* 提供Thrift、Hprose、Swoole三种序列化模式
* TCP、HTTP、WebSocket自由切换
* 支持SSL
* 内置异步MySQL连接池
* 内置异步Redis组件
* 内置异步Http客户端组件
* 内置异步Task组件
* 内置定时器组件
* 内置内存Cache组件
* 内置协程
* 灵活的配置化管理
* 提供系统脚本