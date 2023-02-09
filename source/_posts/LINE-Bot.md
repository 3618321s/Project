---
title: LINE@ Bot
date: 2022-09-22 11:34:53
tags:
- LINE
- google apps script
- google sheet
categories:
  - LINE@
---
Line官方帳號搭配google apps script + google sheet

官方帳號設定知識點，
設定好友點擊每次顯示不同知識點。

<!--more-->

### 事前準備

#### 建立LINE官方帳號
不敘述。
須設定開啟之功能
* 開啟Messaging Api功能
* 開啟聊天機器人
* 開啟Webhook

#### google sheet建立
使用google試算表，建立知識點清單。
第一欄為索引，第二欄為知識點。
![img](https://github.com/3618321s/blog/raw/gh-pages/images/Project/googlesheet.png)
接著共用此工作表，有此連結者皆可以編輯此資料表。
https://docs.google.com/spreadsheets/d/{SheetID}/edit?usp=sharing
{SheetID}為此工作表ID

### 進入主題

#### 使用google app script
程式碼如下
```
function doPost(e) {
  var CHANNEL_ACCESS_TOKEN = 'LINE TOKEN'; //取得LINE CHANNEL_ACCESS_TOKEN
  var msg= JSON.parse(e.postData.contents);
  //console.log(msg);
  
  // 取出 replayToken 和發送的訊息文字
  var replyToken = msg.events[0].replyToken;
  var userMessage = msg.events[0].message.text;

  if (typeof replyToken === 'undefined') {
    return;
  }

  if(userMessage == '小知識'){ //判斷使用者輸入文字若為小知識
    pushMsg(CHANNEL_ACCESS_TOKEN,replyToken,userMessage);
  }
}

function pushMsg(channel_token,reply_token,usermessage){
//取得亂數
  min = 1;
  max = 50;
  num = Math.floor(Math.random() * (max - min + 1)) + min; //取得亂數
  //console.log(num);

//取得工作表資料
  var id = '工作表ID';  //SheetID
  var name = 'db'; //工作表名稱
  var spreadsheet = SpreadsheetApp.openById(id);  
  var sheetName = spreadsheet.getSheetByName(name);  
  var data = sheetName.getDataRange().getValues(); // 取得的資料

  var dataExport = {};  
  var index;
  index = data[num][0]; //找到亂數索引的資料
  dataExport[index] = {
    text: data[num][1]  //帶出該索引的資料  
  }
  
  var dataExportFormat = JSON.stringify(dataExport);
  
  //console.log(dataExportFormat);

//推送回覆訊息
  var url = 'https://api.line.me/v2/bot/message/reply';  
  UrlFetchApp.fetch(url, {
      'headers': {
      'Content-Type': 'application/json; charset=UTF-8',
      'Authorization': 'Bearer ' + channel_token,
    },
    'method': 'post',
    'payload': JSON.stringify({
      'replyToken': reply_token,
      'messages': [{
        'type': 'text',
        'text': data[num][1]
      }],
    }),
  });
}
```
點擊`發布`-->`部屬為網頁應用程式`-->版本控制 每次都用新增
最後複製連結 貼到LINE Messaging api 儲存