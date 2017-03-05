# 服务管理

CatMicro框架提供了一个`run.php`脚本用于启动、重启、停止当前服务。

```bash
# 启动服务
php run.php start

# 停止服务
php run.php stop

# 重新启动服务， 并使用release目录下的配置
php run.php restart -c release

# 停止使用release目录下的配置的服务
php run.php stop -c release
```

使用该脚本时，必须保证配置中明确配置了`project.pid_path`配置，并保证运行服务的用户对指定路径有写入权限。