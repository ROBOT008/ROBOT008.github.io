1. 本地登录阿里云docker容器
```
docker login --username=1160468016@qq.com registry.cn-hangzhou.aliyuncs.com
```
2. 项目根目录创建Dockerfile
```
FROM openjdk:8-jdk-alpine
ADD target/${项目名称}.jar /app.jar
CMD ["java", "-jar", "/app.jar"]
```
3. 编译项目（maven项目）
```
mvn install
```
4. 创建docker镜像
```
docker build -t registry.cn-hangzhou.aliyuncs.com/robot_007/${项目名称}:latest .
```
5. 提交docker到容器（例如：阿里云容器）
```
docker push registry.cn-hangzhou.aliyuncs.com/robot_007/${项目名称}:latest
```
6. 拉取镜像
```
docker pull registry.cn-hangzhou.aliyuncs.com/robot_007/${项目名称}
```
7. 创建并启动
```
docker run --name nanzhujian_vm -p 8899:8080 -v /logs/${项目名称}/:/tmp/ -d registry.cn-hangzhou.aliyuncs.com/robot_007/${项目名称}
```