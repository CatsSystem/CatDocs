# 加载器定义

使用内存缓存需要定义缓存加载器，加载器需要放在`cache_path`配置项指定的路径下。

下面是一个加载器实例：

```php
namespace app\cache;

use app\common\Constants;
use base\concurrent\Promise;
use base\framework\cache\ILoader;

class TestCache extends ILoader
{
    /**
     * 初始化加载器, 定义加载器id 和 tick 数量
     */
    public function init()
    {
        $this->id   = Constants::CACHE_TEST;   // 指定id
        $this->tick = 1;                       // 1个tick的时间后刷新
    }

    /**
     * 加载缓存内容
     * @param Promise $promise
     */
    public function load(Promise $promise)
    {
        
        // 加载结果用Promise对象返回
        $promise->resolve([
            'data' => [1,2,3]
        ]);
    }
}
```

一个加载器类需要继承`ILoader`类，并实现`init`和`load`方法。

在`init`方法中，需要给两个成员变量赋值。

* `$this->id`  加载器的ID，唯一且固定，建议声明在`Constants.php`中
* `$this->tick` 经过多少个`cache_tick`时间后刷新一次

`load`方法就是加载内存缓存的方法，缓存刷新时会重新调用该方法加载缓存内容。