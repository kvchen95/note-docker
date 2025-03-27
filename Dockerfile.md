```dockerfile
FROM debian:buster

# 换国内源
RUN sed -i 's|http://deb.debian.org/debian|http://mirrors.aliyun.com/debian|g' /etc/apt/sources.list && \
    sed -i 's|http://deb.debian.org/debian|http://mirrors.tuna.tsinghua.edu.cn/debian|g' /etc/apt/sources.list && \
    sed -i 's|http://deb.debian.org/debian|http://mirrors.163.com/debian|g' /etc/apt/sources.list && \
    sed -i 's|http://deb.debian.org/debian|http://mirrors.ustc.edu.cn/debian|g' /etc/apt/sources.list

# 更新软件包列表和安装基本工具
RUN apt-get update && apt-get install -y ca-certificates curl gnupg2 software-properties-common apt-transport-https vim git

# 添加 NodeSource 仓库
RUN curl -sL https://deb.nodesource.com/setup_16.x | bash -

# 安装 Node.js 16.x
RUN apt-get install -y nodejs

# 安装 NVM
RUN curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.39.1/install.sh | bash

# 安装 yarn
RUN npm install -g yarn
RUN npm config set registry http://npm-registry.qunhequnhe.com/
RUN npm i @qunhe/def-next-cli -g

RUN apt-get install -y xdg-utils



# 设置工作目录
WORKDIR /codes

# 添加 FNM 到 PATH
# RUN source ~/.nvm/nvm.sh

# 将宿主机的代码目录挂载到容器中
VOLUME ["/codes"]

# 暴露端口
EXPOSE 7000

# 启动命令
CMD ["bash"]

################
# 宿主机命令行  #
################

# 构建Docker镜像：在d:/apps目录下打开命令行工具，运行以下命令来构建镜像：
# docker build -t fed-env .

# 运行Docker容器
# docker run -it --name fed -v /d/apps:/codes -p 7000:7000 fed-env
```