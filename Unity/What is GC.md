
GC
===========================

物件存在激活 / 非激活狀態，當物件處在 "激活" 狀態時，就會造成 GC 效能上的浪費，
變數也是同樣道理，當宣告了一個變數，並且持續使用著，那變數也會變成 "激活"狀態。

場景如果存在過多"激活"狀態的物件，就會造成遊戲卡頓。


###
降低 GC 效能消耗的方法
###

###
1.缓存
###

GameObject.Find ， GetComponent，transform ... 這類的 api 會造成效能的浪費，
能少用就盡可能少用。

```
void Update(){
    this.transform.Translate(0, 1, 0);
    this.GetComponent<Rigidbody>().AddForce(Vector3.forward);
}
```
像在 update 這種寫法，每偵呼叫 GetComponent 會造成過多的 GC 浪費。

建議 :
      void Awake(){
          myRigi = this.GetComponent<Rigidbody>();
          myTransform = this.transform;
      }
(在 Awake 、 Start 先把資料儲存在進行使用)      

###
2. 頻繁使用 Instantiate 和 Destroy
###

頻繁使用 Instantiate 和 Destroy 會讓腳本製造出很多垃圾，會大量佔取到 CPU 的時間，
可以使用 對象池(Object Pool) 的技術，來降低效能消耗


###
3. 空代碼
###

當有空的 Start 、 Update 也會造成 GC 的效能浪費，因此遊戲中能盡量減少 Update 的呼叫就盡量減少

###
4. CPU 峰值
###

同一時間內如果大量產生物件，會造成cpu峰值，因此在某個特定時間點上，有可能會使遊戲卡頓。

* 建議 :
      讓大量物件分開產生，不要一次性產生巨量的物件

###
5. GC(垃圾回收)
###

盡量少調用 GC 的代碼

* 比如 String 會執行到動態操作，可改為 System.Text.StringBuilder 處理。
   (動態操作就是字串會發生變化)

* Unity 上的 API 有 GetComponent，还有GameObject.name或GameObject.tag，Input.touches，Physics.SphereCastAll() 
   盡量少使用。
   
* 減少對粒子系统 Play() 的調用

* 如果可以，盡量不用 MeshCollider，如果不能避免的話，盡量减少 Mesh 的面數，或用較少面的物體替代

* 使用 Vector3.zero 而不是 new Vector(0,0,0)

* 訪問 Transform.position/rotation 都有相應的浪費，能 cache 就 cache 來返回結果
