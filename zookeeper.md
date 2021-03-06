### zookeeper安装

* 192.168.0.201(myid=201)
* 192.168.0.202(myid=202)
* 192.168.0.203(myid=203)

##### root用户

```
cd /tmp
wget -N http://mirrors.cnnic.cn/apache/zookeeper/zookeeper-3.4.5/zookeeper-3.4.5.tar.gz
tar -zxf zookeeper-3.4.5.tar.gz
mv ./zookeeper-3.4.5 /opt/zookeeper
mkdir /opt/zookeeper/data
mkdir /opt/zookeeper/logs

vi /opt/zookeeper/conf/zoo.cfg
tickTime=2000 
initLimit=10
syncLimit=5
dataDir=/opt/zookeeper/data
dataLogDir=/opt/zookeeper/logs
clientPort=2181
server.201=192.168.0.201:2888:3888
server.202=192.168.0.202:2888:3888
server.203=192.168.0.203:2888:3888
```

> * 192.168.0.201 `echo '201' > /opt/zookeeper/data/myid`
> * 192.168.0.202 `echo '202' > /opt/zookeeper/data/myid`
> * 192.168.0.203 `echo '203' > /opt/zookeeper/data/myid`

##### 开机启动
`echo '/opt/zookeeper/bin/zkServer.sh start' >> /etc/rc.d/rc.local`

##### 环境变量
`echo 'export PATH=$PATH:/opt/zookeeper/bin' >> /etc/profile`
`source /etc/profile`

##### 常用命令

```
/opt/zookeeper/bin/zkServer.sh start
/opt/zookeeper/bin/zkServer.sh status
/opt/zookeeper/bin/zkServer.sh stop
/opt/zookeeper/bin/zkServer.sh restart
```
