# CentOS 7.9 Python3.10.9配置ssl

Centos7.9编译安装Python3.10.9后，缺少ssl模块：

```shell
# 缺少ssl模块
$ python
Python 3.10.9 (main, Mar 26 2024, 15:18:07) [GCC 9.3.1 20200408 (Red Hat 9.3.1-2)] on linux
Type "help", "copyright", "credits" or "license" for more information.
>>> import ssl
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
  File "/usr/local/python3/lib/python3.10/ssl.py", line 99, in <module>
    import _ssl             # if we can't import it, let the error propagate
ModuleNotFoundError: No module named '_ssl'
```

使用如下方式编译安装：

```shell
# 安装依赖包
$ sudo yum install zlib-devel bzip2-devel openssl-devel ncurses-devel sqlite-devel readline-devel tk-devel gcc make libffi-devel perl-Test-Simple

$ cd /usr/local/src
$ sudo wget https://github.com/openssl/openssl/releases/download/OpenSSL_1_1_1w/openssl-1.1.1w.tar.gz
$ sudo tar -zxvf openssl-1.1.1w.tar.gz
$ cd openssl-1.1.1w/
$ sudo ./config shared --prefix=/usr/local/openssl --openssldir=/usr/local/openssl
$ sudo make && sudo make test && sudo make install

# 备份系统自带的openssl
$ openssl version
OpenSSL 1.0.2k-fips  26 Jan 2017
$ sudo mv /usr/bin/openssl /usr/bin/openssl.bak
$ sudo ln -s /usr/local/openssl/bin/openssl /usr/bin/openssl
$ sudo ln -s /usr/local/openssl/lib/libssl.so.1.1 /usr/lib/libssl.so.1.1
$ sudo ln -s /usr/local/openssl/lib/libcrypto.so.1.1 /usr/lib/libcrypto.so.1.1

# 配置
$ echo "/usr/local/lib64/" | sudo tee -a /etc/ld.so.conf
$ sudo ldconfig

$ openssl version
OpenSSL 1.1.1w  11 Sep 2023

# 下载python3
$ wget https://www.python.org/ftp/python/3.10.9/Python-3.10.9.tar.xz
# 编译安装
$ tar xf Python-3.10.9.tar.xz
$ cd Python-3.10.9
# 编译安装python配置ssl
$ ./configure prefix=/usr/local/python3 -C --with-openssl=/usr/local/openssl --with-openssl-rpath=auto
$ sudo make && sudo make install

$ sudo ln -s /usr/local/python3/bin/python3 /usr/bin/python
$ sudo ln -s /usr/local/python3/bin/python3.10-config /usr/bin/python3-config
$ python -V
Python 3.10.9
python
Python 3.10.9 (main, Mar 26 2024, 16:42:02) [GCC 9.3.1 20200408 (Red Hat 9.3.1-2)] on linux
Type "help", "copyright", "credits" or "license" for more information.
>>> import ssl
>>> exit()
```
