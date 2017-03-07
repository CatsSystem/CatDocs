# 前置操作

CatMicro在主Callback类中提供了一个前置操作函数`before_start`。该函数会在调用`$server->start()`前执行，用于处理一些特殊逻辑。

## 添加进程

Swoole扩展允许在程序运行前，调用`$server->addProcess`添加一个`swoole_process`进程到服务中，用于处理一些逻辑。`swoole_process`的相关教程见[Process详解](https://www.zybuluo.com/Lancelot2014/note/538684)。

```php
    public function before_start()
    {
        $process = new \swoole_process(function(\swoole_process $worker) use ($init_callback) {
            // 设置进程名
            Globals::setProcessName(Config::get('project_name') . " timer process");
            // 开启一个定时器执行任务
            swoole_timer_tick(1000, function(){
                Globals::var_dump("Hello");
            });
        }, false, false);
        $this->server->addProcess($process);
    }
```

CatMicro内置了一些封装好的进程，比如缓存更新进程等，这些进程可以使用如下代码进行开启：

```php
    public function before_start()
    {
        // 打开内存Cache进程
        $this->open_cache_process(function(){
            // 初始化MySQL连接池
            PoolManager::getInstance()->init('mysql_master');
            // 初始化Redis连接池
            PoolManager::getInstance()->init('redis_master');
        });
    }
```
