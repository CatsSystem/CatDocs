# Worker进程初始化

CatMicro采用的是Swoole的多进程模型，因此每个Worker进程都需要在进程创建的时候进行初始化操作，用于定义全局静态变量、初始化组件等。这些初始化操作需要在主Callback类中的`onWorkerStart`回调当中执行。

```php
    /**
     * 进程初始化回调, 用于初始化全局变量
     * @param \swoole_websocket_server $server
     * @param $workerId
     */
    public function onWorkerStart($server, $workerId)
    {
    
    }
```

## 初始化连接池

CatMicro的各个连接池需要在`onWorkerStart`中初始化，才能在Service中被调用。

```php
    public function onWorkerStart($server, $workerId)
    {
        PoolManager::getInstance()->init('mysql_master');
        PoolManager::getInstance()->init('redis_master');
    }
```

## 初始化单例

程序中需要使用的单例模型可以放在这里进行初始化，以便后续调用

```php
    public function onWorkerStart($server, $workerId)
    {
        Test::getInstance()->init();
    }
```
