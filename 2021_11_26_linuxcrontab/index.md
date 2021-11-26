# Linux Crontab - 排程設定


###前言
在Linux作業系統，一般要執行例行、重覆性的工作，會透過crontab的設定來執行。


### 1.crontab 常用指令
***
#### 個人crontab

##### 查看個人crontab內容
```cmd
crontab -l
```

##### 編輯個人crontab內容
```cmd
crontab -e
```
***
#### 系統設定 crontab
將crontab設定寫在 **/etc/crontab** 及 **/etc/cron.d/ 目錄下的各個設定檔**

***
### 2.crontab 設定格式
MIN       | HOUR  | DOM  |MON   |DOW   |CMD   |
----------|-----|-----|-----|-----|-----|
分鐘      |小時  | 日  |月份   |星期幾   |執行指令   |
0-59      |0-23  | 1-31  |1-12 (可寫月份英文簡寫)  |0-7 (0與7皆代表週日，可用英文簡寫)   |執行指令   |


**系統排程設定crontab格式**
MIN       | HOUR  | DOM  |MON   |DOW   |USER   |CMD   |
----------|-----|-----|-----|-----|-----|-----|
分鐘      |小時  | 日  |月份   |星期幾   | 使用者帳號 |執行指令   |

                                                 => 表示以此使用者的權限執行指令

{{< admonition example >}}
```cmd
# ┌───────────── 分鐘   (0 - 59)
# │ ┌─────────── 小時   (0 - 23)
# │ │ ┌───────── 日     (1 - 31)
# │ │ │ ┌─────── 月份   (1 - 12)
# │ │ │ │ ┌───── 星期幾 (0 - 7，0和7是週日，6 是週六)
# │ │ │ │ │
  * * * * * Your command
```
{{< /admonition >}}
***
### 3.crontab 特殊字元使用
特殊字元       | 說明  |
----------|-----|
 < * > 星號| 代表**任個時刻**，若在日期欄位輸入，代表每日執行 
< - > 減號| 代表**一個區間**，例如在小時欄位輸入8-11，代表上午 8,9,10,11 時|
< , > 逗號| 代表**不同的時間點**，例如在月份欄位輸入1,4,7,10，代表每年1,4,7,10月執行|
< /X> /數字| 代表**每隔X時間**執行，例如在月份欄位輸入* / 3 即代表每季執行一次

***
### 4.常用執行時間簡寫
簡寫 | 說明  |
----------|-----|
@reboot	 | 每次重新開機之後，執行一次|
@yearly	或 @annually | 每年執行一次，亦即 0 0 1 1 *|
@monthly | 每月執行一次，亦即 0 0 1 * *|
@weekly	 | 每週執行一次，亦即 0 0 * * 0|
@daily 或 @midnight	 | 每天執行一次，亦即 0 0 * * *|
@hourly	 | 每小時執行一次，亦即 0 * * * *|

範例 (每小時執行一次)
```cmd
@hourly Your command
```
***
### 5.常用範例及說明
#### 每日上午2點執行MySQL資料庫備份並壓縮
```cmd
0 2 * * * mysqldump --login-path=DBname DBname | gzip > /mysqlbackup/$
```

#### 每日上午2點執行刪除建立超過七天之檔案
```cmd
0 2 * * * rm /mysqlbackup/fileName_`date -d "-7 days" +\%Y\%m\%d`.sql.gz
```

#### 每五分鐘執行一次XXX執行檔
```cmd
5 * * * * sh /FilePath/XXX.sh
或
*/5 * * * * sh /FilePath/XXX.sh
```

#### 每月 10 日、20 日、30 日晚上 10 點 30 分各執行指令一次
```cmd
30 22 10,20,30 * * command
```
#### 從早上 8 點到下午 5 點，遇到整點就執行指令
```cmd
00 08-17 * * * command
```
#### 重啟系統須為最高權限
```cmd
sudo -i

crontab -e

Cronjob內容:
# 每年1/20, 4/20, 7/20及10/20 上午03:00進行伺服器重啟作業 
00 03 20 1,4,7,10 * /sbin/shutdown -r now
```

***
### 6.錯誤範例及說明
週與日、月不可並存
```cmd
0 2 31 12 1 mysqldump --login-path=DBname DBname | gzip > /mysqlbackup/$   
```
=> 系統會判定12月31日或每週一皆執行指令


### 參考資料:
1. [GTW](https://blog.gtwang.org/linux/linux-crontab-cron-job-tutorial-and-examples/)

2. [鳥哥的Linux私房菜-第十五章、例行性工作排程(crontab)](http://linux.vbird.org/linux_basic/0430cron.php#whatiscron_type)
