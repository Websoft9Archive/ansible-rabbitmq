# 更多...

下面每一个方案，都经过实践证明行之有效，希望能够对你有帮助

## 配置

参考官方方案：https://www.rabbitmq.com/configure.html

## 创建用户

我们可以把RabbitMQ想象成一个数据库系统，默认提供的admin账号就是最高管理员权限的账号。admin既是登录RabbitMQ Web界面的账号，同时也是RabbitMQ服务的账号。

通过Web界面我们可以创建更多的账号：

1. 本地浏览器Chrome or Fixfox 访问：http://服务器公网IP:15672，登录RabbitMQ后台
2. 依次打开：【Admin】>【Add a user】
   ![](https://libs.websoft9.com/Websoft9/DocsPicture/zh/rabbitmq/rabbitmq-createuser-websoft9.png)
3. 设置好用户名和密码，以及tag（用户角色，必填项）

## 远程连接

用户可以通过本地的MQ工具连接RabbitMQ服务器。下面以[QueueExplorer](https://www.cogin.com/mq/index.php)这款客户端工具为例进行说明：

1. 下载并安装[QueueExplorer](https://www.cogin.com/mq/download.php)
2. 开启云控制台服务器安全组**TCP:5672**和**TCP:15672**端口
3. 打开客户端，填写配置信息
   ![](https://libs.websoft9.com/Websoft9/DocsPicture/zh/rabbitmq/queueexplorer-rabbtimq001-websoft9.png)
3. 连接成功
   ![](https://libs.websoft9.com/Websoft9/DocsPicture/zh/rabbitmq/queueexplorer-rabbtimq002-websoft9.png)
   ![](https://libs.websoft9.com/Websoft9/DocsPicture/zh/rabbitmq/queueexplorer-rabbtimq003-websoft9.png)

如何远程连接失败，请检查如下几点：

* 是否开启云控制台上的安全组**TCP:5672**和**TCP:15672**端口
* 创建的RabbitMQ账号是否分配角色（下图的test用户由于没有分配角色，导致它无法远程连接）
  ![](https://libs.websoft9.com/Websoft9/DocsPicture/zh/rabbitmq/rabbitmq-createusererror-websoft9.png)


## 配置TLS/SSL

RabbitMQ配置TLS/SSL，需要以下4个步骤：

1. 安装tls-gen

```bash
git clone https://github.com/michaelklishin/tls-gen tls-gen
cd tls-gen/basic
# private key password
make PASSWORD=bunnies
make verify
make info
ls -l ./result
cp -r result/ /etc/rabbitmq/ssl/  
```

2. 追加下面内容到配置文件`/etc/rabbitmq/rabbitmq.config`
```
ssl_options.cacertfile = /etc/rabbitmq/ssl/ca_certificate.pem
ssl_options.certfile   = /etc/rabbitmq/ssl/server_certificate.pem
ssl_options.keyfile    = /etc/rabbitmq/ssl/server_key.pem
ssl_options.verify     = verify_peer
ssl_options.fail_if_no_peer_cert = false
```
3. 重启服务`systemctl restart rabbitmq`

4. 验证
```bash
rabbitmq-diagnostics listeners
```