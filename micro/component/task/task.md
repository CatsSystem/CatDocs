# 任务定义

使用异步任务需要定义任务的执行者，代码文件需要放在`task_path`配置项指定的路径下。

下面是一个执行者实例：

```php
namespace app\task;

use base\framework\pool\PoolManager;
use base\framework\task\IRunner;

class TestTask extends IRunner
{
    public function test_task($id, $name)
    {
        return "Hello {$name}";
    }
}
```

执行者需要继承`IRunner`类，然后在该类中任意定义方法作为任务实体，方法的返回值将作为任务执行的结果返回给调用者。

> 在执行者中编写代码跟在Service中编写代码基本，但是需要将`Http`组件用`CURL`组件替换，并且不能再调用异步任务组件。