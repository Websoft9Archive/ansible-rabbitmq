# 故障处理

此处收集使用 RabbitMQ 过程中最常见的故障，供您参考

> 大部分故障与云平台密切相关，如果你可以确认故障的原因是云平台造成的，请参考[云平台文档](https://support.websoft9.com/docs/faq/zh/tech-instance.html)

#### 如何查看错误日志？

日志文件路径为：`/opt/apache-activemq/data/activemq.log`。检索关键词 **Failed** 或者 **error** 查看错误

#### RabbitMQ服务无法启动？

1. 以调试模式运行`activemq console`，便可以查看启动状态和错误
   ```
   /opt/apache-activemq/bin/activemq
   ```
2. 打开日志文件：*/opt/apache-activemq/data/activemq.log*，检索 **failed** 关键词，分析错误原因

3. 常见的无法启动RabbitMQ服务的原因有如下几点：

   * 主机名不符合要求。例如：activemq5.6，这种包含"."的主机名就会导致RabbitMQ无法重启。参考如下命令重置主机名
   ```
   hostnamectl set-hostname activemq
   ```
   * 缺乏Java的环境变量。通过：`echo $JAVA_HOME` 或 `which java` 查看反馈信息。
