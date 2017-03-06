# Thrift

Thrift模式直接使用了Thrift PHP Library作为支持，使用了Thrift的`TBinaryProtocol`和`TFramedTransport`实现协议解析。

客户端可以使用如下代码访问远程服务：

```php
use app\processor\ThriftServiceClient;
use app\processor\TestRequest;

// 构建Thrift客户端对象
$socket = new \Thrift\Transport\TSocket("127.0.0.1", 9503);
$transport = new \Thrift\Transport\TFramedTransport($socket);
$protocol = new \Thrift\Protocol\TBinaryProtocol($transport);
$transport->open();
$client = new ThriftServiceClient($protocol);

// 构建参数
$req = new TestRequest([
    'id' => 1,
    'name' => "test",
    'lists' => [1,2,3]]
);
// 发起一个远程请求
$ret = $client->test3($req, 1); 
var_dump($ret);

$transport->close();
```

