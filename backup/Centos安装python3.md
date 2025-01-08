1. 更新系统包及其依赖项
```
sudo yum update
```
2. 安装编译Python所需的依赖项
```
sudo yum groupinstall -y "Development Tools"
sudo yum install -y zlib-devel bzip2-devel openssl-devel ncurses-devel sqlite-devel readline-devel tk-devel gdbm-devel db4-devel libpcap-devel xz-devel libffi-devel
```
3. 下载Python 3.11.6源代码
```
wget https://www.python.org/ftp/python/3.11.6/Python-3.11.6.tgz
```
4. 解压下载的源码包
```
tar xvf Python-3.11.6.tgz
```
5. 编译并安装Python 3.11.6
```
cd Python-3.11.6
./configure --enable-optimizations
make altinstall
```
6. 验证Python 3.11.6安装
```
python3.11 --version
```
7. 指定新安装的Python版本
```
sudo update-alternatives --install /usr/bin/python python /usr/local/bin/python3.11 1
sudo update-alternatives --config python

```