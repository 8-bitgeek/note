## 1. 配置 daemon 代理

在 docker v23.0 及以后, 可以通过配置 daemon.json 来实现 daemon 的代理: 

```json
{
  "proxies": {
    "http-proxy": "http://proxy:7890",
    "https-proxy": "http://proxy:7890",
    "no-proxy": "*.test.example.com,.example.org,127.0.0.0/8"  # 不走代理的网站
  }
}
```