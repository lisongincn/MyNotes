# ubuntu基本配置
# 设置中文

ubuntu中有一个语言管理程序,可以通过图形化界面快速设置语言

1. 获得权限

   1. 方法一
   
        ```console
        sudo -i
        ```
   1. 方法二
       
        ```console
        su root
        ```

2. 安装语言管理程序

    ```console
    apt-get install locales
    ```

3. 启动语言管理程序

    ```console
    dpkg-reconfigure locales
    ```

4. 选择并安装要使用的语言 --使用 方向键 空格 回车 操作界面
5. 更新全部软件

    ```console
    apt-get update && apt-get upgrade && apt-get dist-upgrade
    ```

6. 删除已经下载的包

    ```console
    apt-get clean
    ```

7. 重启系统

    ```console
    reboot
    ```
# 允许使用密码登录

甲骨文的主机默认只能使用私钥登录,修改系统中的配置可以用密码登录

1. 使用私钥登录到远程主机
    
    ```console
    ssh -i 私钥所在目录 用户名@主机地址
    ```

1. 切换到 root 用户
    
    ```console
    sudo -i
    ```
1. 为用户设置一个密码 (没有密码拿命登录)
    
    ```console
    sudo passwd 用户名
    ```

1. 修改 sshd_config 配置文件
    1. 使用 vim 编辑器编辑 sshd_config文件

        ```console
        vi /etc/ssh/sshd_config
        ```

    1. 将文件中的这几个 配置值 修改成这个

        ```config
        PermitRootLogin yes
        UsePAM yes
        ```

    1. 保存并退出

        ```console
        :wq!
        ```

        - 命令中 "!" 符号放在最后面，不然会出错，我也不知道为什么

2. 重启 sshd 服务

    ```console
    sudo service ssh restart
    ```

2. 使用设置的密码重新登录

    ```console
    ssh 用户名@主机地址
    ```