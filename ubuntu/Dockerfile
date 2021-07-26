FROM ubuntu:20.04

#更新镜像源
RUN sed -i 's/archive.ubuntu.com/mirrors.ustc.edu.cn/g' /etc/apt/sources.list
RUN apt-get update

#修复时区
ENV TZ=Asia/Shanghai \
    DEBIAN_FRONTEND=noninteractive

RUN apt install -y tzdata \
    && ln -fs /usr/share/zoneinfo/${TZ} /etc/localtime \
    && echo ${TZ} > /etc/timezone \
    && dpkg-reconfigure --frontend noninteractive tzdata

#支持root/123456远程登录 注意：ssh是服务，当cmd启动命令被修改时ssh失效
RUN apt-get install -y python3-pip python-is-python3 pkg-config python3-dev curl sudo openssh-server nano lsof vim
RUN mkdir /var/run/sshd \
    && echo 'root:123456' | chpasswd \
    && sed -i 's/#PermitRootLogin prohibit-password/PermitRootLogin yes/' /etc/ssh/sshd_config
COPY pip.conf /root/.pip/pip.conf

RUN echo "alias pip='pip3'" >> /etc/profile

EXPOSE 22
CMD ["/usr/sbin/sshd","-D"]

# docker build -t linshen/ubuntu:20.04 .