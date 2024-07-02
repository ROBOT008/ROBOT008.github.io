1. 删除旧版及本地docker源
```
yum remove docker  docker-client docker-client-latest docker-common docker-latest docker-latest-logrotate docker-logrotate       
 docker-selinux docker-engine-selinux  docker-engine docker-ce
```
2. 安装环境
```
yum install -y yum-utils   device-mapper-persistent-data  lvm2 --skip-broken
```
3. 设置docker镜像源
```
yum-config-manager --add-repo  https://mirrors.aliyun.com/docker-ce/linux/centos/docker-ce.repo
sed -i 's/download.docker.com/mirrors.aliyun.com\/docker-ce/g' /etc/yum.repos.d/docker-ce.repo
yum makecache
```
4. 安装docker
```
yum install -y docker-ce
```
5. 查看安装是否成功
```
docker images
```
6. 启动&配置网关
```
systemctl stop firewalld # 禁止开机启动防火墙
systemctl disable firewalld
systemctl start docker  # 启动docker服务
systemctl stop docker  # 停止docker服务
systemctl restart docker  # 重启docker服务
```