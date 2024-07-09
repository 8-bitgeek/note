
## 编写 docker-compose.yml

```yaml
version: '3'

networks:
	my-net:
		driver: bridge
		external: true                 # 是否是已经创建的网络
	my-net2:
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
		depends_on:
			- mysql
			- redis
		networks:
			my-net: 
				ipv4_address: 192.168.192.88  # 指定 ip 
			- my-net2
		volumes:
			- my-data:/var/lib/my-service
			- /var/log/my-service:/var/log/my-service
		devices:
			- /dev/dri/card0:/dev/dri/card0
			- /dev/dri/render0128:/dev/dri/render0128
		deploy:
			resource: 
				limits: 
					cpus: '0.50'
					memory: 512M
				reservations:
					memory: 200M            # 最少需要 200M 内存
		logging:
			driver: json-file/syslog/none
			options:
				syslog-address: "tcp://192.168.192.200:3000"
				max-size: '10m'    # 每个文件最大 10m
				max-file: 10       # 最多 10 个文件
```