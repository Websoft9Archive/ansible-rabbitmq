# FAQ

#### Active Classic 与 RabbitMQ Artemis 有什么区别？

RabbitMQ Artemis 是RabbitMQ下一代产品，未来将替换 RabbitMQ Classic。 具体参考：[RabbitMQ Classic](https://activemq.apache.org/getting-started), [RabbitMQ Artemis](https://activemq.apache.org/components/artemis/documentation/)

#### 如何以调试模式启动RabbitMQ服务？

```
systemctl stop activemq
/opt/apache-activemq/bin/activemq console
```

#### 如何修改RabbitMQ后台密码？

密码配置文件 */opt/apache-activemq/conf/jetty-realm.properties*，修改后重启activemq服务后生效

#### 如何退出 RabbitMQ 控制台？

暂无方案

#### 如果没有域名是否可以部署 RabbitMQ？

可以，访问`http://服务器公网IP` 即可

#### RabbitMQ 中是否包含Tomcat？

RabbitMQ 官方提供的二级制包中包含Tomcat，但已经集成到RabbitMQ服务中。

#### 是否可以修改RabbitMQ的源码路径？

可以，但要参考如下的命令重试设置环境变量
```
echo 'export PATH="$PATH:/opt/apache-activemq/bin"' >> /etc/profile
```

#### 如何修改上传的文件权限?

```shell
chown -R activemq.activemq /opt/apache-activemq
find /opt/apache-activemq -type d -exec chmod 750 {} \;
find /opt/apache-activemq -type f -exec chmod 640 {} \;
```
#### 部署和安装有什么区别？

部署是将一序列软件按照不同顺序，先后安装并配置到服务器的过程，是一个复杂的系统工程。  
安装是将单一的软件拷贝到服务器之后，启动安装向导完成初始化配置的过程。  
安装相对于部署来说更简单一些。 

#### 云平台是什么意思？

云平台指提供云计算服务的平台厂家，例如：Azure,AWS,阿里云,华为云,腾讯云等

#### 实例，云服务器，虚拟机，ECS，EC2，CVM，VM有什么区别？

没有区别，只是不同厂家所采用的专业术语，实际上都是云服务器