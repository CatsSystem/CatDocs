# 同步Http客户端

`CURL`客户端使用了`cURL`作为底层驱动，实现了同步发起http请求的功能。

## 构造

`CURL`客户端的构造函数如下所示：

```php
/**
 * Http constructor.
 * @param string    $domain     域名(不带http前缀)或者IP
 * @param bool      $is_ssl     是否开启SSL (https)
 * @param int       $port       端口号,默认80, https默认为443
 */
public function __construct($domain, $is_ssl = false, $port = 80)
```

## 初始化

`CURL`客户端在发起请求前，需要先调用`init`方法。

```php
$result = yield $curl->init();
if($result != Error::SUCCESS)
{
    echo "init failed";
}
```

## 请求设置

> 待开发

## 发起请求

`CURL`客户端可以使用`get`或者`post`方法发起请求。

```php
/**
 * @param string    $path        请求路径 ，例如'/page.html'
 * @param string    $data        请求数据
 * @param int       $timeout     超时时间，单位ms
 * @return Promise
 */
public function post($path, $data, $timeout = 3000)
    
/**
 * @param string    $path       
 * @param int       $timeout
 * @return Promise
 */
public function get($path, $timeout = 3000)
```