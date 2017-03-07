# 缓存配置

内存缓存组件的配置写在`component.php`中，样式如下：

```php
'cache' => [
    'open_cache'    => true,             // 是否开启内存缓存模块
    'cache_tick'    => 10000,            // 缓存刷新的间隔时间,单位为ms
    'cache_path'    => '/app/cache/',    // 缓存更新文件的路径
]
```

