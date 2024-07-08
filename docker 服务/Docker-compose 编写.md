
## 编写 docker-compose.yml

```yaml
version: '3'

networks:
	my-net:
		driver: bridge

volumes:
	my-data:
	driver: local

services:
    my-service:
	    image: ubuntu:22.04
	    hostname: myservice
	    container_name: my-service
	    restart: unless-stopped
	    ports: 
		    - 8090: 9080
		environment:
			- TZ='Asia/Shanghai'
		command:
			- '--server.port=8080'      # 替换 Dockerfile 中的 CMD 中的参数
	    extra_hosts:
		    - 'hs:192.168.192.1'
		networks:
			- 
```