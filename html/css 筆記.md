Css 小技巧
=================================

<h3 id="autoescape"> 參考網址 </h3>

```
https://bootstrap.hexschool.com/docs/4.0/components/forms/	bootstrap 官方前端教學
http://www.w3school.com.cn/cssref/css_selectors.asp		CSS  選擇器用法
https://developer.mozilla.org/zh-TW/docs/Web/CSS/CSS_Animations/Using_CSS_animations		css animation 全解析
https://webgradients.com/					Html 漸層顏色 參考標準
```

```

css (常用) 選擇器 

div > div		//抓下一個 div
:active		//滑鼠點擊
:hover		//滑鼠移過
:LINK		//尚未連接
:VISITED	//已連接

:first-child	//父元素的第一個子物件
:last-child	//父元素的最後一個子物件

:before 	//在之前插入內容
:after		//在之後插入內容

```

<h2 id="autoescape"> API </h2>
<h3 id="autoescape"> 樣式背景 </h3>

```
background-color:#6495ed;
background-image:url('xxxx.png');		//背景圖片
background-repeat:repeat-x;			//背景樣式圖片往水平的方向鋪成(url : http://www.runoob.com/css/css-background.html)
background-repeat:no-repeat;			//背景不重複

	-- 設置背景位置
		background-attachment:fixed;
		background-position:center;	//使用 position 設定背景的位置 (可配合 background-repeat:no-repeat 做搭配)



background-attachment	(固定背景) 背景不會隨著滑鼠滾輪移動
```

<h3 id="autoescape"> 文字教學 </h3>

```
font-family:"Times New Roman"			//設定字體樣式
normal	//正常文字		italic	//斜體

text-transform : capitalize	字母開頭大寫 
text-decoration : none		文字修飾 - 取消底線等等


column-count 	以欄方式，顯示文字
column-gap 	設定欄與欄的間距


text-align: justify; + text-justify: inter-word;	文字垂直對齊


overflow : 	判斷文字 、 圖片是否要顯示(超過範圍之類的)
white-space: nowrap	規定文字不斷行



Content			//內容 (只能在偽元數下插入內容) ex: .class:after
```

<h3 id="autoescape"> 清單樣式 </h3>

```
list-style: none;				//刪除開頭˙
list-style-image:url('xxx.jpg');		//清單開頭設為圖片
```

<h3 id="autoescape"> 版面設定 </h3>

```
參考網址 : (超詳細) http://zh-tw.learnlayout.com/no-layout.html

* 使用 padding or border or other css 會造成內距和邊框增加，使用它，內距和邊框將不會增加元素本身的寬度
( box-sizing )可以完美解決問題

	-webkit-box-sizing: border-box;
     		-moz-box-sizing: border-box;
          		box-sizing: border-box;




float:left;		//往左側靠
cleat:left;		//取消靠左移動，直接移動到 (div float) 的下方

Margin			//外邊界
Border			//邊框
Padding			//內邊框


( border:5px solid red; )			//邊框用法
border-style:solid				//邊框樣式
border-width:5px				//邊框大小
border-top-style				//單邊樣式



max-height	元素的最大高度。
max-width	元素的最大宽度。
min-height	元素的最小高度。
min-width	元素的最小宽度。



(display:none) vs (visibility:hidden)
完全隱藏不佔位置    隱藏但佔位置

	display : 
		block 強迫分段
		inline 水平
		
		inline-block 差別只是多個可以自由設定寬高而已


position:static  	不會被特別定位 ( 瀏覽器預設 )
position:relative  	表現的和 static 一樣，除非你增加了一些額外的屬性。
position:absolute  	固定定位
position:fixed		固定定位

	(fixed) vs (absolute) : 需要指定 bottom / top / left / right : 0
		fixed : 永遠固定位置。 (頁面滑動時，還是會在原位)
		absolute : 固定位置。 (頁面滑動時，會跟著頁面移動)



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


z-index 圖片深度

cursor 改變游標

opacity 透明度

content 顯示 url

word-spacing	字與字之間的距離
letter-spacing  字與字之間增加空白


width: calc(可以進行不同單位的數學運算 : % - px)


filter: 濾鏡效果 
blur(高斯模糊) 單位 : px
grayscale(黑白) 單位 : % 



<h2 id="text">
(#text) :: after or ::before		// after 在目前後方出現 。 before 在目標前方出現 。
{
	content:  attr(id);		// content 顯示要添加的內容 。
					// attr (若不想使內容固定，則使用 attr(id) 便可顯示 "text" )。
}


@media screen and  (orientation: portrait)	視窗為直立的話
@supports <條件規則>
@supports <條件規則> and <條件規則>
@supports not <條件規則>	//當瀏覽器不支持此 css 時

```
