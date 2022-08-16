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
開啟 `/Project/theme/next/_config.yml` 檔案
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
至 `/Project/source/categories/` 找到 `index.md` 檔案
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

### 自訂頁面
在建立網站時，會參考許多資料，一併彙整一起
就以連結頁面為例，新增頁面為links
```
hexo new page links
```
至 `/Project/source/links/` 找到 `index.md` 檔案
直接將連結資料貼到此檔案即可
另外，記得到 `/Project/theme/next/_config.yml` 檔案
找到menu，加上連結的icon
```
menu:
  <<-省略->>
  連結: /links/ || fa fa-link  <<--加入此行
  <<-省略->>
```

### 套件
#### NexT的搜尋套件
Project --> cmd
```
npm install hexo-generator-searchdb --save
```
`/Project/theme/next/_config.yml` 檔案找到 `local_search`
只需要將 `enable` 改成 `true` 就可以搜尋站內網站的功能
```
# Local Search
# Dependencies: https://github.com/theme-next/hexo-generator-searchdb
local_search:
  enable: true   <<--修改成true
  # If auto, trigger search by changing input.
  # If manual, trigger search by pressing enter key or search button.
  trigger: auto
  # Show top n results per article, show all results by setting to -1
  top_n_per_article: 1
  # Unescape html strings to the readable one.
  unescape: false
  # Preload the search data when the page loads.
  preload: false
```

#### NexT的書籤套件 - Bookmark
它會紀錄你在哪一個頁跳出，只需要一個點擊，你就可以跳回到你上一次離開的畫面
Project/theme/next --> cmd
```
git clone https://github.com/theme-next/theme-next-bookmark.git source/lib/bookmark
```
需發布至GitHub才可以使用此功能，在本地預覽沒有效果。