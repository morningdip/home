---
layout: post
title:  設定 Kobo 時跳過登入步驟
date:   2024-01-16
categories: tips
---

入手 Kobo 後，在初始化電子書閱讀器的時候，發現官方會強制要求你登入 Kobo 帳號，
當然這會帶來很多方便的功能，比如自動同步書籍等等，不過代價就是你需要賣一點隱私給 Kobo，
想要全部手動自己來，卻沒有跳過登入的選項，
好在國外有大神用 SQL 語法修改，除了跳過登入的步驟外，還可以關閉 Kobo Analytics Event。


```sql
insert or replace into user
  (UserID, UserKey)
values
  ('-', '-');

drop index if exists analytics_events_timestamp;

create trigger if not exists delete_analytics
after insert on AnalyticsEvents begin
  delete from AnalyticsEvents;
end;
```
<br/>

詳細的步驟如下：
1. 把 Kobo 連接到電腦
2. 下載 [SqliteBrowser](https://sqlitebrowser.org/dl/)
3. 點選 **File/Open Database** ，選擇 Kobo 目錄下的 **.kobo/KoboReader.sqlite**
4. 在 **Execute SQL** 分頁中輸入上述的程式碼
5. 點選 **File/Close Database**，並儲存變更
6. 完成囉
<br/>

[Ref: Setting up a Kobo without logging in](https://jacobalbano.com/2021/06/24/setting-up-a-kobo-without-logging-in/)
