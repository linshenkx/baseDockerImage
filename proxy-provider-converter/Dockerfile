FROM ubuntu:20.04

#更新镜像源
RUN cp -a /etc/apt/sources.list /etc/apt/sources.list.bak \
    && sed -i "s@http://.*archive.ubuntu.com@http://repo.huaweicloud.com@g" /etc/apt/sources.list \
    && sed -i "s@http://.*security.ubuntu.com@http://repo.huaweicloud.com@g" /etc/apt/sources.list \
    && apt-get update

#修复时区
ENV TZ=Asia/Shanghai \
    DEBIAN_FRONTEND=noninteractive

RUN apt install -y tzdata \
    && ln -fs /usr/share/zoneinfo/${TZ} /etc/localtime \
    && echo ${TZ} > /etc/timezone \
    && dpkg-reconfigure --frontend noninteractive tzdata

RUN apt-get install -y curl sudo nano lsof vim net-tools git

RUN curl -fsSL https://deb.nodesource.com/setup_18.x | sudo -E bash - \
    && apt-get install -y  nodejs

RUN cd /opt/ && git clone https://github.com/qier222/proxy-provider-converter.git

RUN cd /opt/proxy-provider-converter && npm -v \
    && npm install \
    && npm run build

WORKDIR /opt/proxy-provider-converter

CMD ["npm","start"]

EXPOSE 3000


