# 连接池使用

仍然以MySQL为例，我们通过一段代码来演示如何使用MySQL连接池。

```php

//获取连接池对象
$pool = PoolManager::getInstance()->get('mysql_master');
if(empty($pool))
{
    return;
}

// 从连接池中弹出一个连接
$driver = $pool->pop();
if( $driver instanceof MySQL ) {   // 有空闲连接
    $result = yield $driver->execute("select * from table", false);
    Globals::var_dump($result);
} else {  // 没有空闲连接， 需要等待
    $driver = yield $driver；
    $result = yield $driver->execute("select * from table", false);
    Globals::var_dump($result);
}

```

连接池的`pop`方法会返回两种结果：

* 如果此时连接池有空余连接，则会返回空余连接
* 如果此时连接池没有空余连接，则会返回一个Promise对象，这个Promise对象的`resolve`回调会在有空余连接时被调用，并将空余连接作为`value`传递过来，然后在这里再次发起请求。

