# thrift格式文件

CatMicro框架使用了Thrift的IDL（接口定义语言）来定义接口。Apache Thrift官网上对Thrift IDL的定义可以查看[这里](https://thrift.apache.org/docs/idl)。如果觉得难以理解，可以查看这篇[入门教程](http://www.jianshu.com/p/0f4113d6ec4b)帮助理解。

## 安装Thrift

> 注：本文档仅给出Ubuntu14.04环境下的安装命令，如果使用CentOS或其他操作系统，请自行查找相关lib库的安装命令。Mac系统上推荐使用Homebrew安装对应的库。 


安装Thrift前，需要保证系统中已经安装了如下库或组件：

```bash
apt-get install build-essential autoconf libboost-all-dev libtool glib-2.0 bison flex
```

[Thrift下载地址](https://github.com/apache/thrift/releases)

选择适合自己的Thrift版本下载，并解压到任意目录。在解压后的Thrift目录中，使用如下命令来编译安装：

```bash
./bootstrap.sh 
./configure --prefix=/usr/local/thrift \
--with-boost --with-qt4=no --with-qt5=no \
--with-csharp=no --with-java=no --with-erlang=no \
--with-nodejs=no --with-lua=no --with-perl=no \
--with-dart=no --with-ruby=no --with-haskell=no \
--with-go=no --with-haxe=no --with-d=no
make
make install
```

> 注：如果在编译安装过程中出现错误，可根据错误信息，安装缺失的第三方库，然后重新执行上述命令。

## 编写Thrift文件

在项目目录的`thrift`目录下用于存放编写好的thrift文件。

CatMicro要求所有的thrift文件必须使用以下命名空间：

```thrift
namespace php app.processor
```

除此之外，可以使用任意的Thrift语法定义接口。

## 生成PHP源码

编写好Thrift文件之后，即可使用框架提供的`thrift-gen`脚本统一生成PHP文件。

```bash
cd thrift/
./thrift-gen filename.thrift
```

生成后的PHP文件会存放在项目目录中的`app/processor`路径下。

> 注： 必须将所有的接口定义写在同一个thrift文件内，Thrift会自动将不同的service定义拆分到各个文件中。