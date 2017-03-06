# 多端口配置

CatMicro框架采用的是多端口模式，Thrift定义的每一个Service都会对应一个端口，并可以自由定义端口所使用的协议类型和序列化方式。

## 端口配置

服务使用的端口配置在配置目录的`service.php`文件中定义，其基本结构如下所示：

```php
return [

    'open_hprose'   => true,          // 开启hprose支持
    'open_thrift'   => true,          // 开启thrift支持
    'open_swoole'   => true,          // 开启swoole支持

    'service' => [
        [
            'port_type'         => 'hprose',                            // 模块类型,支持hprose, thrift, swoole
            'socket_type'       => 'tcp',                               // tcp, http, ws,
            'enable_ssl'        => false,                               // 是否开启SSL
            'host'              => '0.0.0.0',
            'port'              => 9502,

            'processor_path'    => 'app\\processor\\HproseService',     // Processor路径
            'service_path'      => 'app\\service\\HproseService',       // Service路径

            'protocol'  => [    // 自定义协议设置

            ]
        ],
        …
    ]
];
```

前三个选项用于配置是否开启对应的序列化模式，只有设置为true的模式才能够使用。

在`service`配置中定义了每一个端口的行为。

* `port_type`定义了端口的序列化类型。
* `socket_type`决定了端口使用tcp、http还是websocket协议。
* `enable_ssl`决定是否启用SSL加密，如果开启需要在`protocol`指定密钥文件。
* `host`和`port`共同决定了监听的IP和端口号
* `processor_path`指定了Thrift生成的Processor类的路径
* `service_path`指定了处理请求的Service的路径
* `protocol`中是对端口的定制化配置，参见[swoole端口配置](https://wiki.swoole.com/wiki/page/526.html)
