# Troubleshooting

We collect the most common troubleshooting of using RabbitMQ for your reference:

#### How can I use the logs?

You can find the keywords **Failed** or **error** from the logs file: `/opt/apache-activemq/data/activemq.log`

#### RabbitMQ service can't start?

1. Use the debug mode of `activemq console` and you can see the errors
   ```
   /opt/apache-activemq/bin/activemq
   ```
2. Search the keywords **Failed** or **error** in the log file: */opt/apache-activemq/data/activemq.log*

3. The most common reasons are as follows:

   * The hostname have "." string, e.g: activemq5.6, you must rename it and restart the service by the following commands
   ```
   hostnamectl set-hostname activemq
   systemctl restart activemq
   ```
   * Java environment variable problem. you can use the command `echo $JAVA_HOME` or `which java` to check it