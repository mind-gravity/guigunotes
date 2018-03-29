默认各位都安装了Docker CE
- 零、Dockerfile内容
```
FROM node:6.13.1

MAINTAINER mindgravity

WORKDIR /home/node/code

ADD . /home/node/cache

RUN apt-get update \
  && apt-get upgrade -y \
  && npm install -g webpack webpack-cli \
  && npm install -g truffle ganache-cli \
  && truffle unbox react \
  && npm install --save react@^16.2.0 react-dom@^16.2.0 antd@^3.3.3 \
  && cp -rf /home/node/cache/truffle.js /home/node/code/truffle.js \
  && cp -rf /home/node/cache/getWeb3.js /home/node/code/src/utils/getWeb3.js \
  && rm -rf /home/node/cache/* \
  && mkdir /home/node/code_backup \
  && mv /home/node/code/* /home/node/code_backup

EXPOSE 3000
EXPOSE 8545
EXPOSE 9545
```
- 一、拖取镜像
```
Host$ docker pull mindgravity/guigulive:latest
```
- 二、启动镜像容器，切换到宿主机挂载目录
```
Host$ cd 你的宿主机文件路径/code
Host$ docker run -t -i -p 3000:3000 -p 8545:8545 -p 9545:9545 --mount type=bind,source=/你的宿主机文件路径/code,target=/home/node/code mindgravity/guigulive:latest /bin/bash
```
- 三、复制react文件到本地目录(节约unbox下载react的过程)
（<font color=red>注意！</font>如果你是从第五课开始使用本镜像，请注意备份原开发环境中的contracts、migrations、src、test文件夹内容，以防重置覆盖。）
```
Container$ cp -rf /home/node/code_backup/* .
```
（将已备份的上述文件夹再拷到原位置实现环境更新而本地文件保持原样。）
- 四、像课里那样在另一个终端里启动测试网络
```
Host$ docker exec -it 容器id /bin/bash
Container$ ganache-cli
```
- 说明：初学docker，按照视频安装了truffle，unbox了react，但是有些原始的坑没有修改，需要自行debug。P.S. Host$表示宿主机终端，Container$表示容器内终端。
- 更新lesson5 tag：安装了react 16.2.0；安装了antd 3.3.3；修改了truffle.js和getWeb3.js文件，默认使用ganache的8545端口。将原latest tag改为lesson4。
