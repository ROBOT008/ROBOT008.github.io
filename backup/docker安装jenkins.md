1. 登录阿里云获取个人仓库镜像源
2. 拉取Jenkins镜像
```
docker pull registry.cn-hangzhou.aliyuncs.com/robot_007/jenkins:lts
```
3. 创建仓库并启动
```
docker run -d -p 8086:8080 -p 50000:50000 -v /root/docker/jenkins/data:/var/jenkins_home  -v /etc/localtime:/etc/localtime -v /usr/bin/docker:/usr/bin/docker     -v /var/run/docker.sock:/var/run/docker.sock   --restart=on-failure  -u 0 --name jenkins-lts registry.cn-hangzhou.aliyuncs.com/robot_007/jenkins:lts
```