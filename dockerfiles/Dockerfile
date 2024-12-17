# 已构建好的本地镜像 vue环境
# syntax=docker/dockerfile:1.4 版本信息 https://hub.docker.com/r/docker/dockerfile
# Dockerfile 文档 https://docs.docker.com/engine/reference/builder/#usage
# 0.进入项目目录
# 1.构建镜像 docker build -t local_image:nginx --build-arg tag_name=nginx_1.21.5 --no-cache .
# 2.启动镜像 docker run -itd -p 8001:80 --name node_container -v /root/workdir/project/docker-web/dist:/usr/src/dist local_image:nginx
# 3.访问 http://docker主机ip:8841 （如无法访问则排查vue的host设置是否为 0.0.0.0）

ARG tag_name=nginx_1.21.5
FROM registry.cn-hangzhou.aliyuncs.com/padora/ali_docker:${tag_name}
MAINTAINER yuzhou
ENV BUILD_APP_NAME testprofile
WORKDIR /usr/src/dist
VOLUME /usr/src/dist
EXPOSE 80
COPY --chown=root:root ./nginx.conf /etc/nginx/nginx.conf


RUN mkdir -p /usr/src/dist/
RUN mkdir -p /usr/src/volumes/volume/
RUN mkdir -p /usr/src/volumes/bind/
RUN echo "echo to testprofile" > /usr/src/dist/alreadyValue
RUN echo "echo to testprofile" > /usr/src/volumes/volume/alreadyValue
RUN echo "echo to testprofile" > /usr/src/volumes/bind/alreadyValue

# ENTRYPOINT [ "echo", "I have started"]


# -- docker build时执行的
# FROM registry.cn-hangzhou.aliyuncs.com/padora/ali_docker:latest       拉取镜像，本地没有则从配置的远程镜像仓库中拉取
# ARG tag_name=node                                                     构建参数 只会存在于镜像构建过程，启动容器后并不保留这些变量  使用  docker build --build-arg PROFILE=dev 覆盖
# ENV REDIS_VERSION 5.0.3                                               环境变量 启动容器后仍然保留 ${REDIS_VERSION}
# VOLUME [ "/mount/node1", "/mount/node2" ]                             创建容器内部挂载点，要与外部连接挂载点，此参数必须声明
# WORKDIR /app/${BUILD_APP_NAME}                                        启动容器时进入的工作目录
# EXPOSE 8841 8083                                                      声明暴露的端口，容器启动时通过-p与主机去关联
# ONBUILD RUN echo "test"                                               使用ONBUILD命令时，后面跟着的其他命令在当前镜像构建时不会被执行，以其为基础镜像源，构建下级镜像源时才会执行
# COPY --chown=user:group ./ ./						将宿主机文件copy到镜像中 允许本地
# ADD --chown=user:group ./ ./						将宿主机文件copy到镜像中 允许本地和远程link
# RUN npm install                                                       容器内部运行指令 build阶段容器内部

# -- docker run 时执行
# ENTRYPOINT [ "npm", "run" ]                                           docker run 时执行  
# CMD ["start"]                                                         docker run 时执行 拼接在ENTRYPOINT后边，只有最后一个CMD会生效



