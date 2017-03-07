# Service定义

CatMicro框架使用的是Thrift的接口定义，Thrift会给每个定义好的`service`自动生成一个`interface`接口，如下所示：

```php
// 来自 app\processor\ThriftService.php文件
// Thrift自动生成代码

interface ThriftServiceIf {
  /**
   * @param \app\processor\TestRequest $request
   * @return \app\processor\TestResponse
   */
  public function test1(\app\processor\TestRequest $request);
  /**
   * @param string $name
   * @param int $id
   * @return int
   */
  public function test2($name, $id);
  /**
   * @param \app\processor\TestRequest $request
   * @param int $id
   * @return int
   */
  public function test3(\app\processor\TestRequest $request, $id);
}
```

因此，我们定义的Servcie需要实现这个`interface`, 并在对应的接口中填入逻辑代码。

```php
namespace app\service;

use app\processor\ThriftServiceIf;

class ThriftService implements ThriftServiceIf
{
}
```
