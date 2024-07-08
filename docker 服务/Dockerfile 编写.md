Dockerfile 用于构建一个镜像

```Dockerfile
FROM ubuntu:22.04
LABEL image.author="gldwolf"
RUN apt update -y && apt upgrade -y && apt install bin86
COPY target/docker-image.jar /web/services/
CMD ["--server.port", "8080"]                         # 传递可变参数给 ENTRYPOINT
ENTRYPOINT ["java", "-jar", "docker-image.jar"]       # 容器要执行的程序, 参数不可变
ENV JAVA_HOME /usr/bin/jdk-1.8/
EXPOSE 8080 8081 ...
WORKDIR /web/services                                 # 指定工作目录

```