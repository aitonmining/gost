

# Mining start





## coin address

### 安装trust metamask

使用google play商店

### 生成地址

```shell
#ETH
ETH:0xECDaE17E2778B032C2474102c9ceB9b29aeBA192

#BabyDoge
BABYDOGE:0xbB112e637559F1fe7A355d439DeB5586D265cc91
#Doge
DOGE:D6ZrMZgAmW1UXVUHgiJbFvW2NqcYaDrf5X
#FTM
FTM:0xbB112e637559F1fe7A355d439DeB5586D265cc91
#MTIC  polygon
MTIC:0xbB112e637559F1fe7A355d439DeB5586D265cc91

#rvn 
RVN:RGvsdJP4xyFzKfaSNXy1dTxddmuq6yHN7F




```

## 系统安装

### 系统更新

```shell
apt update -y
apt install -y curl
apt install -y socat
```





### 申请服务器

购买 AWS

[AWS](https://aws.amazon.com/cn/)





### 购买域名

各个厂家都可以，最好使用国外

[namesilo](https://www.namesilo.com/)   各个博主都在用，不知道为什么

```shel

```

### 进行DNS解析

登陆域名后台，进行解析到服务器上的IP地址



### 安装GOST



```shell
###
#	客户机和服务都进行安装
#
##二进制安装
wget https://github.com/ginuerzh/gost/releases/download/v2.11.1/gost-linux-amd64-2.11.1.gz

gunzip gost-linux-amd64-2.11.1.gz
mkdir /root/gost
mv gost-linux-amd64-2.11.1 /root/gost/gost
chmod +x /root/gost/gost



###################################################################
#源码编译

git clone https://github.com/ginuerzh/gost.git
cd gost/cmd/gost
go build

#####################Docker

docker pull ginuerzh/gost

#########################Ubuntu Store

sudo snap install core
sudo snap install gost




```



### 安装 acme 脚本

```shell
curl https://get.acme.sh | sh

# 申请的证书，两台机器都需求用到
#域名SSL申请
~/.acme.sh/acme.sh --register-account -m 1472638@qq.com~/.acme/acme.sh --issue -d gost.xaiton.uk –standalone
#
~/.acme.sh/acme.sh --installcert -d gost.xaiton.uk --key-file /root/private.key --fullchain-file /root/cert.crt


#对xxx.crt和.xxx.key文件进行openssl转换     也可以不用转换
openssl x509 -in xxxx.xxx.crt -out cert.pem
openssl rsa -in xxxx.xxx.key -out key.pem
#转换成cert.pem和key.pem移动到/root/gost文件下
#并下载到本地保存到一个方便找到的文件夹中备后续本地使用
```



### 配置跳转

```shell
#服务器部分
gost -L="relay+tls://账号:密码@:端口?cert=证书文件&key=私钥"
nohup gost -L="relay+tls://6543:1234@:1310?cert=/root/cert.crt&key=/root/private.key" >>/dev/null 2>&1 &


#客户机部分
gost -L=tcp://:10111/ethash.unmineable.com:3333 -F="relay+tls://6543:1234@gost.xaiton.uk:1310?secure=true&cert=/home/ubuntu/cert.crt"

```

### 挖矿脚本

```shell
./t-rex -a ethash -o stratum+tcp://127.0.0.1:10111 -u ETH:0xECDaE17E2778B032C2474102c9ceB9b29aeBA192.ubuntu24 -p x
pause 
```

