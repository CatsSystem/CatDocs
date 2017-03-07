# 配置目录

CatMicro的配置文件都存放于项目目录的`config`路径下。

## 配置分类

CatMicro可以将用于不同环境的配置分别存放于不同的文件夹中，在运行的时候指定使用的配置目录。例如我们可以在`config`目录下创建如下两个文件夹：

```bash
cd config/
mkdir default  # 用于测试环境
mkdir release  # 用于线上环境
```

在运行时，使用如下命令即可指定配置路径：

```bash
php run.php             # 默认使用default
php run.php -c release  # 指定使用release
```

在default目录中，可以填写本地配置（比如数据库IP、密码等），并将default目录的配合文件传上代码库用于规范配置格式。

在release目录中，就可以存放线上实际使用的配置，由运维人员编写并上传到服务器指定目录中。

## 配置目录

CatMicro默认必须有的4个配置文件如下所示：

```
├─config                配置目录
│  ├─default            默认配置目录
│  │  ├─component.php   组件配置
│  │  ├─config.php      主配置
│  │  ├─pool.php        连接池配置
│  │  ├─service.php     服务&端口配置
```

开发者可以任意添加自己所需的配置文件，配置文件格式见[配置格式](micro/config/format.md)一章

## config.php

`config.php`是核心配置文件，其中定义了项目相关的配置和swoole扩展的核心配置。其内容如下：

```php
return array(
    'project'=>array(
        'pid_path'          => '/var/run/',       // pid文件存放目录，必须保证路径可写
        'project_name'      => 'micro_service',   // 项目名称

        'main_callback'     => '\\app\\callback\\MainServer', // 主Callback类路径
    ),

    'base' => [                  // swoole扩展配置项
        'daemonize' => 0,

        'worker_num' => 1,
        'dispatch_mode' => 2,

        'task_worker_num' => 1,

        'package_max_length'    => 524288,
    ],

    'server' => array(          // Admin端口配置
        'host' => '0.0.0.0',
        'port' => 9501,
    ),
);
```

其中，swoole扩展配置项见文档[配置选项](https://wiki.swoole.com/wiki/page/274.html)。