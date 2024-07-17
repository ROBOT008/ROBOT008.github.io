1、创建docker-compose.yml文件
```
version: '3.8'

services:
  registry-ui:
    image: registry.cn-hangzhou.aliyuncs.com/robot_007/docker-registry-ui:2
    restart: always
    ports:
      - 8899:80
    environment:
      - SINGLE_REGISTRY=true
      - REGISTRY_TITLE=ROBOT007的docker私有仓库
      - DELETE_IMAGES=true
      - SHOW_CONTENT_DIGEST=true
      - NGINX_PROXY_PASS_URL=http://registry-server:5000
      - SHOW_CATALOG_NB_TAGS=true
      - CATALOG_MIN_BRANCHES=1
      - CATALOG_MAX_BRANCHES=1
      - TAGLIST_PAGE_SIZE=100
      - REGISTRY_SECURED=false
      - CATALOG_ELEMENTS_LIMIT=1000
    container_name: registry-ui
  registry-server:
    image: registry.cn-hangzhou.aliyuncs.com/robot_007/registry:latest
    restart: always
    ports:
     - 5000:5000
    environment:
      - REGISTRY_HTTP_HEADERS_ACCESS_CONTROL_ALLOW_ORIGIN=*
    volumes:
      - /root/docker/registry:/var/lib/registry/docker/registry/v2
    container_name: registry-server
```
2、配置docker的http请求问题（Get ~~ http: server gave HTTP response to HTTPS client）
编辑/etc/docker/daemon.json
```
{
 "registry-mirrors":[
   "http://ip:5000"
 ],
 "insecure-registries":["ip:5000"] 
}
```
编辑 /etc/default/docker增加：
```
 DOCKER_OPTS="$DOCKER_OPTS --insecure-registry=ip:5000"
```
3、重启docker
```
systemctl daemon-reload
systemctl restart docker
```
4、启动服务
```
docker-compose up -d
```
5、构建本地镜像
```
docker tag 镜像:版本 ip:5000/镜像:版本
```
6、推送镜像到仓库
```
docker push ip:5000/镜像:版本
```