---
# multilingual page pair id, this must pair with translations of this page. (This name must be unique)
lng_pair: id_linux_7
title: Linux添加新硬盘扩展/home容量

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
date: 2025-05-11 13:45:08 +0900

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

# Linux添加新硬盘扩展/home容量
    机器中已有两块硬盘，一块为系统盘，一块为存储/home目录的存储盘(sdc)
## 备份数据(新移动硬盘备份)
#### 格式化新移动硬盘
##### 查看移动硬盘
    lsblk
##### 格式化移动硬盘(我这里移动硬盘为/dev/sda)
    # 因为我要备份/home目录内容，所以格式化移动硬盘为ext4格式
    mkfs.ext4 /dev/sda
##### 备份/home目录下内容
    # 挂载硬盘
    mount /dev/sda /media/backup
    # 复制/home 到 /media/backup
    cp -rv /home /media/backup
    # 或者使用rsync (十分推荐)
    rsync -Paz /home /media/backup
##### 取消挂载移动硬盘
    umount /dev/sda
##### 查看备份数据是否完整

## 安装新硬盘
##### 格式化新硬盘为ext4(新增硬盘为/dev/sdb)
    mkfs.ext4 /dev/sdb
##### 将新增硬盘初始化为LVM物理卷
    pvcreate /dev/sdb
##### 创建卷组
    vgcreate vg_home /dev/sdb
##### 创建逻辑卷
    lvcreate -n lv_home -l 100%FREE vg_home
##### 格式化逻辑卷为ext4格式
    mkfs.ext4 /dev/vg_home/lv_home

## 复制/home目录内容到新硬盘
##### 挂载逻辑卷到临时目录
    mount /dev/vg_home/lv_home /mnt/backup
##### 复制/home目录到逻辑卷
    cp -av /home/* /mnt/backup/
##### 取消挂载
    umount /dev/vg_home/lv_home
##### 修改/etc/fstab
    # 注释掉原挂载信息
    #/dev/sdc /home ext4 defaults 0 1
    /dev/vg_home/lv_home /home ext4 defaults 0 1
##### 重启系统，查看内容是否完整

## 将旧硬盘添加到卷组
##### 创建逻辑卷
    pvcreate /dev/sdc
##### 将旧硬盘添加到卷组
    vgextend vg_home /dev/sdc
##### 扩展逻辑卷
    lvextend -l +100%FREE /dev/vg_home/lv_home
##### 调整逻辑卷大小
    resize2fs /dev/vg_home/lv_home


    

    
     

