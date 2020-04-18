# Start or Stop the Services

These commands you must know when you using the RabbitMQ of Websoft9

## RabbitMQ

```shell
sudo systemctl start activemq
sudo systemctl stop activemq
sudo systemctl restart activemq
sudo systemctl status activemq

# you can use this debug mode if RabbitMQ service can't run
/opt/apache-activemq/bin/activemq console
```