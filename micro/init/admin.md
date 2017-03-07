# Admin端口

CatMicro框架默认会提供一个http端口对外提供服务，这个端口用于向服务发送Admin指令，开发者可以在主回调类的`onRequest`回调中接收并处理Admin指令。这里仅介绍一些比较简单的用法。

## 获取服务器状态

```php
    public function onRequest(\swoole_http_request $request, \swoole_http_response $response)
    {
        if($request->server['path_info'] == '/stats')
        {
            // 调用stats方法获取服务器状态
            $response->end(json_encode($this->server->stats()));
        }
    }
```

## 重启Worker进程

```php
    public function onRequest(\swoole_http_request $request, \swoole_http_response $response)
    {
        if($request->server['path_info'] == '/reload')
        {
            // 调用reload方法重启Worker
            $this->server->reload();
        }
    }
```

## 停止服务

```php
    public function onRequest(\swoole_http_request $request, \swoole_http_response $response)
    {
        if($request->server['path_info'] == '/shutdown')
        {
            $this->server->shutdown();
        }
    }
```

Admin端口的配置在`config.php`配置文件中的`server`类目中，如下：

```php
return [
    'server' => array(
        'host' => '192.168.0.1',  // 最好是内网IP或者本地IP，避免管理端口被外网攻击
        'port' => 9501,           // 监听端口
    ),
];
```