1. 登录阿里云获取个人仓库镜像源
2. 拉取sqlserver镜像
```
docker pull registry.cn-hangzhou.aliyuncs.com/robot_007/server:2019-latest
``` 
3. 创建仓库并启动
```
docker run -e "ACCEPT_EULA=Y" -e 'SA_PASSWORD=root1234!@#' -p 1433:1433 --name sqlserver2019 -d registry.cn-hangzhou.aliyuncs.com/robot_007/server:2019-latest
```
