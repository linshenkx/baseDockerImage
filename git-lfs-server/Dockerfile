FROM golang:1.14.7

ENV LFS_CONTENTPATH=/data
ENV LFS_ADMINUSER=gitlfs
ENV LFS_ADMINPASS=gitlfs

RUN go env -w GO111MODULE=on
RUN go env -w GOPROXY=https://goproxy.cn,direct
RUN go get github.com/github/lfs-test-server

VOLUME /data
EXPOSE 8080

CMD ./bin/lfs-test-server

# docker build  -t linshen/git-lfs-server .
