# Hprose

[Hprose](http://www.hprose.com/)和Thrift一样提供了跨语言的RPC服务支持。作为服务器，CatMicro框架选用了[hprose-swoole](https://github.com/hprose)作为底层支持。

客户端可以借助Hprose提供的客户端组件访问服务：

```php
// 构建Hprose客户端，选用tcp协议
$client = new \Hprose\Socket\Client('tcp://127.0.0.1:9502', false);
$req = new TestRequest([
        'id' => 1,
        'name' => "test",
        'lists' => [1,2,3]
    ]
);
$response = $client->test1($req);
var_dump($response);
```

更多Hprose的用法可以参考Hprose的文档。