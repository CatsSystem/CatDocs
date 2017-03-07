# 任务调用

在Service中可以使用封装好的`AsyncTask`组件发起一个异步任务。

```php
// 创建一个异步任务对象
$task = new AsyncTask('TestTask');
// 执行任务并协程等待返回结果。
$result = yield $task->test_task(1, "test");
Globals::var_dump($result);
```


构造`AsyncTask`时需要传入一个`IRunner`实例的类名，比如这里传入的`TestTask`。
调用时，则直接像调用普通函数一样调用`TestTask`中定义的方法即可。