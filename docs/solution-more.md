# More

Each of the following solutions has been proven to be effective and we hope to be helpful to you.

## Configuration 

Refer to the official docs: https://www.rabbitmq.com/configure.html

## Create User

The user for RabbitMQ web console is also the user for RabbitMQ Server. You can use the default administrator user **admin** or create more by RabbitMQ web console

1. Use you local Chrome or Firefox to visit URL: *http://Internet IP:15672*, login to RabbitMQ console
2. Open the 【Admin】>【Add a user】
   ![](https://libs.websoft9.com/Websoft9/DocsPicture/zh/rabbitmq/rabbitmq-createuser-websoft9.png)
3. Set your username, password and tag(Role for RabbitMQ)
4. Created

## Remote connection

You can use the local MQ tools to connect RabbitMQ server remote if you want. 
Following is using the [QueueExplorer](https://www.cogin.com/mq/index.php) to describe the steps for connection:

1. Download and install [QueueExplorer](https://www.cogin.com/mq/download.php)
2. Enable the **TCP:5672** and **TCP:15672** ports of your Security Group of your Cloud Platform
3. Open the QueueExplorer, fill the your credentials for RabbitMQ
   ![](https://libs.websoft9.com/Websoft9/DocsPicture/zh/rabbitmq/queueexplorer-rabbtimq001-websoft9.png)
3. Connect successfully
   ![](https://libs.websoft9.com/Websoft9/DocsPicture/zh/rabbitmq/queueexplorer-rabbtimq002-websoft9.png)
   ![](https://libs.websoft9.com/Websoft9/DocsPicture/zh/rabbitmq/queueexplorer-rabbtimq003-websoft9.png)

If you can't remote connect RabbitMQ, please check the following conditions:

* Enable the **TCP:5672** and **TCP:15672** ports of your Security Group of your Cloud Platform
* The user of RabbitMQ was assigned the suitable role (The user **test** can't connect from remote because it has not been assigned any role in the the picture below)
  ![](https://libs.websoft9.com/Websoft9/DocsPicture/zh/rabbitmq/rabbitmq-createusererror-websoft9.png)

## Config TLS/SSL

RabbitMQ config TLS/SSL, need following 4 steps：

1. Install tls-gen

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

2. Add follow content into `/etc/rabbitmq/rabbitmq.config`

```
ssl_options.cacertfile = /etc/rabbitmq/ssl/ca_certificate.pem
ssl_options.certfile   = /etc/rabbitmq/ssl/server_certificate.pem
ssl_options.keyfile    = /etc/rabbitmq/ssl/server_key.pem
ssl_options.verify     = verify_peer
ssl_options.fail_if_no_peer_cert = false
```
3. Restart RabbitMQ service `systemctl restart rabbitmq`

4. Verification

```
rabbitmq-diagnostics listeners
```