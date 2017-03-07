# Redis请求

Redis客户端实现了`__call`魔术方法，用于将Redis指令映射成方法，将指令所用的参数作为方法的参数调用。

比如调用`set`方法，就可以使用如下代码：

```php
$result = yield $redis->set("key", "value");
```

需要注意的是，Redis客户端屏蔽了`订阅`相关的所有命令。