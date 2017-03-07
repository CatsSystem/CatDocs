# MySQL连接

## 构造Redis客户端
```php
use base\framework\client\MySQL;

$config = Config::get('mysql');
$mysql = new MySQL($config, Constants::MODE_ASYNC);

```

`MySQL`客户端的构造函数接受两个参数，第一个参数是配置数据，第二个参数是运行模式

* Constants::MODE_ASYNC 使用`swoole_mysql`作为驱动
* Constants::MODE_SYNC  使用`mysqli`作为驱动


## 发起请求
MySQL客户端可以通过调用`connect`方法来发起向数据库的连接请求：
```php
use base\framework\client\MySQL;

$config = Config::get('mysql');
// Constants::MODE_ASYNC 指定使用swoole_mysql作为驱动
$mysql = new MySQL($config, Constants::MODE_ASYNC);

// 发起连接，指定id为0，并设置超时时间为3000ms
$result = yield $mysql->connect(0, 3000);
```

`connect`方法接收两个参数，第一个参数是id，第二个参数是超时的毫秒数。`connect`方法返回一个Promise对象，因此可以使用协程获取连接结果。