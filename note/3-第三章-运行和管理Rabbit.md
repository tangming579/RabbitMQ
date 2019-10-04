## 运行和管理Rabbit

### 启动节点

Erlang也是一个虚拟机，虚拟机的每个实例称之为节点（node）。不同于JVM，多个Erlang应用程序可以运行在同一个节点之上。节点之间可以进行本地通信（不管他们是否真的在同一台服务器上）。如果应用程序崩溃了，Erlang节点会自动尝试重启应用程序。

<div>
    <image src="../img/node.png"></image>
</div>

RabbitMQ启动Erlang节点和Rabbit应用程序方式：

```
RabbitMQ安装目录下找到 ./sbin 目录，运行 ./rabbitmq-server
```

如果遇到错误，检查 /lograbbitmq/目录下 rabbit@[hostname].log 的日志

### 停止节点

在RabbitMQ安装目录下运行：

```
./sbin/rabbitmqctl stop
```

也可以指定关闭不同节点，包括远程节点，只需要传入 -n rabbit@[hostname]

**关闭和重启应用程序的差别：**rabbitmq-server 同时启动了节点和应用程序，而 ./rabbitmqctl stop 会把应用程序和节点同时关闭，如果此时再次运行 rabbit-server，又迫使把应用程序和节点同时启动，无法做集群。此时，如果只想停止应用程序，可以执行：

```
./rabbitmqctl stop_app
```

### Rabbit 配置文件

Linux下配置文件的路径为：/etc/rabbitmq/rabbitmq.conf