## 镜像
是一种轻量级、可执行的独立软件包，它包含运行某个软件所需的所有内容，我们把应用程序和配置依赖打包好形成一个可交付的运行环境（包含代码、运行时需要的库、环境变量和配置文件等），这个打包好的运行环境就是 `image 镜像文件`

只有通过这个镜像文件才能生成 `Docker` 容器实例（类似 `Java` 中 `new` 出来一个对象）。