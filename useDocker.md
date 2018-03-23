默认各位都安装了Docker CE
- 零、Dockerfile内容
```
FROM node:6.13.1

MAINTAINER mindgravity

WORKDIR /home/node/code

RUN apt-get update \
  && apt-get upgrade -y \
  && npm install -g truffle ganache-cli \
  && cd .. \
  && mkdir code_backup \
  && cd /home/node/code \
  && truffle unbox react \
  && mv /home/node/code/* /home/node/code_backup

EXPOSE 3000
EXPOSE 8545
EXPOSE 9545
```
- 一、拖取镜像
```
docker pull mindgravity/guigulive:latest
```
- 二、启动镜像容器
```
docker run -t -i -p 3000:3000 -p 8545:8545 -p 9545:9545 --mount type=bind,source=/你的宿主机文件路径/code,target=/home/node/code mindgravity/guigulive:latest /bin/bash
```
- 三、复制文件，略过下载react的过程
```
cp -rf /home/node/code_backup/* .
```
- 说明：初学docker，按照视频安装了truffle，unbox了react，但是有些原始的坑没有修改，需要自行debug。
