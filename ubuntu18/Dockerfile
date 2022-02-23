FROM ubuntu:18.04

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

#支持root/123456远程登录 注意：ssh是服务，当cmd启动命令被修改时ssh失效
RUN apt-get install -y libcairo2-dev python3-pip pkg-config python3-dev curl sudo openssh-server nano lsof vim
RUN apt-get install -y

RUN mkdir /var/run/sshd \
    && echo 'root:123456' | chpasswd \
    && sed -i 's/#PermitRootLogin prohibit-password/PermitRootLogin yes/' /etc/ssh/sshd_config
COPY pip.conf /root/.pip/pip.conf

RUN echo "alias pip='pip3'" >> /etc/profile

EXPOSE 22
CMD ["/usr/sbin/sshd","-D"]

# docker build -t linshen/ubuntu18 .