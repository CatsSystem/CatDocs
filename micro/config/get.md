# 配置获取

CatMicro中提供了一个`Config`组件用于读取配置选项，其使用方法如下：

```php
use base\frameworkd\config\Config;

$name = Config::get('name');
$host = Config::getField('server','host');
```

如果希望返回一个默认值，可以使用如下代码：

```php
use base\frameworkd\config\Config;

$name = Config::get('name', 'test');
$host = Config::getField('server','host', '127.0.0.1');
```

如果前面给定的key不存在，则会将最后一个参数作为默认值返回。

超过2级以上的配置，建议使用读取2级目录后再遍历的方式去获取。

```php
use base\frameworkd\config\Config;

$ports = Config::get('port', []);
foreach($ports as $port)
{
    var_dump($port['host']);
    var_dump($port['port']);
}
```

