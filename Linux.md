# 1. Linux 简介

![image-20240319162324638](https://raw.githubusercontent.com/normalSp/imgSave/master/image-20240319162324638.png)



# 2. Linux 安装

![image-20240322145850602](https://raw.githubusercontent.com/normalSp/imgSave/master/image-20240322145850602.png)

![image-20240322150339018](https://raw.githubusercontent.com/normalSp/imgSave/master/image-20240322150339018.png)

## 2.1 目录特点

![image-20240322152234126](https://raw.githubusercontent.com/normalSp/imgSave/master/image-20240322152234126.png)

![image-20240322152358125](https://raw.githubusercontent.com/normalSp/imgSave/master/image-20240322152358125.png)



# 3. Linux 命令

![image-20240322152939197](https://raw.githubusercontent.com/normalSp/imgSave/master/image-20240322152939197.png)

![image-20240322153110324](https://raw.githubusercontent.com/normalSp/imgSave/master/image-20240322153110324.png)

![image-20240322153632020](https://raw.githubusercontent.com/normalSp/imgSave/master/image-20240322153632020.png)

![image-20240322153835108](https://raw.githubusercontent.com/normalSp/imgSave/master/image-20240322153835108.png)

## 3.1 文件目录操作命令

![image-20240322154055574](https://raw.githubusercontent.com/normalSp/imgSave/master/image-20240322154055574.png)

![image-20240322154236231](https://raw.githubusercontent.com/normalSp/imgSave/master/image-20240322154236231.png)

![image-20240322154922310](https://raw.githubusercontent.com/normalSp/imgSave/master/image-20240322154922310.png)

![image-20240322155354538](https://raw.githubusercontent.com/normalSp/imgSave/master/image-20240322155354538.png)

![image-20240322155516047](https://raw.githubusercontent.com/normalSp/imgSave/master/image-20240322155516047.png)

![image-20240322155818834](https://raw.githubusercontent.com/normalSp/imgSave/master/image-20240322155818834.png)

![image-20240322155947057](https://raw.githubusercontent.com/normalSp/imgSave/master/image-20240322155947057.png)

![image-20240322160114914](https://raw.githubusercontent.com/normalSp/imgSave/master/image-20240322160114914.png)



## 3.2 拷贝移动命令

![image-20240322160310366](https://raw.githubusercontent.com/normalSp/imgSave/master/image-20240322160310366.png)

![image-20240322161459093](https://raw.githubusercontent.com/normalSp/imgSave/master/image-20240322161459093.png)

## 3.3 打包压缩命令

![image-20240322161706798](https://raw.githubusercontent.com/normalSp/imgSave/master/image-20240322161706798.png)

![image-20240322163120410](https://raw.githubusercontent.com/normalSp/imgSave/master/image-20240322163120410.png)



## 3.4 文本编辑命令 Vi / Vim

![image-20240322163255951](https://raw.githubusercontent.com/normalSp/imgSave/master/image-20240322163255951.png)

![image-20240322163404699](https://raw.githubusercontent.com/normalSp/imgSave/master/image-20240322163404699.png)

![image-20240322163525698](https://raw.githubusercontent.com/normalSp/imgSave/master/image-20240322163525698.png)

![image-20240322163626471](https://raw.githubusercontent.com/normalSp/imgSave/master/image-20240322163626471.png)

![image-20240322163736837](https://raw.githubusercontent.com/normalSp/imgSave/master/image-20240322163736837.png)



## 3.5 查找命令

![image-20240322164103327](https://raw.githubusercontent.com/normalSp/imgSave/master/image-20240322164103327.png)

![image-20240322164145286](https://raw.githubusercontent.com/normalSp/imgSave/master/image-20240322164145286.png)

grep 区分大小写



# 4. 软件安装

## 4.1 软件安装方式

![image-20240322164509301](https://raw.githubusercontent.com/normalSp/imgSave/master/image-20240322164509301.png)



## 4.2 安装jdk、tomcat

![image-20240322164642626](https://raw.githubusercontent.com/normalSp/imgSave/master/image-20240322164642626.png)

![image-20240322165515974](https://raw.githubusercontent.com/normalSp/imgSave/master/image-20240322165515974.png)

![image-20240322165903834](https://raw.githubusercontent.com/normalSp/imgSave/master/image-20240322165903834.png)

![image-20240322170500728](https://raw.githubusercontent.com/normalSp/imgSave/master/image-20240322170500728.png)

![image-20240325091421048](https://raw.githubusercontent.com/normalSp/imgSave/master/image-20240325091421048.png)



## 4.3 安装MySQL

![image-20240325091527870](https://raw.githubusercontent.com/normalSp/imgSave/master/image-20240325091527870.png)

![image-20240325091753501](https://raw.githubusercontent.com/normalSp/imgSave/master/image-20240325091753501.png)

![image-20240325091845752](https://raw.githubusercontent.com/normalSp/imgSave/master/image-20240325091845752.png)

![image-20240325092403427](https://raw.githubusercontent.com/normalSp/imgSave/master/image-20240325092403427.png)

**阿里云服务器安装时若提示：**

[root@iZ2zedbyxwi8py5tqfo2haZ mysql]# rpm -ivh mysql-community-server-5.7.25-1.el7.x86_64.rpm
警告：mysql-community-server-5.7.25-1.el7.x86_64.rpm: 头V3 DSA/SHA1 Signature, 密钥 ID 5072e1f5: NOKEY
错误：依赖检测失败：
        libaio.so.1()(64bit) 被 mysql-community-server-5.7.25-1.el7.x86_64 需要
        libaio.so.1(LIBAIO_0.1)(64bit) 被 mysql-community-server-5.7.25-1.el7.x86_64 需要
        libaio.so.1(LIBAIO_0.4)(64bit) 被 mysql-community-server-5.7.25-1.el7.x86_64 需要

**安装：yum install libaio**

![image-20240325093358548](https://raw.githubusercontent.com/normalSp/imgSave/master/image-20240325093358548.png)

![image-20240325094643951](https://raw.githubusercontent.com/normalSp/imgSave/master/image-20240325094643951.png)

![image-20240325094820023](https://raw.githubusercontent.com/normalSp/imgSave/master/image-20240325094820023.png)



## 4.4 安装lrzsz

![image-20240325101942215](https://raw.githubusercontent.com/normalSp/imgSave/master/image-20240325101942215.png)

输入rz便可以进行文件上传



# 5. 项目部署

## 5.1 手工部署

![image-20240325103404721](https://raw.githubusercontent.com/normalSp/imgSave/master/image-20240325103404721.png)

![image-20240325103435672](https://raw.githubusercontent.com/normalSp/imgSave/master/image-20240325103435672.png)

![image-20240325103517894](https://raw.githubusercontent.com/normalSp/imgSave/master/image-20240325103517894.png)

![image-20240325103644518](https://raw.githubusercontent.com/normalSp/imgSave/master/image-20240325103644518.png)

![image-20240325103655883](https://raw.githubusercontent.com/normalSp/imgSave/master/image-20240325103655883.png)

![image-20240325104034345](https://raw.githubusercontent.com/normalSp/imgSave/master/image-20240325104034345.png)



## 5.2 shell 脚本自动部署

![image-20240325104210493](https://raw.githubusercontent.com/normalSp/imgSave/master/image-20240325104210493.png)

![image-20240325104348420](https://raw.githubusercontent.com/normalSp/imgSave/master/image-20240325104348420.png)

![image-20240325104642223](https://raw.githubusercontent.com/normalSp/imgSave/master/image-20240325104642223.png)

#!/bin/sh
echo =================================
echo  自动化部署脚本启动
echo =================================

echo 停止原来运行中的工程
APP_NAME=helloworld

tpid=`ps -ef|grep $APP_NAME|grep -v grep|grep -v kill|awk '{print $2}'`
if [ ${tpid} ]; then
    echo 'Stop Process...'
    kill -15 $tpid
fi
sleep 2
tpid=`ps -ef|grep $APP_NAME|grep -v grep|grep -v kill|awk '{print $2}'`
if [ ${tpid} ]; then
    echo 'Kill Process!'
    kill -9 $tpid
else
    echo 'Stop Success!'
fi

echo 准备从Git仓库拉取最新代码
cd /usr/local/helloworld

echo 开始从Git仓库拉取最新代码
git pull
echo 代码拉取完成

echo 开始打包
output=`mvn clean package -Dmaven.test.skip=true`

cd target

echo 启动项目
nohup java -jar helloworld-1.0-SNAPSHOT.jar &> helloworld.log &
echo 项目启动完成

![image-20240325105603239](https://raw.githubusercontent.com/normalSp/imgSave/master/image-20240325105603239.png)

![image-20240325110439778](https://raw.githubusercontent.com/normalSp/imgSave/master/image-20240325110439778.png)

![image-20240325110705326](https://raw.githubusercontent.com/normalSp/imgSave/master/image-20240325110705326.png)

![image-20240325110934671](https://raw.githubusercontent.com/normalSp/imgSave/master/image-20240325110934671.png)

![image-20240325111307253](https://raw.githubusercontent.com/normalSp/imgSave/master/image-20240325111307253.png)

**详情：https://www.bilibili.com/video/BV13a411q753?p=141&spm_id_from=pageDriver&vd_source=542979c6bdb106fd23293c7648d31688**

**9分48**

按道理用的云服务器不存在这个问题

![image-20240325111555667](https://raw.githubusercontent.com/normalSp/imgSave/master/image-20240325111555667.png)

