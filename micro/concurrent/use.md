# 协程使用

在CatMicro中，可以对任何一个返回Promise对象的函数调用yield关键字，将其作为一个协程调用，Promise对象的结果会直接通过yield返回。

```php
function test_yield()
{
    $promise = new Promise();
    swoole_timer_after(1000, function() use ($promise){
        $promise->resolve("Hello");
    });
    return $promise;
}

// 使用协程的代码需要使用Promise::co()包起来
Promise::co(function(){
    $result = yield test_yield();
    var_dump($result); // 1s后输出 "Hello"， 这1s内进程可以处理其他请求而不会阻塞。
});
```

## 顺序调用

使用如下代码来实现协程的顺序调用：

```php
Promise::co(function(){
	// 协程Redis
	$redis_result = yield $this->redis_pool->pop()->get('cache');
	Globals::var_dump($redis_result);
	
	// 协程MySQL
	$sql_result = yield MySQLStatement::prepare()
	    ->select("Test",  "*")
	    ->limit(0,2)
	    ->query($this->mysql_pool->pop());
	Globals::var_dump($sql_result);
	
	// 协程Async Task
	$result = yield (new AsyncTask('TestTask'))
	    ->test_task(1, "test", [1, 2, 3 ]);
	Globals::var_dump($result);
	
	// 协程Http
	$http = new Http("www.baidu.com");
	yield $http->init();
	$result = yield $http->get('/');
	Globals::var_dump($result);
});
```

## 并发调用
```php
Promise::co(function(){
    // 协程Redis
    $redis_result = $this->redis_pool->pop()->get('cache');
    
    // 协程Async Task
    $http_result = (new AsyncTask('TestTask'))->test_task(1, "test", [1, 2, 3 ]);
    
    // 并行调用
    $result = yield Promise::all([
        $redis_result, $http_result
    ]);
    Globals::var_dump($result);
});
```

## 在Service中使用

在Service中，因为CatMicro底层在调用Service方法前已经使用了`Promise::co`方法，因此无需在Service内部调用该方法，可以直接使用协程。

```php
public function test1()
{
    $redis_result = yield $this->redis_pool->pop()->get('cache');
    Globals::var_dump($redis_result);
}
```