## 帮助启动类命令

```shell
# === 基于 centos ===
# 启动 docker
systemctl start docker

# 终止 docker
systemctl stop docker

# 重启 docker
systemctl restart docker

# 查看 docker 状态 
systemctl status docker

# docker 开机启动
systemctl enable docker

# 查看 docker 概要信息
docker info

# docker 帮助命令
docker --help
docker <cmd> --help
```

## 镜像命令

```shell
# 查看本地镜像
docker images
docker images [OPTIONS] [REPOSITORY[:TAG]]
# OPTIONS -a 列出本地所有的镜像
#         -q 只显示镜像 id

# 查找远程仓库镜像
docker search [NAME]

# 拉取镜像
docker pull [NAME][:TAG]

# 查看镜像、容器、数据卷所占的空间
docker system df

# 删除镜像
docker rmi (-f) [ID]
# -f force 强制删除
```

## 命令第二弹

```shell
# 启动容器
docker run
# --name="容器新名字" 为容器指定一个名字
# -d (后台运行) 后台运行容器并返回容器 ID, 即启动守护式容器。
# -i 以交互模式运行，通常与 -t 同时使用;
# -t 为容器分配一个伪输入终端，通常与 -i 同时使用;
# -P (大写) 随机 端口映射
# -p 8080:80 指定 端口映射
#    [宿主机port:容器port]

# 查看运行的容器
docker ps
# -a 查看所有容器，包含未运行的容器
# -q 静默模式，只显示容器编号
# -n [number] 显示最近创建的 n 个容器
# -l 显示最近创建的容器
```

## 命令第三弹

```shell
# 退出容器
exit # 容器停止
ctrl + p + q # 容器

# 启动停止停止运行的容器
docker start [ID、NAME]

# 停止容器
docker stop [ID、NAME]

# 杀死 (强制停止) 容器
docker kill [ID、NAME]

# 删除已停止的容器
docker rm [ID]

docker run -it redis # 前台守护式启动
docker run -d redis  # 后台守护式启动
```

## 命令第四弹

```shell
# 查看容器日志
docker logs [ID]

# 查看容器资源资源占用情况
docker top []

# 进入后台的容器
docker exec -it [ID]
docker attach [ID]
# !!! attach 直接进入容器并启动终端，不会启动新的进程，用 exit 退出，会导致容器的停止；
#     exec 在容器中打开新的终端，并且启动新的进程，用 exit 退出，不会导致容器的停止。(推荐使用)
```

## 命令第五弹

```shell
# 将容器内文件拷贝到宿主机
docker cp [ID]:[file_path] [path]

# 导入 导出 整个容器
# export 导出容器的内容留作为一个 tar 归档文件（对应 import 命令）
# import 才 tar 包中的内容创建一个新的文件系统再导入镜像（对应 export）
docker export [ID]>[NAME].tar
cat [NAME].tar | docker import - [镜像用户名]/[镜像名]:[版本号]
```