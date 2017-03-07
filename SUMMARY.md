# Summary

## Overview

* [概要](README.md)

## CatAPI
* [介绍](api.md)

## CatMicro
* [介绍](micro.md)
* 快速开始
    * [安装](micro/quick_start/install.md)
    * [创建项目](micro/quick_start/create.md)
    * [服务管理](micro/quick_start/manage.md)
* 框架结构
    * [架构总览](micro/structure/main.md)
    * [thrift格式文件](micro/structure/thrift.md)
    * [命名空间](micro/structure/namespace.md)
    * [自动加载](micro/structure/autoload.md)

* 配置
    * [配置目录](micro/config/content.md)
    * [配置格式](micro/config/format.md)
    * [读取配置](micro/config/get.md)
    * [配置加载&重载](micro/config/load_and_reload.md)

* 多端口服务
    * [多端口配置](micro/multi_port/port.md)
    * [Hprose](micro/multi_port/hprose.md)
    * [Thrift](micro/multi_port/thrift.md)
    * [Swoole](micro/multi_port/swoole.md)
    * [自定义端口服务](micro/multi_port/user_define.md)

* 服务初始化
    * [Swoole回调](micro/init/callback.md)
    * [前置操作](micro/init/before_start.md)
    * [Worker进程初始化](micro/init/init_worker.md)
    * [Admin端口](micro/init/admin.md)

* Service
    * [Service定义](micro/service/service.md)
    * [Service初始化](micro/service/init.md)
    * [Service开发](micro/service/develop.md)

* 协程
    * [Promise](micro/concurrent/promise.md)
    * [yield](micro/concurrent/yield.md)
    * [协程使用](micro/concurrent/use.md)

* 连接池
    * [连接池配置](micro/pool/pool.md)
    * [连接池初始化](micro/pool/init.md)
    * [连接池管理](micro/pool/pool_manager.md)
    * [连接池使用](micro/pool/use.md)

* 客户端
    * MySQL
        * [MySQL配置](micro/mysql/config.md)
        * [MySQL连接](micro/mysql/mysql.md)
        * [MySQL请求](micro/mysql/request.md)
    * Redis
        * [Redis配置](micro/redis/redis.md)
        * [Redis连接](micro/redis/config.md)
        * [Redis请求](micro/redis/request.md)
    * Http客户端
        * [同步Http请求](micro/http/sync.md)
        * [异步Http请求](micro/http/async.md)

* 组件
    * 异步任务Task
        * [任务配置](micro/component/task/config.md)
        * [任务定义](micro/component/task/task.md)
        * [任务调用](micro/component/task/use.md)
    * 内存缓存
        * [缓存配置](micro/component/cache/config.md)
        * [加载器定义](micro/component/cache/cache.md)
        * [调用缓存](micro/component/cache/use.md)
    * 毫秒级定时器
        * [定时器配置](micro/component/timer/config.md)
        * [定时器定义](micro/component/timer/config.md)
        * [After定时器](micro/component/timer/config.md)
        * [Tick定时器](micro/component/timer/config.md)
    * 日志
        * [日志配置](micro/component/log/config.md)
        * [日志驱动](micro/component/log/config.md)
        * [日志写入](micro/component/log/config.md)

* SSL支持
    * [SSL密钥文件](micro/ssl/key.md)
    * [开启SSL支持](micro/ssl/open.md)

## CatClient

## CatCenter

## CatDashboard