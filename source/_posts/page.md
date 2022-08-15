---
layout: hexo
title: Hexo新增分類或標籤等其他自訂頁面
date: 2022-08-15 14:11:55
categories: 
- Hexo
tags: 
- Hexo
---
### 新增分類、標籤頁面
<!--more-->
先在主題裡配置好分類、標籤
開啟`/Project/theme/next/_config.yml`檔案
找到menu

```
menu:
  home: / || fa fa-home
  #about: /about/ || fa fa-user
  tags: /tags/ || fa fa-tags  //刪除前面#
  categories: /categories/ || fa fa-th //刪除前面#
  archives: /archives/ || fa fa-archive
  #schedule: /schedule/ || fa fa-calendar
  #sitemap: /sitemap.xml || fa fa-sitemap
  #commonweal: /404/ || fa fa-heartbeat
```
再來建立分類、標籤的目錄檔案
Project --> cmd
```
hexo new page categories
hexo new page tags
```
以分類做說明
至`/Project/source/categories/`找到`index.md`檔案
```
---
title: categories
date: 2022-08-15 14:20:06
type: "categories"  <<--新增這段
---
```
tags也是如此操作方式

### 新增文章如何使用分類與標籤
在文章上方區域新增categories與tags
```
----------------
title: GitHub + Hexo
author: 3618321s
date: 2022-08-10 16:56:38
tags: 
- GitHub <<--
- Hexo  <<--
----------------
```
備註：分類一次只能設定一個，設定兩個則第二個為第一個的子項目
