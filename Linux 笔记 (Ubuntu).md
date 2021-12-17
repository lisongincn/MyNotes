# 目录

- [目录](#目录)
- [设置系统代理](#设置系统代理)
  - [开启代理](#开启代理)
  - [关闭代理](#关闭代理)
  - [自动设置代理](#自动设置代理)
- [设置中国仓库 (中科大仓库)](#设置中国仓库-中科大仓库)
- [设置中文](#设置中文)
- [允许使用密码登录](#允许使用密码登录)
- [设置 Tabel键 自动补全时忽略大小写](#设置-tabel键-自动补全时忽略大小写)
- [打包文件/文件夹](#打包文件文件夹)
  - [tar](#tar)
    - [单个文件压缩打包](#单个文件压缩打包)
    - [多个文件压缩打包](#多个文件压缩打包)
    - [单个目录压缩打包](#单个目录压缩打包)
    - [多个目录压缩打包](#多个目录压缩打包)
    - [解包至当前目录](#解包至当前目录)
- [更新 CA 证书](#更新-ca-证书)
  - [更新证书](#更新证书)


# 设置系统代理

## 开启代理

```console
export proxy="http://127.0.0.1:1080" && export http_proxy=$proxy && export https_proxy=$proxy && export no_proxy="localhost, 127.0.0.1, ::1" #&& export ftp_proxy=$proxy
```

## 关闭代理

```console
unset http_proxy && unset https_proxy && unset ftp_proxy && unset no_proxy && unset export proxy
```

## 自动设置代理

将命令添加到 ~/.bashrc 文件中

# 设置中国仓库 (中科大仓库)

```console
sudo sed -i 's/archive.ubuntu.com/mirrors.ustc.edu.cn/g' /etc/apt/sources.list && apt update && apt upgrade
```

# 设置中文

1. 安装语言管理程序

    ```console
    apt-get install locales
    ```

2. 启动语言管理程序

    ```console
    dpkg-reconfigure locales
    ```

3. 更新全部软件

    ```console
    apt-get update && apt-get upgrade && apt-get dist-upgrade
    ```

4. 删除已经下载的包

    ```console
    apt-get clean
    ```

5. 重启系统

    ```console
    reboot
    ```

# 允许使用密码登录

1. 使用私钥登录到远程主机
    
    ```console
    ssh -i 私钥所在目录 用户名@主机地址
    ```

2. 切换到 root 用户
    
    ```console
    sudo -i
    ```
3. 为用户设置一个密码 (没有密码拿命登录)
    
    ```console
    sudo passwd 用户名
    ```

4. 修改 sshd_config 配置文件
    1. 使用 vim 编辑器编辑 sshd_config文件

        ```console
        vi /etc/ssh/sshd_config
        ```

    2. 将文件中的这几个 配置值 修改成这个

        ```config
        PermitRootLogin yes
        UsePAM no
        ```

    3. 保存并退出

        ```console
        :wq!
        ```

        - 命令中 "!" 符号放在最后面，不然会出错，我也不知道为什么

5. 重启 sshd 服务

    ```console
    sudo service ssh restart
    ```

6. 使用设置的密码重新登录

    ```console
    ssh 用户名@主机地址
    ```

# 设置 Tabel键 自动补全时忽略大小写

```console
vi ~/.inputrc #创建或编辑 .inputrc 文件
set completion-ignore-case on #添加一行命令
:wq #保存并且退出
exit #退出终端
```

# 打包文件/文件夹
## tar

tar命令可以用来压缩打包单文件、多个文件、单个目录、多个目录。

### 单个文件压缩打包 

```console
tar czvf my.tar file1
```

### 多个文件压缩打包

```console
tar czvf my.tar file1 file2,...
```

### 单个目录压缩打包

```console
tar czvf my.tar dir1
```

### 多个目录压缩打包

```console
tar czvf my.tar dir1 dir2
```

### 解包至当前目录

```console
tar xzvf my.tar
```

# 更新 CA 证书

- 在访问需要 HTTPS协议 的服务时会验证 CA证书，如果你的证书已经过期了，可能会无法访问。
- 比如：
  - wget https://xxxx.com/xxx/xxx.zip
  - curl https://xxxx.com/xxx/xxx.zip
  - git clone https://github.com/xxx/xxx/

## 更新证书

```console
sudo apt-get install apt-transport-https ca-certificates -y
sudo update-ca-certificates
```