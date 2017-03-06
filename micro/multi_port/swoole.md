# Swoole

Swoole模式采用的序列化方式是[swoole_serialize](https://github.com/swoole/swoole_serialize)。

客户端向一个Swoole模式的端口发起请求时，请求的数据格式如下：

```php
$data = swoole_pack([
    'method' => 'methodName',
    'data' => [
        'arg1' => $arg1_value,
        'arg2' => $arg2_value,
        'arg3' => $arg3_value,
    ]
]);
```

在`http`模式和`websocket`模式下请求时，都可以直接发送上面的数据。在`tcp`模式下，需要在数据前加上一个4字节的`unsigned int`类型用于存放数据长度。

```php
$data = pack('N', strlen($data)) . $data;
```