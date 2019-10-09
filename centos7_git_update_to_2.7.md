## centos7 update git 
### yum resource  aliyun

### update 
CentOS 自带的git版本太低，需要升级到2.1.2版本以上才能使用gitea。

## 升级方法：

#### 1、安装所需软件包
```
yum install curl-devel expat-devel gettext-devel openssl-devel zlib-devel 
yum install gcc perl-ExtUtils-MakeMaker
```
#### 2、下载&安装
````
cd /usr/src
wget https://www.kernel.org/pub/software/scm/git/git-2.7.3.tar.gz 
tar xzf git-2.7.3.tar.gz
cd git-2.7.3
make prefix=/usr/local/git all
make prefix=/usr/local/git install
````
#### 创建软连接
```
cd /usr/bin
ln -s  /usr/local/git/bin/git git
```
#### 3、检查版本
````
git --version
````
#### o、其他
centos自带Git，7.x版本自带git 1.8.3.1，安装新版本之前需要使用yun remove git卸载。
```
执行make prefix=/usr/local/git all时，可能会报错：make: * [git-credential-store] Error 1，此时可以使用以下命令代替

./configure --without-iconv
make CFLAGS=-liconv prefix=/usr/local/git all
make CFLAGS=-liconv prefix=/usr/local/git install
```