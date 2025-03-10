

## 先检查环境是否满足要求

1.请输入以下命令下载该组件：
```bash
yum -y install wget
```

2.更换yum源为阿里云
```bash
mv /etc/yum.repos.d/CentOS-Base.repo /etc/yum.repos.d/CentOS-Base.repo.backup

curl -o /etc/yum.repos.d/CentOS-Base.repo https://mirrors.aliyun.com/repo/Centos-7.repo

yum makecache   #生成缓存
```


# 脚本使用方法

## 1. 下载脚本
下载 `install_docker.sh` 脚本：
```bash
wget https://gitee.com/xy12306/Docker/releases/download/v2.0/install_docker.sh
```



**检查当前目录文件**：
输入 `ll` 查看文件内容。


## 2. 赋予脚本执行权限
运行以下命令，赋予脚本可执行权限：
```bash
chmod +x install_docker.sh
```

## 3. 执行脚本
运行以下命令，执行脚本：
```bash
./install_docker.sh
```

---

# 执行过程
脚本会依次执行以下操作：
1. **切换 yum 源为阿里云**：加快软件包下载速度。
2. **安装 Docker**：
    - 安装必要的工具。
    - 添加 Docker 官方源（阿里云镜像）。
    - 安装 Docker 及相关组件。
    - 启动 Docker 服务并设置开机自启。
3. **配置 Docker 镜像加速**：
    - 使用多个国内镜像加速地址。
    - 重启 Docker 服务使配置生效。
4. **检查镜像加速是否生效**：
    - 输出 `docker info` 信息，并检查是否包含镜像加速地址。

---

# 注意事项
1. **系统要求**：
    - 脚本适用于 **CentOS 7** 系统。
    - 若使用其他 Linux 发行版（如 Ubuntu），需调整部分命令。
2. **网络连接**：
    - 确保服务器可正常访问外网，以便下载必要的软件包。
3. **权限问题**：
    - 脚本中部分命令需要 root 权限，请使用 `sudo` 或以 root 用户运行。
4. **镜像加速地址**：
    - 脚本中配置了多个镜像加速地址，若某个地址不可用，可手动修改 `/etc/docker/daemon.json` 文件。

---
参考链接：

* [CentOS 7 环境下的 Docker 安装与配置 详细过程](https://juejin.cn/post/7452652375342874624)