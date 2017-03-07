# 连接池初始化

这里我们以一个`MySQL`连接池作为例子来演示如何初始化一个连接池。

首先我们获取到`MySQL`连接池的配置：

```php
$config = Config::getField('pool', 'mysql_master');
```

然后我们创建一个`MySQL`连接池对象：

```php
use base\framework\pool\adapter\MySQL;

$pool = new MySQL();
```

接着，调用初始化方法:

```php
$pool->init();
```

现阶段，连接池的初始化是一个异步操作，还未接入协程。后续版本的更新将引入协程机制。