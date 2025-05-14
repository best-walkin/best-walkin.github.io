---
# multilingual page pair id, this must pair with translations of this page. (This name must be unique)
lng_pair: id_linux_3
title: Ubuntu22.04安装TightVNC

# post specific
# if not specified, .name will be used from _data/owner/[language].yml
#author: ""
# multiple category is not supported
category: Linux
# multiple tag entries are possible
tags: [Linux]
# thumbnail image for post
img: ":post_pic3.jpg"
# disable comments on this page
comments_disable: false

# publish date
date: 2025-05-14 13:45:08 +0900

# seo
# if not specified, date will be used.
#meta_modify_date: 2021-09-12 13:45:08 +0900
# check the meta_common_description in _data/owner/[language].yml
#meta_description: ""

# optional
# please use the "image_viewer_on" below to enable image viewer for individual pages or posts (_posts/ or [language]/_posts folders).
# image viewer can be enabled or disabled for all posts using the "image_viewer_posts: true" setting in _data/conf/main.yml.
#image_viewer_on: true
# please use the "image_lazy_loader_on" below to enable image lazy loader for individual pages or posts (_posts/ or [language]/_posts folders).
# image lazy loader can be enabled or disabled for all posts using the "image_lazy_loader_posts: true" setting in _data/conf/main.yml.
#image_lazy_loader_on: true
# exclude from on site search
#on_site_search_exclude: true
# exclude from search engines
#search_engine_exclude: true
# to disable this page, simply set published: false or delete this file
#published: false
---

{%- comment -%} Please delete below and place your page content here {%- endcomment -%}

# Ubuntu22.04安装TightVNC
    参考链接https://help.aliyun.com/zh/simple-application-server/use-cases/use-vnc-to-build-guis-on-ubuntu-18-04-and-20-04
## 安装TightVNC
#### 安装所需的包
    sudo apt install gnome-panel gnome-settings-daemon metacity nautilus gnome-terminal ubuntu-desktop
#### 安装TightVNC
    sudo apt install tightvncserver
#### 初始化
    vncserver
    # 这是在个人账户下，非root账户
    # 会提示你输入密码，按要求输入即可。密码的长度必须介于六到八个字符之间，超过 8 个字符的密码将被自动截断。
    # 后续如果修改密码可以通过 vncpasswd 修改
#### 备份配置文件
    cp ~/.vnc/xstartup ~/.vnc/xstartup.bak
#### 修改配置文件
    vi ~/.vnc/xstartup
    # 将内容替换成如下
    #!/bin/sh
    autocutsel -fork
    xrdb $HOME/.Xresources
    xsetroot -solid grey
    export XKL_XMODMAP_DISABLE=1
    export XDG_CURRENT_DESKTOP="GNOME-Flashback:Unity"
    export XDG_MENU_PREFIX="gnome-flashback-"
    unset DBUS_SESSION_BUS_ADDRESS
    gnome-session --session=gnome-flashback-metacity --disable-acceleration-check --debug &
#### 启动VNC
    vncserver :1
    # 这里默认端口为5900，":1"代指5901，依次类推。
#### 关闭VNC
    vncserver -kill :1

## 使用frp内网穿透实现外网访问VNC
    # 原理就是将5901端口转发到外网访问的端口，我这里转发到了20035
    # 修改frpc.toml文件，增加下述内容
    [[proxies]]
    name = "vnc"
    type = "tcp"
    localIP = "127.0.0.1"
    localPort = 5901
    remotePort = 20035
    transport.useEncryption = true   #传输加密，加密算法采用 aes-128-cfb
    transport.useCompression = true
    # 修改frps.toml文件，将20035端口加入



    
     

