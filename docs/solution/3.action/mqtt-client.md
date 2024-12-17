# MQTT客户端
## MQTT客户端介绍
如下为mqtt客户端的介绍
https://docs.emqx.com/zh/emqx/latest/messaging/publish-and-subscribe.html
## 安装MQTT客户端
- 登陆到EMQX的服务器
- 安装mqttx
```
curl -LO https://www.emqx.com/zh/downloads/MQTTX/1.11.1/mqttx-cli-linux-x64
sudo install ./mqttx-cli-linux-x64 /usr/local/bin/mqttx
```
## 订阅消息
通过如下命令订阅消息
```
mqttx sub -t 'testtopic/#' -q 1 -h 'localhost' -p 1883 'public' -v

✔ Connected
✔ Subscribed to testtopic/#
```
参数说明：
- `-t`：订阅主题。
- `-q`：订阅 QoS，默认为 0。
- `-h`：服务器地址，填写对应监听器的 IP 地址，默认为 `localhost`。
- `-p`：服务器端口，默认为 `1883`。
- `-v`：在接收到的 Payload 前显示当前 Topic。

## 发布消息
通过如下命令发布一条消息：
```
mqttx pub -t 'testtopic/1' -q 1 -h 'localhost' -p 1883 -m 'from MQTTX CLI'

✔ Connected
✔ Message published
```
参数说明：
- `-t`：订阅主题。
- `-q`：订阅 QoS，默认为 0。
- `-h`：服务器地址，填写对应监听器的 IP 地址，默认为 `localhost`。
- `-p`：服务器端口，默认为 `1883`。
- `-m`：消息 Payload。
对应订阅端的打印如下：
```
mqtt-packet: Packet {
  cmd: 'publish',
  retain: false,
  qos: 1,
  dup: false,
  length: 30,
  topic: 'testtopic/1',
  payload: <Buffer 66 72 6f 6d 20 4d 51 54 54 58 20 43 4c 49>,
  messageId: 1
}, topic: testtopic/1, qos: 1
from MQTTX CLI
```




## 参考网页
https://mqttx.app/zh/docs/cli/downloading-and-installation
https://docs.emqx.com/zh/emqx/latest/messaging/publish-and-subscribe.html