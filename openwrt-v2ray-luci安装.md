# OpenWRT 系统为 v2ray 安装图形界面
# 先要在 系统中安装 luci-compat 程序 (如果已经安装,可以忽略)
## 安装方法
1. 使用 管理界面 安装
   1. 浏览器输入 192.168.1.1 登录管理界面
   2. 系统 > 软件 > 更新列表 > 搜索 "luci-compat"
   3. 安装
2. 使用 命令 安装
   1. ssh 连接到路由器
        ```console
        ssh root@192.168.1.1
        ```
   2. 更新软件列表
        ```console
        apt update
        ```
   3. 安装
        ```console
        apt install luci-compat
        ```
# 安装 luci-app-v2ray 自己系统的
## 下载 luci-app-v2ray
[在这里下载](https://github.com/kuoruan/luci-app-v2ray/releases)
## 安装
1. 进入 管理界面
2. 系统 > 软件 > 上传包 > 安装
- 需要中文支持只需要重复安装操作，下载链接里面有中文支持包