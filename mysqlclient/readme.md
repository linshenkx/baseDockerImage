docker buildx build --platform=linux/arm64,linux/amd64 -t linshen/mysqlclient . --push

docker buildx build --platform=linux/arm64 -t linshen/mysqlclient -o type=docker,dest=- . > mysqlclient.tar

docker buildx build --platform=linux/arm64 -t linshen/mysqlclient -o type=docker .
