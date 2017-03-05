# 命名空间

CatMicro需要使用命名空间来配合自动加载功能。

> 如果不清楚命名空间的基本概念，可以参考PHP手册：[命名空间](http://www.php.net/manual/zh/language.namespaces.php)

特别注意的是，如果你需要调用PHP内置的类库，或者第三方没有使用命名空间的类库，记得在实例化类库的时候加上 \，例如：

```
// 错误的用法
$class = new stdClass();
$xml  =  new SimpleXmlElement($xmlstr);
// 正确的用法
$class = new \stdClass();
$xml  =  new \SimpleXmlElement($xmlstr);
```

在CatMicro中，必须保证命名空间的路径与PHP文件的目录一致，并且PHP文件名和所包含的`class`类名一致，那么就可以实现类的自动加载。

正确的示例：

```php
// 文件路径： app/service
namespace app\service;

// 文件名：MainService.php
class MainService
{

}
```

在使用的时候：

```php
// 在文件开头声明
use app\service\MainService;

// 使用时
$service = new MainService();
```

