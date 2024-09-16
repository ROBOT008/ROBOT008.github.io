1. 登录阿里云获取个人仓库镜像源
2. 拉取postgresql镜像
```
docker pull registry.cn-hangzhou.aliyuncs.com/robot_007/postgres:alpine3.20
```
3.  创建仓库并启动
```
docker run --name postgresql3.20 --restart=always -d -p 5432:5432 -v /root/docker/postgresql:/var/lib/postgresql/data --shm-size=10g -e POSTGRES_PASSWORD=root1234 registry.cn-hangzhou.aliyuncs.com/robot_007/postgres:alpine3.20
```
4. 开放端口即可访问