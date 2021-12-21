# 打开 WSL 资源目录
- 在 文件资源管理器的地址栏 中输入 \\wsl$ 就可以打开 WSL 子系统的目录

```console
\\wsl$
```

# 区分大小写

- 在 Windows 中默认是关闭区分大小写的，比如 文件名 a.txt 和 A.txt Windows会认为是同一个文件，只能存在其中一个。
- 如果使用 Linux子系统 并使用 非Linux子系统 文件可能就会出现一些错误，因为 Linux系统 是区分大小写的，也就是 a.txt 和 A.text 是两个不同的文件，可以同时存在。

## 为某个文件夹 开启 区分大小写。

- Windows 可以为某个 文件夹 开启区分大小写功能。

### 检查 是否已经开启

```console
fsutil.exe file queryCaseSensitiveInfo <path> #<path> 替换为路径
```

### 开启或关闭

```console
#开启
fsutil.exe file setCaseSensitiveInfo <path> enable #<path> 替换为路径

#关闭
fsutil.exe file setCaseSensitiveInfo <path> disable #<path> 替换为路径
```

## WSL 设置中文
WSL 尽管已经设置了中文语言但是许多软件依然不能显示为中文，那是因为 WSL 中没有中文字体，需要安装中文字体才能正常显示中文。

> 把 Windows 中的字体复制到 Linux 中，这样比较快，不然安装字体需要下载，有些慢。

# 复制字体文件

```console
sudo ln -s /mnt/c/Windows/Fonts /usr/share/fonts/font
```

# 安装字体管理软件

```console
sudo apt install fontconfig
```

# 刷新字体

```console
sodu fc-cache -fv
```