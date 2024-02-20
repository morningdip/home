---
layout: post
title:  解決 Safari iCloud 標籤頁同步問題
date:   2024-01-16
categories: tips
---

前陣子發現 iPhone 的 Safari 顯示 Mac Safari 很久以前的標籤頁，
想關也關不掉，即便我點選關閉，過一陣子又回朔回去，超惱人，解決方法如下：

1. 把所有平台 iCloud 設定裡的 Safari 同步關閉，
2. iPhone、iPad 會問你如何處理裝置上的 Safari 資料，選擇 **從我的 iPhone / iPad 刪除**
3. Mac 的部分要手動刪除，到 **~/Library/Containers/com.apple.Safari/Data/Library/Safari** 目錄
4. 刪除以下三個檔案
   - CloudTabs.db-wal
   - CloudTabs.db
   - CloudTabs.db-shm
5. 重新打開所有裝置 Safari 的 iCloud 同步功能
6. 搞定收工
    
