## 概述

百度网盘官方linux版的docker封装。相信外国人对此兴趣不大，所以直接上中文。

本项目来自[john-shine](https://github.com/john-shine/Docker-CodeWeavers_CrossOver-VNC)，仅取个人所需，力求简单实用。在此向作者表示敬意。

项目受众：消费级NAS拥有者，比如某晖、某联通；重度Docker使用者；好奇的小伙伴。

当前运行的百度网盘官方linux版本：3.3.2，base docker image：centos7。


## 快速上手

### pull镜像到本地

`sudo docker pull djangoyi/baidunetdisk:v3.3.2`

### 启动镜像

`sudo docker run -d --privileged -p 5901:5901 -p 6080:6080 djangoyi/baidunetdisk:v3.3.2`

vnc客户端通过5901端口访问容器，浏览器通过6080端口访问容器。`-p`选项至少保留1个，可减少访问容器的麻烦。

### 绑定host的本地目录至容器

`-v /host/path/to/download/folder:/home/baidu/baidunetdiskdownload/`

把`-v`选项添加到`docker run`的命令中。

该目录可作为百度网盘的专用下载目录，在host中就能访问。

> 注意：需要绑定到容器的`/home/baidu/baidunetdiskdownload/`目录，避免可能出现的权限问题（原作者留）

## ENV参数说明

可通过`-e`命令修改部分默认配置

| 名称 | 默认值 | 说明 |
| --- | --- | --- |
| RESOLUTION | 1024x768 | vnc server提供的窗口大小 |
| vnc_password | 无 | 访问vnc server时的密码 |

> 注：`vnc_password`部分为原作者提供，有点存疑，待查。

## 版权声明

本项目引用的“百度网盘官方linux版”归“北京百度网讯科技有限公司”所有。

本项目原始代码来自[john-shine](https://github.com/john-shine/Docker-CodeWeavers_CrossOver-VNC)。
