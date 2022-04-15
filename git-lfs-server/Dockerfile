FROM golang

ENV GOPROXY="https://goproxy.cn"

ENV LFS_CONTENTPATH=/data
ENV LFS_ADMINUSER=gitlfs
ENV LFS_ADMINPASS=gitlfs

RUN go install github.com/github/lfs-test-server@latest

VOLUME /data
EXPOSE 8080

CMD ./bin/lfs-test-server

# docker build  --network=host  -t linshen/git-lfs-server .
