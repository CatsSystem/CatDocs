# 架构总览

[架构图](http://static.zybuluo.com/Lancelot2014/8defbqb68tmu1a8kt7gohl4v/CatMicro%E7%BB%93%E6%9E%84%E5%9B%BE.001.jpeg)

http://static.zybuluo.com/Lancelot2014/8defbqb68tmu1a8kt7gohl4v/CatMicro%E7%BB%93%E6%9E%84%E5%9B%BE.001.jpeg

CatMicro采用了Swoole的多端口监听功能，主服务提供一个http端口用于接收Admin命令，然后根据配置文件的配置，添加额外的端口用于对外提供服务，每个端口可以定义端口使用的基本协议（tcp，http，websocket）、序列化方式（Hprose、Thrift、Swoole）以及对应的Service服务。
对应每个端口，可以使用相应的客户端进行访问。
