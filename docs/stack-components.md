# Parameters

The RabbitMQ deployment package contains a sequence software (referred to as "components") required for RabbitMQ to run. The important information such as the component name, installation directory path, configuration file path, port, version, etc. are listed below.

## Path

You can check the file path by the cmd `whereis` of RabbitMQ, and we have prepared more detail for your reference

```
whereis activemq
whereis java
```

### RabbitMQ

RabbitMQ installation directory:  */opt/activemq/*  
RabbitMQ configuration directory:  */opt/apache-activemq/conf*  
RabbitMQ data directory:  */opt/apache-activemq/data*  
RabbitMQ logs directory:  */opt/apache-activemq/data/activemq.log*

> you can reset the administrator password of RabbitMQ by modify the file: */opt/apache-activemq/conf/jetty-realm.propertie* 

### Java

Java Directory: */usr/lib/jvm*

## Ports

You can control(open or shut down) ports by **[Security Group Setting](https://support.websoft9.com/docs/faq/zh/tech-instance.html)** of your Cloud Server whether the port can be accessed from Internet.

You can run the cmd `netstat -tunlp` to list all used ports, and we list the following most useful ports for you:

| Name | Number | Use |  Necessity |
| --- | --- | --- | --- |
| HTTP | 8161 | HTTP requests for RabbitMQ Console| Required |
| HTTPS | 5672 | amqp | Optional |

## Version

You can see the version from product page of Marketplace. However, after being deployed to your server, the components will be automatically updated, resulting in a certain change in the version number. Therefore, the exact version number should be viewed by running the command on the server:

```shell
# Linux Version
lsb_release -a

# Java Version
java -version

# RabbitMQ version
ls /opt/apache-activemq | grep activemq
```