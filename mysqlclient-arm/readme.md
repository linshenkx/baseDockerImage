docker buildx build --platform=linux/arm64,linux/amd64 -t linshen/mysqlclient-arm . --push

docker buildx build --network=host --platform=linux/arm64 -t linshen/mysqlclient-arm .

docker buildx build --platform=linux/arm64 -t linshen/mysqlclient-arm -o type=docker,dest=- . > mysqlclient-arm.tar

docker buildx build --platform=linux/arm64 -t linshen/mysqlclient-arm -o type=docker .
