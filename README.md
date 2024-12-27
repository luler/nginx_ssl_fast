# nginx_ssl_fast_test

#### 介绍
快速部署nginx，给ip+端口添加自定义证书访问


#### 配置

1. 修改conf.d下的default.conf，修改或增加server配置
```
server {
	listen 8443 ssl default_server;
	#server_name test.com; # 将 your_domain.com 替换为你的域名或 IP 地址

	ssl_certificate /etc/nginx/conf.d/certs/justfortest.com.pem;
	ssl_certificate_key /etc/nginx/conf.d/certs/justfortest.com-key.pem;

	location / {
		proxy_pass http://host.docker.internal:9000;
		proxy_set_header Host $host;
		proxy_set_header X-Real-IP $remote_addr;
		proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
		proxy_set_header X-Forwarded-Proto $scheme;
	}
}
```
2. 修改conf.d/certs下的自定义证书（可选）
3. 修改docker-compose.yml文件的端口映射（可选）

#### 启动与使用

```
docker-compose up -d
```

#### 访问测试

访问：https://ip:8443
