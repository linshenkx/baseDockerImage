### 构建镜像
```shell
docker build -t linshen/ubuntu .  && docker push linshen/ubuntu
docker build -t linshen/ubuntu:20.04 .  && docker push linshen/ubuntu:20.04
```
### 运行容器
```shell
docker rm -f my-ubuntu
docker run -d \
--restart=always \
--volume /home/data/ubuntu:/data \
--name my-ubuntu \
-p 15000:15000 \
-p 4022:22 \
linshen/ubuntu
```
### 远程连接
```shell
ssh -p 4022 localhost
```