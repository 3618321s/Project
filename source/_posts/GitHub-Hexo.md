---
title: GitHub + Hexo
author: 3618321s
date: 2022-08-10 10:56:36
categories: 
- GitHub
tags: 
- GitHub
- Hexo 
---
## 環境準備
<!--more-->
### 安裝工具
* [Node.js](https://nodejs.org/zh-tw/download/)：提供npm來安裝所需的套件(下載安裝檔)
* [Git](https://git-scm.com/downloads)：將檔案發布到 GitHub Page(下載安裝檔)

### [Hexo](https://hexo.io/zh-tw/docs/)

開啟cmd命令提示字元，輸入以下安裝指令

```
npm install hexo-cli -g
```

安裝後，可輸入以下指令查看Hexo版本，確認是否安裝成功

```
hexo -v
```

在要新增資料夾的路徑上輸入CMD，輸入以下指令

```
hexo init 資料夾名稱
hexo init Project //假設資料夾名稱為Project
```

進入Project資料夾

```
cd Project 
```

輸入以下指令，安裝所需的npm套件

```
npm install //安裝完成後可在Project看見資料
```

## 常用指令

### 新增文章
```
hexo new "文章標題" //若含空白須加上雙引號"
```
### 建立頁面
```
hexo new page "頁面名稱" //可在source資料夾找到該頁面名稱之資料夾 編輯index.md
```
### 將檔案發布至GitHub
檔案發布之前需在Github建立Repository **以下簡稱repo
在Project資料夾，輸入以下指令(cmd)
```
npm install hexo-deployer-git --save  //安裝部屬所需套件
```

修改Project/_config.yml檔案的Deployment設定
```
deploy:
  type: git
  repo: https://github.com/username/repo.git
  branch: master / gh-pages
```
修改後，輸入以下指令
```
hexo deploy //部屬指令
```

## 總結
基本上每次修改後輸入指令為
```
hexo cl //hexo clean 清除靜態檔案與快取
hexo g  //hexo generate 產生靜態檔案
hexo d  //hexo deploy 部屬至GitHub
```
第二步驟和第三步驟可直接合併使用
```
hexo g -d
```
發布之前可以輸入以下指令，在自己電腦上預覽結果

```
hexo s  //hexo server 啟動伺服器 本地瀏覽使用
```
