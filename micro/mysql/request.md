# MySQL请求

MySQL客户端可以通过调用`execute`方法来发起一个SQL请求：

```php
$result = yield $mysql->execute("select * from table", false , 3000);
```

`execute`方法的原型如下：

```php
/**
 * @param $sql              string  SQL语句
 * @param $get_one          bool    获取1个结果还是获取所有结果
 * @param $timeout          int     超时时间 单位ms       
 * @return Promise
 */
public function MySQL::execute($sql, $get_one, $timeout=3000);
```

`execute`的返回结果是一个数组，其中`code`字段保存了请求的错误码。共分一下4种情况：

* 请求超时   

```
[
    'code' => Error::ERR_MYSQL_TIMEOUT,
]
```

* 请求失败

```
[
    'code'  => Error::ERR_MYSQL_QUERY_FAILED,
    'errno' => "错误信息"
]
```

* 更新请求成功

```
[
    'code'          => Error::SUCCESS,
    'affected_rows' => 1,              // 受影响的行数
    'insert_id'     => 1               // last id
]
```

* 查询请求成功

```
[
    'code'  => Error::ERR_MYSQL_QUERY_FAILED,
    'data'  => [] // 查询结果，数组格式
]
```