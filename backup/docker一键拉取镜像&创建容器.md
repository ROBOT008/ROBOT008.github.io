1. 安装[docker环境](https://robot008.github.io/post/Centos-an-zhuang-docker.html)
2. 创建linux脚本（build${项目名称}.sh）
```
echo '-----stop and rm docker ---'
docker stop `docker ps -a |grep ${项目名称}| awk '{print $1}'`
sleep 3
echo '-----rm-----'
docker rm `docker ps -a |grep ${项目名称}| awk '{print $1}'`
sleep 3
echo '-----rmi ----'
docker rmi `docker images |grep ${项目名称}| awk '{print $3}'`
sleep 3
echo '-----pull docker images---'
docker pull registry.cn-hangzhou.aliyuncs.com/robot_007/${项目名称}:test
sleep 3
echo '-----start docker images---'
docker run --name nanzhujian_vm -p 8899:8080 -v /logs/${项目名称}/:/tmp/ -d registry.cn-hangzhou.aliyuncs.com/robot_007/${项目名称}:test
sleep 3
echo '-----start end ----'
docker ps  |grep ${项目名称}
echo '-----look logs'
docker logs -f  `docker ps -a |grep ${项目名称}| awk '{print $1}'`
```