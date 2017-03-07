# Service初始化

每个Service可以定义一个构造函数，这个构造函数会在每个请求进来时执行一次（这也意味着每个请求都独自占用一个Service对象，互相不影响）。开发者可以在这个构造函数内执行初始化逻辑。

```php
class ThriftService implements ThriftServiceIf
{
    private $mysql_pool;
    private $redis_pool;

    public function __construct()
    {
        // 获取连接池对象
        $this->mysql_pool = PoolManager::getInstance()->get('mysql_master');
        $this->redis_pool = PoolManager::getInstance()->get('redis_master');
    }
}

```