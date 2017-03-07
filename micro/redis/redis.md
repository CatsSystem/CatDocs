# Redis连接

## 构造Redis客户端
```php
use base\framework\client\Redis;

$config = Config::get('redis');
// Constants::MODE_ASYNC 指定使用swoole_redis作为驱动
$redis = new Redis($config, Constants::MODE_ASYNC);

```

`Redis`客户端的构造函数接受两个参数，第一个参数是配置数据，第二个参数是运行模式

* Constants::MODE_ASYNC 使用swoole_redis作为驱动
* Constants::MODE_SYNC  使用phpredis作为驱动

## 发起连接

Redis客户端可以通过调用`connect`方法来发起向数据库的连接请求：


```php
// 发起连接，指定id为0，并设置超时时间为3000ms
$result = yield $mysql->connect(0, 3000);
```

`connect`方法接收两个参数，第一个参数是id，第二个参数是超时的毫秒数。`connect`方法返回一个Promise对象，因此可以使用协程获取连接结果。