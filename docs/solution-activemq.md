# RabbitMQ Web Demos

RabbitMQ comes with a number of Web demos that illustrate how to use the RabbitMQ broker with REST and AJAX. The Web demos are not activated in the default configuration, so you must follow the steps below to get them running:

1. Edit the */opt/apache-activemq/examples/conf/activemq-demo.xml* file and change the `locations` property to reflect the location of the encrypted credentials file, located at */opt/activemq/conf/credentials-enc.properties*:
  ```shell
  <property name="locations">
        <value>file:${activemq.conf}/credentials-enc.properties</value>
  </property>
  ```

2. If the RabbitMQ server is currently running, stop it:
  ```shell
  systemctl stop activemq
  ```

3. Run the example:
  ```shell
  cd /opt/activemq
  sudo ./bin/activemq console xbean:/opt/activemq/examples/conf/activemq-demo.xml
  ```

4. The RabbitMQ broker should now start.
5. Log in to the Web administration panel and view the demos by browsing to *http://Internet IP:8161/demo*, If needed, use the credentials obtained from the server dashboard to log in.