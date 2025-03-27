`docker` 的镜像实际上由一层一层的文件系统组成，这种层级的文件系统 `UnionFS` 。

`bootfs (boot file system)` 主要包含 `bootloader` 和 `kernel` ，`bootloader` 主要是引导加载 `kernel` ，`Linux` 刚启动时会加载 `bootfs` 文件系统， 在 `Docker 镜像` 的最底层是引导文件系统 `bootfs` 。这一层与我们典型的 `Linux / Unix` 系统是一样的，包含 `boot` 加载器和内核。当 `boot` 加载完成之后整个内核就在内存中了，此时内存的使用权已由 `bootfs` 转交给内核，此时系统也会卸载 `bootfs` 。

`rootfs (root file system)`，在 `bootfs` 之上。包含的就是典型 `Linux` 系统中的 `/dev`，`/proc`，`/bin`，`/etc` 等标准目录和文件。`rootfs` 就是各种不同的操作系统发行版，比如 `Ubuntu`，`CentOS` 等。

