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