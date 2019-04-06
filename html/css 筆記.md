Css 小技巧
=================================

<h3 id="autoescape"> 參考網址 </h3>

```
https://bootstrap.hexschool.com/docs/4.0/components/forms/	bootstrap 官方前端教學
http://www.w3school.com.cn/cssref/css_selectors.asp		CSS  選擇器用法
https://developer.mozilla.org/zh-TW/docs/Web/CSS/CSS_Animations/Using_CSS_animations		css animation 全解析
https://webgradients.com/					Html 漸層顏色 參考標準
```




-----------------------------------------------------------------------------------------


```
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



@media screen and  (orientation: portrait)	視窗為直立的話
@supports <條件規則>
@supports <條件規則> and <條件規則>
@supports not <條件規則>	//當瀏覽器不支持此 css 時

```
