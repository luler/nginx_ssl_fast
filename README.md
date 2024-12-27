# nginx_ssl_fast_test

#### 介绍
快速部署nginx，给ip+端口添加自定义证书访问


#### 配置

1. 修改conf.d下的default.conf，指定后端服务
2. 修改conf.d/certs下的自定义证书（可选）
3. 修改docker-compose.yml文件的端口映射（可选）

#### 启动与使用

```
docker-compose up -d
```

#### 访问测试

访问：https://ip:8443
