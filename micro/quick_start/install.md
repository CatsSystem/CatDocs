# 安装

## 环境依赖

安装前请先确保您的操作系统中已经安装了如下库或者扩展：

* [hiredis库](https://github.com/redis/hiredis)
* [thrift库](micro/structure/thrift.md)
* [swoole扩展](https://github.com/swoole/swoole-src)
* [swoole_serialize扩展](https://github.com/swoole/swoole_serialize)
* [phpredis扩展](https://github.com/phpredis/phpredis)
* [hprose-pecl扩展](https://github.com/hprose/hprose-pecl)

## 安装
CatMicro支持使用Composer安装，只需在项目目录下创建`composer.json`文件，并写入如下内容：

```json
{
    "require": {
        "cat-sys/cat-micro":"dev-master"
    }
}
```

接着在Shell中执行`composer update`命令即可。

如果你的环境中没有安装Composer组件，可以访问如下网址学习如何安装：[Composer中文网](http://www.phpcomposer.com/)