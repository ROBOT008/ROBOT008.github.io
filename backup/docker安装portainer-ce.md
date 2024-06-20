1. 登录阿里云获取个人仓库镜像源
2. 拉取Portainer-ce镜像
```
docker pull registry.cn-hangzhou.aliyuncs.com/robot_007/portainer-ce
```
3. 创建仓库并启动
```
docker run -d -p 8000:9000 --name=portainer --restart=always -v /var/run/docker.sock:/var/run/docker.sock -e LANG=zh registry.cn-hangzhou.aliyuncs.com/robot_007/portainer-ce
```
![image](https://video007.oss-cn-shenzhen.aliyuncs.com/github/1.png)