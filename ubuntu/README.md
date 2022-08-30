### 构建镜像
```shell
docker buildx build --platform=linux/arm64,linux/amd64  -t linshen/ubuntu .  --push
docker buildx build --platform=linux/arm64,linux/amd64  -t linshen/ubuntu:20.04 .  --push
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

### 普通使用
```shell
docker rm -f ubuntu
docker run -d \
--restart=always \
--name ubuntu \
linshen/ubuntu

```