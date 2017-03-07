# Service开发

Service逻辑部分的开发遵循Thrift Service开发的基本逻辑，函数参数为请求参数，函数返回值为请求的响应值。这里只列出一些需要注意的点。

## 打印DEBUG信息

因为在Hprose模式下，CatMicro会屏蔽`var_dump`和`echo`等输出，因此如果需要将调试信息打印到终端中，可以调用`Globals::var_dump()`方法，该方法等效于`var_dump`。

```php
Globals::var_dump($sql_result);
```

