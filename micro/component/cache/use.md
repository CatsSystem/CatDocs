# 调用缓存

`CacheLoader`组件是内存缓存的管理组件，该类是一个单例，位于`base\framework\cache`命名空间下。

使用内存缓存前，需要在主回调类的`onWorkerStart`回调中初始化缓存管理器。

```php
public function onWorkerStart($server, $workerId)
{
    CacheLoader::getInstance()->init();
}
```

之后在Service中使用时，就可以根据每个加载器的ID，获取到对应的缓存内容了。

```php
$cache = CacheLoader::getInstance()->get(Constants::CACHE_TEST);
```