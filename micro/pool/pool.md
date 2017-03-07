# 连接池配置

CatMicro目前只支持`mysql`和`redis`两种连接池，这些连接池的配置存放于`pool.php`配置文件中。

```php
return [
    /*********************** Pool Config Start ***********************/

    'pool'  => [
        /**
         * MySQL 连接池
         */
        'mysql_master' => [
            'type'  => 'mysql',                 // 连接池类型
            'size'  => 5,                       // 连接池大小

            'args'  => [                        // 连接参数
                'host'      => '127.0.0.1',     // 主机名
                'port'      => 3306,            // 端口号
                'user'      => 'root',          // 用户名
                'password'  => '123456',        // 密码
                'database'  => 'Test'           // 数据库名称
            ]
        ],

        /**
         * Redis 连接池
         */
        'redis_master' => [
            'type'  => 'redis',                 // 连接池类型
            // 'size' => 1,                     // 默认为 1 连接, 无需设置

            'args'  => [
                'host'      => '127.0.0.1',     // 主机名
                'port'      => 6379,            // 端口号
                'select'    => 0,               // 库编号
                'pwd'       => '123456'         // 口令
            ]
        ],
    ]
    /*********************** Pool Config end *************************/
];
```

> 注：同一类型的连接池可以创建多个，通过`key`值来区分。