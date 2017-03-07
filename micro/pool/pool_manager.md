# 连接池管理

CatMicro框架提供了`PoolManager`管理类用于管理各个类型的连接池。

`PoolManager`是个单例，提供了针对连接池的设置和管理，主要提供两个API：

```php
/**
 * @param $name   连接池的名称（对应配置里的key值）
 * @return bool   初始化是否成功
 * @throws \Exception  如果指定的连接池类型不存在，会抛出异常
 */
function PoolManager::init(string $name);
```


```php
/**
 * @param $name 连接池的名称（对应配置里的key值）
 * @return mixed|null  返回连接池对象，不存在则返回空
 */
function PoolManager::get(string $name);
```
