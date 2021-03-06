# DiscordSearcher
可以自訂下載想要的Discord頻道

頻道內所有文字內容會以SQLite儲存在db檔案內

## 截圖

DiscordSearcher.exe介面：
![DiscordSearcher介面](https://github.com/mtis1233/DiscordSearcher/blob/main/%E5%9C%96%E7%89%87/pic1.png?raw=true)

DB Browser for SQLite開啟DiscordData.db：
![DiscordData](https://github.com/mtis1233/DiscordSearcher/blob/main/%E5%9C%96%E7%89%87/pic2.png?raw=true)

## 使用教學
1. 開啟DiscordSeacher.exe
2. 點選登入設定按鈕填入資訊儲存
2_1. 點選資料庫設定  設定自己的資料庫規則(可省略)
3. 將要下載的頻道網址填入
4. 可選擇是否開啟快速模式(只下載最新50筆資料)
5. 點選開始搜尋按鈕


## 產生檔案

使用後會產生DiscordURL.txt、DiscordData.db、DiscordRule.ini

1. DiscordURL.txt ： 

      用於儲存要搜索的網址
      
      每行一個網址 格式為 https://discord.com/channels/.../...
      
2. DiscordData.db： 

      用於儲存搜索的資料

      可用DB Browser for SQLite開啟
      
      兩個資料庫： 內容只有文字、內容有網址
      
      資料庫表格格式：
      
        id: 創建第幾筆
      
        timestamp: 時間
      
        content: 聊天內容
      
        title: 內容裡的網站名稱
      
        url: 內容裡的網址
      
        attachmentsname: 上傳的文件名稱
      
        attachmentsurl: 上傳的文件下載網址
        
        referer: 這筆資料的來源
        
3. DiscordRule.ini：

      儲存登入資訊的資料、資料庫分類的規則
      
      資料庫分類的規則 儲存方式：點選"新增分類方式"按鈕(無須輸入判斷關鍵字)
      
      直接改內容是不會自動儲存的 要點選"新增分類方式"按鈕才會儲存
      
      另外下方的"點擊開始測試"按鈕是讀取未儲存的資訊
      

## 登入資訊填入教學

注意：authorization、cookie等同帳密資訊 勿外流

1. 使用Chrome登入Discord
2. 點F12
3. 點選Network標籤
4. 點選XHR標籤
5. 從Name列表點選其中一個
6. Headers標籤下尋找Request Headers
7. 在Request Headers下方尋找你所需要的資訊複製過去

## 資料庫分類方式

0. 格式：
      
      關鍵字，等於or不等於，資料表
      
      越上面優先權越高 資料成立時以下的規則將會略過
      
1. 關鍵字：
      
      可直接輸入文字數字 不分大小寫
      
      有這個關鍵字會執行動作
      
      進階指令: r'正規表達式'
      
2. 等於or不等於：

      = 等於 當等於關鍵字時 將這筆資料丟入資料表
      
      ≠ 不等於 當不等於關鍵字時 將這筆資料丟入資料表
      
3. 資料表：

      SQLite Table
      
4. 測試區：

      可以測試你上面設定的規則會怎麼被分配
      
      將要測試的資料填入左邊
      
      點選開始測試
      
      結果會出現在右邊
      
      
