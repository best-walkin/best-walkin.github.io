---
# multilingual page pair id, this must pair with translations of this page. (This name must be unique)
lng_pair: id_linux_3
title: Linux创建RAID1

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
date: 2025-08-05 13:45:08 +0900

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

# Linux创建RAID1
    两块容量大小一致的硬盘
## 安装硬盘
#### 格式化硬盘
##### 查看硬盘
    lsblk
##### 格式化硬盘(我这里硬盘为/dev/sda和/dev/sdb)
    mkfs.ext4 /dev/sda
    mkfs.ext4 /dev/sdb
##### 硬盘分区(由于硬盘大于2T时不能使用fdisk分区，只能使用parted分区)
    # 给硬盘sda分区
    parted /dev/sda
    # 新建磁盘标签类型为GPT
    mklabel gpt
    # 创建分区(整个硬盘就是一个分区)
    mkpart primary 0% 100%
    # 退出
    quit
    # 对/dev/sdb执行相同操作
##### 格式化分区
    mkfs.ext4 /dev/sda1
    mkfs.ext4 /dev/sdb1
##### 查看备份数据是否完整

## 创建RAID
##### 安装mdadm
    apt install mdadm
##### 创建md0硬盘RAID1组
    mdadm --create --verbose /dev/md0 --level=1 --raid-devices=2 /dev/sda1 /dev/sdb1 
##### 查看创建进程(时间比较久，不要关机)
    cat /proc/mdstat


    
     

