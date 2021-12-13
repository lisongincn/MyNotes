# 设置系统代理

## 开启代理

```console
export proxy="http://192.168.1.5:1080" && export http_proxy=$proxy && export https_proxy=$proxy && export no_proxy="localhost, 127.0.0.1, ::1" #&& export ftp_proxy=$proxy 
```

## 关闭代理

```console
unset http_proxy && unset https_proxy && unset ftp_proxy && unset no_proxy && unset export proxy
```

## 自动设置代理
将命令添加到 ~/.bashrc 文件中

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

#### 解包至当前目录

```console
tar xzvf my.tar
```

# 仓库地址 设置为 中国仓库 (中科大仓库)

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