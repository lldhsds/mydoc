# CentOS 7.9 安装配置Python2与Python3共存

CentOS 7.9默认安装的是Python2.7.5版本, 当前主流的python项目多用Python3，同时CentOS中部分工具如yum依赖Python2，因此配置Python3与Python2共存。

安装步骤如下：

```shell
# 查看当前版本
$ python -V
Python 2.7.5
$ which python
/usr/bin/python

$ pip -V
pip 8.1.2 from /usr/lib/python2.7/site-packages (python 2.7)

# 安装依赖
$ sudo yum -y install zlib-devel bzip2-devel openssl-devel ncurses-devel sqlite-devel readline-devel tk-devel gcc make

# 备份当前版本
$ sudo mv /usr/bin/python /usr/bin/python2.7.5                
$ ls /usr/bin/python2
python2      python2.7    python2.7.5

# 下载python3
$ wget https://www.python.org/ftp/python/3.10.9/Python-3.10.9.tar.xz
# 编译安装
$ tar xf Python-3.10.9.tar.xz
$ cd Python-3.10.9
$ ./configure prefix=/usr/local/python3 -C --with-openssl=/usr/local/openssl --with-openssl-rpath=auto
$ sudo make && sudo make install

$ sudo ln -s /usr/local/python3/bin/python3 /usr/bin/python
$ sudo ln -s /usr/local/python3/bin/python3.10-config /usr/bin/python3-config
$ python -V
Python 3.10.9

# 配置yum Python版本，此时yum无法使用
$ sudo yum repolist
  File "/usr/bin/yum", line 30
    except KeyboardInterrupt, e:
           ^^^^^^^^^^^^^^^^^^^^
SyntaxError: multiple exception types must be parenthesized
$ which yum
/usr/bin/yum
# 修改yum主文件第一行，使用python2.7.5
$ sudo vim /usr/bin/yum
#!/usr/bin/python2.7.5

# 此时yum安装软件还会遇到如下错误
Total download size: 422 k
Installed size: 1.0 M
Is this ok [y/d/N]: y
Downloading packages:
  File "/usr/libexec/urlgrabber-ext-down", line 28
    except OSError, e:
           ^^^^^^^^^^
SyntaxError: multiple exception types must be parenthesized


Exiting on user cancel

# 修改库文件urlgrabber-ext-down第一行，使用python2.7.5
$ sudo vim /usr/libexec/urlgrabber-ext-down
#! /usr/bin/python2.7.5

# 测试yum安装软件成功。

# pip3配置
$ sudo ln -s /usr/local/python3/bin/pip3 /usr/bin/pip3
$ pip3 -V
pip 22.3.1 from /usr/local/python3/lib/python3.10/site-packages/pip (python 3.10)
```
