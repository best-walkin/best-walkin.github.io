---
# multilingual page pair id, this must pair with translations of this page. (This name must be unique)
lng_pair: id_vasp_1
title: How to use VASP

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
comments_disable: true

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

{%- include util/auto-content-generator.liquid -%}

<!-- outline-start -->

{{ website_info_text_first }}

<!-- outline-end -->

{{ website_info_text_second }}