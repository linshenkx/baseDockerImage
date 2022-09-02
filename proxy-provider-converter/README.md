### 构建镜像
```shell
docker build  --platform=linux/arm64,linux/amd64  -t linshen/proxy-provider-converter .  --push
```
### 运行容器
```shell
docker rm -f ppc
docker run -d \
--restart=always \
--name ppc \
-p 33000:3000 \
linshen/proxy-provider-converter

docker run -d --restart=always --name ppc -p 33000:3000 linshen/proxy-provider-converter

```

