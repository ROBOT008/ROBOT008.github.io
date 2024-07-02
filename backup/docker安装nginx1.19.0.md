1. 登录阿里云获取个人仓库镜像源
2. 拉取nginx1.19.0镜像
```
docker pull registry.cn-hangzhou.aliyuncs.com/robot_007/nginx:1.19.0
```

3. 创建仓库并启动
```
docker run --name nginx -p 80:80 -d registry.cn-hangzhou.aliyuncs.com/robot_007/nginx:1.19.0
```

4. 复制文件到宿主电脑
```
docker cp nginx:/etc/nginx/nginx.conf /root/tools/nginx/conf/nginx.conf
docker cp nginx:/etc/nginx/conf.d /root/tools/nginx/conf/conf.d
docker cp nginx:/usr/share/nginx/html /root/tools/nginx/html
docker cp nginx:/var/log/nginx/ /root/tools/nginx/logs
```

5. 重新创建仓库并启动
```
ocker run  --name nginx -d -p 80:80 -v /root/tools/nginx/html:/usr/share/nginx/html -v /root/tools/nginx/conf/nginx.conf:/etc/nginx/nginx.conf -v /root/tools/nginx/logs:/var/log/nginx registry.cn-hangzhou.aliyuncs.com/robot_007/nginx:1.19.0
```