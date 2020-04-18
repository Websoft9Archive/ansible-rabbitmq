---
sidebarDepth: 3
---

# 参数

RabbitMQ 预装包包含 RabbitMQ 运行所需一序列支撑软件（简称为“组件”），下面列出主要组件名称、安装路径、配置文件地址、端口、版本等重要的信息。

## 路径

虽然运行 `whereis` 命令可以查看相关安装路径，但接下来我们仍然对路径信息进行更为准确的说明。

```
whereis activemq
whereis java
```

### RabbitMQ

RabbitMQ 安装目录： */opt/activemq/*  
RabbitMQ 配置目录： */opt/apache-activemq/conf*  
RabbitMQ 数据目录： */opt/apache-activemq/data*  
RabbitMQ 日志目录： */opt/apache-activemq/data/activemq.log*

> 通过修改 */opt/apache-activemq/conf/jetty-realm.propertie* 重置管理密码

### Java

Java Directory: */usr/lib/jvm*


## 端口号

在云服务器中，通过 **[安全组设置](https://support.websoft9.com/docs/faq/zh/tech-instance.html)** 来控制（开启或关闭）端口是否可以被外部访问。 

通过命令`netstat -tunlp`查看相关端口，下面列出本应用可能要用到的端口：

| 名称 | 端口号 | 用途 |  必要性 |
| --- | --- | --- | --- |
| HTTP | 8161 | 通过 HTTP 访问 RabbitMQ 控制台 | 可选 |
| TCP | 5672 | amqp | 可选 |

## 版本号

组件版本号可以通过云市场商品页面查看。但部署到您的服务器之后，组件会自动进行更新导致版本号有一定的变化，故精准的版本号请通过在服务器上运行命令查看：

```shell
# Linux Version
lsb_release -a

# Java Version
java -version

# RabbitMQ version
ls /opt/apache-activemq | grep activemq
```