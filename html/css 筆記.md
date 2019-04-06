Css 小技巧
=================================


bootstrap 官方前端教學 : https://bootstrap.hexschool.com/docs/4.0/components/forms/

Html  常用標籤 http://web.thu.edu.tw/hzed/www/tag.htm *****
section 標題 + 內容

* 選項選擇 - 

<input type="checkbox" value="option1" disabled> => (disabled) 讓按鈕失去功能

-- 單選 --

<input type="radio" name="Options" value="option1">
<input type="radio" name="Options" value="option2">

-- 可多選 ---

<input type="radio" value="option1">
<input type="radio" value="option2">

-----------------------------------------------------------------------------------------

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



-----------------------------------------------------------------------------------------
****** CSS  選擇器用法  http://www.w3school.com.cn/cssref/css_selectors.asp

-webkit-box-sizing: border-box;
     -moz-box-sizing: border-box;
          box-sizing: border-box;		//參考網址 : http://zh-tw.learnlayout.com/box-sizing.html
// 使用 padding or border or other css 會造成內距和邊框增加，使用它，內距和邊框將不會增加元素本身的寬度


column-count 以欄方式，顯示文字
column-gap 設定欄與欄的間距


position:static  不會被特別定位，瀏覽器預設
position:relative  表現的和 static 一樣，除非你增加了一些額外的屬性。
position:absolute  固定定位


overflow : 	判斷文字 、 圖片是否要顯示(超過範圍之類的)
white-space: nowrap	規定文字不斷行

text-align: justify; + text-justify: inter-word;	文字垂直對齊
text-transform : capitalize	字母開頭大寫 
text-decoration : none		文字修飾 - 取消底線等等
justify-content 搭配 display:flew (水平對齊) (塞在父物件，子物件移動)
align-items (垂直對齊) (同上)  
align-self  (在使用過 align-items 的情況下，align-items位置已經固定，由此函式去改寫物件位置)

*注意 : align-items 執行為物件目前的中心位置  align-content 為群體的中心位置

flex-wrap	當物件以display:flow 就是以單行得方式排列，如果要強迫換行使用 flex-wrap 來換行

vertical-align 圖片在文字指定地方(文字上方 或者 文字下方) 顯示

flex-direction 物件排序 row：預設值，由左到右，從上到下  row-reverse：與 row 相反
			column：從上到下，再由左到右	column-reverse：與 column 相反
( flex-wrap:wrap 自動換行 ， flex-direction 不會幫忙自動換忙)

flex-grow: 0 (代表分成幾份);	( 預設為 0 ) 放置子物件身上，給予父物件剩餘空間
				(父物件 width 500，子物件 100 100 100 則剩餘 200 空間)

background-attachment	(固定背景) 背景不會隨著滑鼠滾輪移動


z-index 圖片深度

cursor 改變游標

opacity 透明度

content 顯示 url

word-spacing	字與字之間的距離
letter-spacing  字與字之間增加空白


width: calc(可以進行不同單位的數學運算 : % - px)

1.ul -> li 清單
list-style: none;	** 刪除開頭˙


filter: 濾鏡效果 
blur(高斯模糊) 單位 : px
grayscale(黑白) 單位 : % 


css animation 全解析 : https://developer.mozilla.org/zh-TW/docs/Web/CSS/CSS_Animations/Using_CSS_animations

*********************************************************************

:active		//滑鼠點擊
:hover		//滑鼠移過
:LINK		//尚未連接
:VISITED	//已連接

:first-child	//父元素的第一個子物件
:last-child	//父元素的最後一個子物件


<h2 id="text">
(#text) :: after or ::before		// after 在目前後方出現 。 before 在目標前方出現 。
{
	content:  attr(id);		// content 顯示要添加的內容 。
					// attr (若不想使內容固定，則使用 attr(id) 便可顯示 "text" )。
}



**********************************************************************


網頁可見區域寬：document.body.clientWidth
網頁可見區域高：document.body.clientHeight

網頁可見區域寬：document.body.offsetWidth(包括邊線和捲軸的寬)
網頁可見區域高：document.body.offsetHeight(包括邊線的寬)


@media screen and  (orientation: portrait)	視窗為直立的話



@supports <條件規則>
@supports <條件規則> and <條件規則>
@supports not <條件規則>	//當瀏覽器不支持此 css 時
