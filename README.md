# LEMP-example

## Intro
這是一個已經設定好可執行 PHP 程式碼的 docker 環境，你需要依照以下步驟啟用容器。

## Steps
- git clone 你的專案到本目錄下
- 你的專案中需要有一個可讓資料庫初始化的「.sql」檔案
- 完成以上內容後請修改「.env」文件
- 在該目錄下執行 `docker compose up -d`，如果你還在調試環境請執行 `docker compose up` 查看 log
- 如果沒有問題的話，你應該已經能夠從 `localhost:5080` 看到網頁了，如果你有在「.env」文件中修改為其他的 port，`localhost:` 請接上修改後的 port
- 你可以選擇直接在這個目錄繼續開發你的專案，或是進入到容器裡開發。因為已經掛載好了，兩邊的檔案會同步

## Error log
我們主要是在把專案掛載到 app 這個容器的 apache2 網頁伺服器下，所以我們查看 error log 的時候可以進入到 app 這個容器裡面，使用 `tail -f /var/log/apache2/error.log ` 查看 PHP 噴的錯誤。

另一個是讓 error 也顯示在網頁上，你需要使用函式 `phpinfo()` 找到文件「php.ini」並修改如下列變數的值：

```
error_reporting = E_ALL
display_errors = On
display_startup_errors = On
```
