Git 小知識
==================

<h3 id="autoescape"> 建立使用者名稱與信箱 </h3>

```
git config   user.name "(使用者名稱)"   // 設定使用者名稱
git config   user.email "(使用者信箱)"  // 設定使用者信箱
```

<h3 id="autoescape"> 設定連線 </h3>

```
git remote -v                                  // 檢視你已經設定好的Online端
git remote add "(連線標籤名稱)" (Online端URL)   // 建立Online端連線
```

<h3 id="autoescape"> 資料新增 </h3>

```
git add (檔案名稱 ex : content.txt)   // 新增檔案到暫存檔
git add --all                        // 新增該資料夾的所有檔案
git commit -m "(要備註的訊息)"        // 將暫存檔的所有資料送出
```

<h3 id="autoescape"> 資料上傳 </h3>

```
git push                              // 提交所有暫存檔的資料到 Online
git push -u origin origin             // 提交所有暫存檔的資料到 Online ，並選擇要提交的 branch
```

<h3 id="autoescape"> 刪除檔案 </h3>

```
git rm (檔案名稱)                      // 刪除 "localtion 端" 的檔案
git rm --cached (檔案名稱)             // 刪除 Online端的檔案
```

<h3 id="autoescape"> 獲取 </h3>

```
git clone (Online端 URL)               // 將 Online端 的資料 Download 至 localtion 端
git fetch                             // 並不想抓檔案下來同步，只是想確認本地和線上的版本是否有差異
git pull                              // 將 Online端 的資料 Download 同步下來。   ( pull的內容就是 fetch + merge 所組成的 )
```

<h3 id="autoescape"> 檔案修改 </h3>

```
git checkout (檔案名稱)                // 檔案復原回上個 commit 的狀態
git reset (還原點hash)                 // 選擇還原點
git reset HEDE	[檔案名稱]             // 將檔案從目錄與暫存檔中拿掉
git reset mixed [檔案名稱]             // 將檔案從暫存檔中拿掉
git mv (content.txt ,test.txt)        // 更改檔案名稱。 (要更改的檔案名稱 , 要更改的名稱)
```

<h3 id="autoescape"> 狀態檢查 </h3>

```
git status                            // 檢查當前資料的狀態。( 可看到刪除 / 新增的資料有哪些 )
git log --oneline                     // 檢查過去所有的 Commit 紀錄
git --version                         // 檢查版本
```

<h3 id="autoescape"> 分支 (branch) </h3>

```
git branch                            // 檢查目前在哪個branch 上
git checkout (分支名稱)                // 切換到另外一個 branch
git branch (分支名稱)                  // 建立一個新 branch
git push -u origin (分支名稱)          // 當存在兩個以上 branch 時，檔案必須選定要上傳的 branch
git branch (分支名稱) -d               // 刪除 branch 。 (master 不可刪除)
git merge (別的分支名稱)               // branch 合併，將別的 branch 資料合併過來，注意可能會有 “衝突”。
```

<h3 id="autoescape"> 互動模式操作 </h3>

```
離開 Esc + :
編輯 : i
復原 : u 
存檔 + 離開 : Esc + : -> wq
```

<h1 id="autoescape"> 額外狀況 </h1>

<h3 id="autoescape"> git commit 指令下完，想要收回 </h3>

```
git reset HEAD content.txt  or  git reset HEAD^^
git checkout (檔案名稱)
* 取離暫存檔 (單個 / 全部) -> git checkout => 復原回上個 commit
```

<h3 id="autoescape"> git commit ( HEAD )收回時，又想要復原 </h3>

```
git reset (commit 版本號) --hard
* 復原上一次的 Commit。  ( 若忘記查看版本號 : git reflog )
```
  
<h3 id="autoescape"> 若想更改最後一筆 git commit 所傳送的訊息  </h3>

```
git commit --amend -m "(重新輸入要傳送的訊息)"
```
   
<h3 id="autoescape"> 若想清除帳號(github)  </h3>

```
git credential-wincred erase    //清除github帳號
	protocol=https
	host=github.com

```
