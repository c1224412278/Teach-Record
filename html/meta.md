meta 小技巧
==============================

<h3 id="autoescape"> 參考網址 </h3>

```
httpwww.pcnet.idv.twpcnethtml17.htm	              //功能使用
http://www.cnblogs.com/sniper007/p/3258389.html		//解說
```


```
* meta Attributes

name = descript 以及 name=keywords，每個 meta 使用 name 的時候，都會搭配 content 來呈現資訊內容，
簡單來說，name 代表資訊項目，content 代表資訊值

<META HTTP-EQUIV="refresh" CONTENT="15; url=http://www.pcnet.idv.tw/">
		說明：
			refresh==>更新或重整
			15==>15秒後執行下一動作
			; => CONTENT內要作的每件事" "，分別以分號區隔
			url=http://www.pcnet.idv.tw/ =>指定轉換到此網頁

<meta name="Creation-Date" content="01-jan-2003 20:40:01">	網頁何時完成
		說明：
			Creation-Date==>創作日期
			01-jan-2003 20:40:01==>詳細日期時間

<link rev="made" href="mailto:pcnettw@yahoo.com.tw">
		說明：網頁作者信箱或網址陳述
			rev==>正向關聯
			made=>網頁製造者
			href==>您的信箱或網址

<meta name="description" content="網頁簡短描述">	用來寫網頁的簡短描述。
<meta name="keywords" content="網頁關鍵字">	用來放置網頁關鍵字。
<meta name="author" content="作者姓名">		記錄網頁的作者名稱
<meta name="generator" content="編輯器名稱">	用來記錄網頁編輯器名稱
<meta name="copyright" content="網頁版權">	用來標示網頁的版權或著作權聲明
<meta name="distribution" content="網頁發佈地區">	用來記錄網頁的發佈地區


<meta http-equiv="Content-Type" content="text/html"; charset="uft-8">	網頁內容的種類以及編碼
<meta http-equiv="Content-Language" content="zh-TW">			網頁所使用的語言種類
<meta http-equiv="Refresh" content="time">				自動更新網頁的時間
<meta http-equiv="Pragma" content="no-cache">				禁止瀏覽器用快取開啟網頁
<meta http-equiv="windows-Target" content="_top">			強制在單一視窗中顯示網頁

```
