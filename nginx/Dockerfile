FROM nginx:latest

##修复时区
RUN ln -sf /usr/share/zoneinfo/Asia/Shanghai /etc/localtime && echo 'Asia/Shanghai' >/etc/timezone

#容器对外暴露80端口
EXPOSE 80

CMD ["nginx", "-g", "daemon off;"]

