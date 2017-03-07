# Swoole回调

使用CatMicro框架的程序必须实现一个Callback类，并继承CatMicro提供的一个BaseCallback虚基类。示例代码如下：

```php
// 位于 app/callback 目录下
namespace app\callback;

class MainServer extends BaseCallback
{
    /**
     * 服务启动前执行该回调, 用于添加额外监听端口, 添加额外Process
     */
    public function before_start()
    {
       
    }

    /**
     * 进程初始化回调, 用于初始化全局变量
     * @param \swoole_websocket_server $server
     * @param $workerId
     */
    public function onWorkerStart($server, $workerId)
    {
    
    }

    /**
     * Admin 管理接口, 可自定义管理接口行为
     * @param \swoole_http_request $request
     * @param \swoole_http_response $response
     */
    public function onRequest(\swoole_http_request $request, \swoole_http_response $response)
    {

    }
}
```

并且在`config.php`配置文件中，需要指定该类作为`main_callback`。

```php
return [
    'project' => [
        'main_callback' => '\\app\\callback\\MainServer',
    ]
];
```

在该类中，还可以添加其他Swoole相关的回调函数。具体回调函数的类型和作用请参考Swoole官方文档：[事件回调函数](https://wiki.swoole.com/wiki/page/41.html)。

在这些回调函数中，以下两个回调函数在CatMicro底层做了实现，因此这两个回调无需再次定义：

* onTask
* onFinish

需要注意的是，有一部分回调函数在CatMicro框架内已经有过定义，因此在实现这些回调函数时，需要调用父类的对应函数，例如：

```php
public funciton onStart(\swoole_server $server)
{
    parent::onStart($server);
}
```