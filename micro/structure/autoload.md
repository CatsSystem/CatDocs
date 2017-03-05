# 自动加载

CatMicro使用了Composer的`autoload`机制。详细用法可以参考Composer官方文档的定义[autoload](https://getcomposer.org/doc/04-schema.md#autoload)。

在CatMicro项目中，需要在`composer.json`中加入如下定义：

```json
{
    "autoload": {
        "psr-4": {
            "app\\":"app/"
        },
        "classmap": [
            "app/processor"
        ]
    }
}
```

第一组`psr-4`定义是指定项目的`app`目录及其子目录中所有的PHP文件都会遵循PHP的`PSR-4`自动加载规范进行加载。

第二组`classmap`是针对Thrift自动生成文件的加载，会将`app/processor`目录下所有文件中的所有类添加到自动加载路径中。

之后，调用`composer update`生成自动加载文件，并在程序的入口文件中引入Composer的`autoload.php`文件，即可实现自动加载。

> 注：每当`app/processor`目录中的文件有变动时，都需要重新执行`composer update`，才能实现自动加载功能。