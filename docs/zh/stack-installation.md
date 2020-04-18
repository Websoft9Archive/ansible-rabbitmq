# 初始化安装

在云服务器上部署 RabbitMQ 预装包之后，请参考下面的步骤快速入门。

## 准备

1. 在云控制台获取您的 **服务器公网IP地址** 
2. 在云控制台安全组中，检查 **Inbound（入）规则** 下的 **TCP:8161** 端口是否开启
3. 若想用域名访问 RabbitMQ，请先到 **域名控制台** 完成一个域名解析

## RabbitMQ 安装向导

1. 使用本地电脑的 Chrome 或 Firefox 浏览器访问网址：*http://域名:8161* 或 *http://Internet IP:8161*, 进入初始化页面
   ![RabbitMQ初始化页面](http://libs.websoft9.com/Websoft9/DocsPicture/zh/activemq/activemq-login-websoft9.png)

2. 点击【Manage RabbitMQ broker】登录RabbitMQ控制台（[不知道账号密码？](/zh/stack-accounts.md#activemq)）
   ![RabbitMQ控制台](http://libs.websoft9.com/Websoft9/DocsPicture/zh/activemq/activemq-logined-websoft9.png)

3. 建议通过 */opt/apache-activemq/conf/jetty-realm.properties* 文件修改默认密码

> 需要了解更多RabbitMQ的使用，请参考官方文档：[Using Apache RabbitMQ](https://activemq.apache.org/using-activemq)

## 常见问题

#### 浏览器打开IP地址，无法访问 RabbitMQ（白屏没有结果）？

您的服务器对应的安全组8161端口没有开启（入规则），导致浏览器无法访问到服务器的任何内容

#### RabbitMQ 服务启动失败？

请确保您的服务器主机名中没有包含"."，例如：activemq5.6 这样的主机名就会导致RabbitMQ服务无法启动  

请通过下面的命令修改:  

```
hostnamectl set-hostname activemq
```
