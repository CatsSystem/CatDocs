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
    * Swoole回调
    * 前置操作
    * Worker进程初始化
    * Admin端口

* Service
    * Service定义
    * Service初始化
    * Service开发

* 协程
    * Promise
    * yield
    * 协程使用

* 连接池
    * 连接池配置
    * 连接池初始化
    * 连接池管理
    * 连接池使用

* 客户端
    * MySQL
        * MySQL配置
        * MySQL连接
        * MySQL请求
    * Redis
        * Redis配置
        * Redis连接
        * Redis请求
    * Http客户端
        * 同步Http请求
        * 异步Http请求

* 组件
    * 异步任务Task
        * 任务配置
        * 任务定义
        * 任务调用
    * 内存缓存
        * 缓存配置
        * 实现原理
        * 加载器定义
    * 毫秒级定时器
        * 定时器配置
        * 定时器定义
        * After定时器
        * Tick定时器
    * 日志
        * 日志配置
        * 日志驱动
        * 日志写入

* SSL支持
    * SSL密钥文件
    * 开启SSL支持

## CatClient

## CatCenter

## CatDashboard