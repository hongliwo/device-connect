# 基于EC2搭建EMQX
该步骤基于EC2来搭建EMQX，还有基于EKS的方案
## 1. 创建EC2实例
在新加坡创建一个EC2实例
- 名称：abx-emqx-develop
- 镜像：Ubuntu 22.04
- 实例：t3.medium
- 密钥对：my_test_ec2_wini10_221110
- 安全组：SSH
- 存储：32GiB / gp3
## 2. 连接EC2
!!!note
    实例ID为：i-0b41045fae70d07ac
    相应的IP可以在实例列表中获得
在MacBook上进行连接
```
cd ~/Key
ssh -i "my_test_ec2_win10_221110.pem" ubuntu@ec2-x-x-x-x.ap-southeast-1.compute.amazonaws.com

vim ~/.screenrc

autodetach          on
crlf                off
deflogin            off
hardcopy_append     on
startup_message     off
termcapinfo linux "ve=\E[?25h\E[?17;0;64c"
vbell               off

defscrollback       4096
silencewait         15

hardstatus alwayslastline "%{=b}%{b}%-w%{.BW}%10>%n*%t%{-}%+w%< %=%{kG} %Y-%m-%d %c:%s"
sorendition gK

altscreen on
```
## 3. 安装EMQX
```
sudo apt update
mkdir -p  projects/emqx
cd projects/emqx
curl -s https://assets.emqx.com/scripts/install-emqx-deb.sh | sudo bash
sudo apt-get install emqx
```
## 4. 启动EMQX
```
sudo systemctl enable emqx
sudo systemctl start emqx
```
## 5. 查看端口占用
```
sudo apt install net-tools
netstat -netpl
```
![[emqx-port-use.png]]
## 6. 创建安全组
SG-EMQX-PORT
![[sg-emqz.png]]
## 7. 修改实例安全组
- 路径：实例->实例状态->安全->更改安全组
- 添加：在关联的安全组搜索框搜索”EMQX“，点击添加安全组
- 保存：点击保存来完成安全组的添加
## 参考网页
### 下载 EMQX 开源版
https://www.emqx.com/zh/downloads-and-install/broker?os=Ubuntu