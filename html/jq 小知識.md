Jquery 小技巧
=================================

<h3 id="autoescape"> 參考網址 </h3>

```
http://www.cnblogs.com/zhongweiv/archive/2011/11/04/EventBubbling.html		阻止事件冒泡
```

```
.ready	進場直接執行，觸發時間較早 * 注意 $(document).ready() 必須在 window.onload 之前使用
window.onload	整個頁面下載完，才開始，如果網頁有100張圖片會下載完100張才執行

.hide()	/ .hide(int 隱藏時間動態效果) 隱藏
.show()	顯示
.toggle() 切換顯示 / 隱藏	可以用來切換功能 (多種以上)

.fadeIn() / .fadeIn("slow") / .fadeIn(3000)	播放物件顯示的時間快慢
.fadeOut() 	//同上


append() - 在被選元素的結尾插入內容
prepend() - 在被選元素的開頭插入內容
after() - 在被選元素之插入內容
before() - 在被選元素之前插入內容


<input type="text" name="name" id="first_name">		// 需要使用者輸入的字串的時候，可以預設字串
$("#first_name").attr('placeholder' , 'Johnny');	// (placeholder 為佔位符號 , "Johnny" 為預設字串的內容) 


location.reload		//F5
.load()			//載入圖片或文本
.dblclick()		//當物件點擊兩下
$(window).resize	//當窗口解析度調動時
window.setInterval(fun , 200)	//判斷每幾毫秒執行一次方法
setTimeout(fun , 200)	//方法延遲幾秒執行


parent() 			//取得父物件 - 只往上查找一層
closest() 			//找尋父物件 - 只要找到符合條件的 就停止
parents() 			//取得父物件 - 不停止 找出所有符合條件的


.children()			//取得子物件 - 不停止 找出所有子物件
.find()				//取得子物件 - 找到第一個符合的子物件 就停止


.click vs .unbind()//解綁事件(click解除)
.unbind()	//可以選擇按鈕要不要解除偵測


this.querySelector("a");	//抓取子物件 <a> 
		
.mouseover()			//當鼠標在上方時
.mouseout()			//鼠標離開上方時

.slideToggle()			//滑動隱藏
.preventDefault()		//拒絕超連接 (當Form要提取時，填寫不完全可以拒絕提送表單)

.each				輸出每個 li 
.next				下一筆資料

.focus				當Input地方獲得焦點時呼叫
.blur				當Input地方失去焦點時呼叫


:first 				尋到第一個元素
:last				尋找最後一個元素
:not 				比對未選取的元素
:gt(number)			列出大於 number 的元素
:lt(number)			列出小於 number 的元素
:even 				比對索引值為偶數的元素
:odd 				比對索引值為基數的元素
:eq	$("tr:eq(0)") 		比對指定索引值的元素 -------------- * 重要
:animated 			比對所有執行動畫效果的元素
:has(img) 			比對div裡面是否有 img 


$("div") 			選取所有 Div
$("#body")  			選取ID為body元素
$("div#body") 			選取 id 為 body 的 <div>
$("div.contents p") 		選取clss為contents 的下層子物件 <p>
$("div > p") 			選取 <div> 包住的下一層 <p>



網頁可見區域寬：document.body.clientWidth
網頁可見區域高：document.body.clientHeight

網頁可見區域寬：document.body.offsetWidth(包括邊線和捲軸的寬)
網頁可見區域高：document.body.offsetHeight(包括邊線的寬)

```

<h3 id="autoescape"> 事件呼叫 </h3>

```
bind		//(綁定事件 , 方法)
unbind()	//取消綁定方法
one(events, handler)	//可以取代 unbind 的動作，但只執行一次就會自動.unbind()


---------------------------------------------------------------------------------------

bind 與 on 的差別 :
bind 是直接將事件處理函式直接綁定在選取的元素上面，所以在綁定當時，元素必須是已經存在 DOM 中的
on 可接受動態新增元素 ( 'li' 之類的元素可能會新增or刪除) 

$('#dataTable tbody').on('click', 'tr', function() {
	// 這裡的 this 指向符合 selector 的 DOM 元素，也就是 tr
	console.log( $(this).text() );
});

off() 可刪除事件
$('p').off();
$('p').off('click');
$('p').off('click', '#foo');

```
