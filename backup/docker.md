1. 登录阿里云获取个人仓库镜像源
2. 拉取Portainer-ce镜像
```
docker pull registry.cn-hangzhou.aliyuncs.com/robot_007/mysql:5.7
```
3. 创建仓库并启动
```
docker run --name mysql5.7 -p 3306:3306 -e MYSQL_ROOT_PASSWORD='root1234!@#' -v /root/docker/mysql/data:/var/lib/mysql -v /root/docker/mysql/conf:/etc/mysql/conf.d  -d registry.cn-hangzhou.aliyuncs.com/robot_007/mysql:5.7
```
4.进入容器并设置mysql远程登录
```
docker exec -it mysql5.7 bash
mysql -u root -p
GRANT ALL ON *.* TO 'root'@'%' IDENTIFIED BY 'root1234!@#' WITH GRANT OPTION;
FLUSH PRIVILEGES;
```