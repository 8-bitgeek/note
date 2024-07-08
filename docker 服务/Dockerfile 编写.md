

```Dockerfile
FROM ubuntu:22.04
LABEL image.author="gldwolf"
RUN apt update -y && apt upgrade -y && apt install bin86


```