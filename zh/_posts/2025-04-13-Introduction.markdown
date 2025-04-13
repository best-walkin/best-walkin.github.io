---
# multilingual page pair id, this must pair with translations of this page. (This name must be unique)
lng_pair: id_vasp_1
title: Linux系统安装VASP6.3.2(vtst&vaspsol++)

# post specific
# if not specified, .name will be used from _data/owner/[language].yml
#author: ""
# multiple category is not supported
category: VASP
# multiple tag entries are possible
tags: [vasp, python]
# thumbnail image for post
img: ":post_pic3.jpg"
# disable comments on this page
comments_disable: false

# publish date
date: 2025-04-13 13:45:08 +0900

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

# VASP.6.3.2编译
| Name        | Version     |
| :---:        |    :---:   |
| Linux System| Ubuntu 22.04|
| gcc         | 11.4        |
| Intel oneAPI Base Toolkit| 2023.1.0.46401|
| Intel oneAPI HPC Toolkit| 2023.1.0.46346|
### Intel OneAPI安装
##### 1. 下载Intel oneAPI到/opt目录
    root@localhost:/opt# chmod +x l_BaseKit_p_2023.1.0.46401_offline.sh
    root@localhost:/opt# chmod +x l_HPCKit_p_2023.1.0.46346_offline.sh
    root@localhost:/opt# apt-get install make gcc g++ libxml2-dev zlib1g-dev libboost-all-dev libssl-dev apt-get install xdg-utils libgbm1 libgtk-3-0 libnotify4 libnotify4 libxcb-dri3-0 libatspi2.0-0 -y
##### 2. 安装Intel oneAPI Base Toolkit
    root@localhost:/opt# ./l_BaseKit_p_2023.1.0.46401_offline.sh
    
     

