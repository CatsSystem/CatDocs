# 配置格式

CatMicro的配置文件采用PHP数组形式存放。我们用下面一个例子来展示配置文件的编写规范：

```php
// config.php

return [
    // 1级配置
    'name' => 'cat_micro',
    // 2级配置
    'server' => [
        'host' => '127.0.0.1',
        'port' => 9501 
    ],
    
    // 2级列表配置
    'list' => [
        'item1',
        'item2',
        'item3'
    ],
    
    // 多级配置
    'port' => [
        'hprose' => [
            'host' => '127.0.0.1',
            'port' => 9501 
        ],
        'thrift' => [
            'host' => '127.0.0.1',
            'port' => 9501 
        ],
    ]
];
```

需要注意的是，在配置文件中，第一级配置必须是字符串型key值，并且key值必须唯一（即使在不同配置文件中，也不允许存在同名key值）。

# 固定配置

## config.php

## component.php

## pool.php

## service.php