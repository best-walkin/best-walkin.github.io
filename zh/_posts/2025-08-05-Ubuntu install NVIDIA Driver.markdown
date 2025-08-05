---
# multilingual page pair id, this must pair with translations of this page. (This name must be unique)
lng_pair: id_linux_5
title: Ubuntu离线安装NVIDIA驱动

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
date: 2025-08-05 16:45:08 +0900

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

# Ubuntu离线安装NVIDIA驱动
    两块容量大小一致的硬盘
## 安装gcc-12(如果已经安装了可以跳过)
#### 安装gcc-12
    如果没有安装的话会报错

## 安装NIVDIA驱动
##### 从NVIDIA官网下载对应的驱动文件.run格式
    https://www.nvidia.cn/geforce/drivers
##### 查看nouveau驱动
    lsmod | grep nouveau
###### 如果有输出则需要禁用
    vi /etc/modprobe.d/blacklist.conf

    在最后添加如下内容
    blacklist nouveau
    options nouveau modeset=0
###### 更新
    update-initramfs -u
    lsmod | grep nouveau
    没有输出即为成功，有的话可以重启机器尝试
##### 安装NVIDIA驱动
    chmod +x NVIDIA-Linux-x86_64-440.31.run
    sh NVIDIA-Linux-x86_64-440.31.run --no-opengl-files
##### 查看是否成功
    nvidia-smi

    
     

