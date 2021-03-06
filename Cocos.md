Cocos 小知識
========================

Text Content <html>

參考資料 : https://docs.cocos.com/creator/manual/zh/components/richtext.html



sprite type:
```
  Simple (普通圖片)
  Sliced (九宮格切圖模式圖片)
  Tiled (平舖圖片) : 當改變 sprite size-w 時，會以 "重複" 方式來自動選染原始圖片
            Fill Type : 
                HORIZONTAL 水平填充
                VERTICAL 垂直填充
                RADIAL 扇形填充
            
  Filled (填充圖片) : 類似 Unity 的 Image Amount
```

Mask :
```
    * 注意该组件不能添加到有其他渲染组件（如 Sprite、Label 等）的节点上。
    * 子物件放在 "父物件(mask)" node底下，並修改 mask width/height
```
  
Widget :
```
    Top     對齊上邊界
    Bottom  對齊下邊界
    Left    對齊左邊界
    Right   對齊右邊界
    HorizontalCenter	水平方向居中
    VerticalCenter    垂直方向居中
    Target  對齊目標
    AlignOnce (false)會一直保持與父物件對齊 / (true)只會與父物件對齊一次
```

項目文件結構
```
ProjectName（项目文件夹）
├──assets
├──library
├──local
├──settings
├──temp
└──project.json

* 資源文件夾 (assets) :

assets 将会用来放置您游戏中所有本地资源、脚本和第三方库文件。只有在 assets 目录下的内容才能显示在 资源管理器 中。assets 中的每个文件在导入项目后都会生成一个相同名字的 .meta 文件，用于存储该文件作为资源导入后的信息和与其他资源的关联。一些第三方工具生成的工程或设计原文件，如 TexturePacker 的 .tps 文件，或 Photoshop 的 .psd 文件，可以选择放在 assets 外面来管理。

* 資料庫 (library) : 

library 是将 assets 中的资源导入后生成的，在这里文件的结构和资源的格式将被处理成最终游戏发布时需要的形式。如果您使用版本控制系统管理您的项目，这个文件夹是不需要进入版本控制的。

当 library 丢失或损坏的时候，只要删除整个 library 文件夹再打开项目，就会重新生成资源库。

* 本地設置 (local)

local 文件夹中包含该项目的本地设置，包括编辑器面板布局，窗口大小，位置等信息。您不需要关心这里的内容，只要按照您的习惯设置编辑器布局，这些就会自动保存在这个文件夹。一般 local 也不需要进入版本控制。

* 項目設定 (Settings)

settings 里保存项目相关的设置，如 构建发布 菜单里的包名、场景和平台选择等。这些设置需要和项目一起进行版本控制。

* project.json 

project.json 文件和 assets 文件夹一起，作为验证 Cocos Creator 项目合法性的标志。只有包括了这两个内容的文件夹才能作为 Cocos Creator 项目打开。而 project.json 本身目前只用来规定当前使用的引擎类型和插件存储位置，不需要用户关心其内容。

这个文件也应该纳入版本控制。

* 構建目標 (build)

在使用主菜单中的 项目 -> 构建发布... 使用默认发布路径发布项目后，编辑器会在项目路径下创建 build 目录，并存放所有目标平台的构建工程。由于每次发布项目后资源 id 可能会变化，而且构建原生工程时体积很大，所以此目录建议不进入版本控制。

```


###
Cocos Code
###

屬系申明

```
const LEVEL = cc.Enum({EASY:1,HARD:2});

@ccclass
export class Game extends cc.Component {
	// 整型
    @property(cc.Integer)
    intVar: number = 0;
    // 浮点型
    @property(cc.Float)
    floatVar: number = 0;
    // 布尔型
    @property(cc.Boolean)
    boolVar: boolean = false;
    // 节点
    @property(cc.Node)
    nodeVar: cc.Node = null;
    // 节点数组
    @property([cc.Node])
    nodeArrVar: Array<cc.Node> = [];
    // Label
    @property(cc.Label)
    labelVar: cc.Label = null;
    // 预制体
    @property(cc.Prefab)
    prefabVar: cc.Prefab = null;
    // 点
    @property(cc.Vec2)
    vec2Var: cc.Vec2 = cc.v2();
    // 自定义节点
    @property(Player)
    palyerVar: Player = null;
    // 重点来了，自定义枚举
    /**
     * 全局变量
     * const LEVEL = cc.Enum({EASY:1,HARD:2});
     */ 
    @property({
        type:LEVEL
    })
    enumVa = LEVEL.EASY;
}
```

Array 

```
參考網址 :　https://blog.csdn.net/wangshunli123/article/details/62881622
```


Interface

* 介面使用

```
interface LabelledValue
{
    label:string;
}

@ccclass
export default class a extends cc.Component
{
    @property(cc.Object)
    private o:object = null;

    start()
    {
        let myObj = {size:10 , label:'size 10 object'};
        this.printLabel(myObj);
    }

    private printLabel(labelledObj:LabelledValue)
    {
        console.log(labelledObj.label);
    }
}
```
* key / value 使用
```
參考網址 : https://oomusou.io/typescript/interface/

interface CloudDictionary
{
    [key:string]: number;
}

@ccclass
export default class a extends cc.Component
{
    start()
    {
        let clouds:CloudDictionary = {};
        clouds['aws'] = 0;
        clouds['azure'] = 1;
        clouds['gcp'] = 2;
    }
}
```



Cocos2D Life Time

```
- onLoad	腳本初始化階段，在start之前，可用於安排腳本初始化順序
- start		第一次"激活"，update之前觸發
- update	每一帧都渲染物體的行為
- lateUpdate	update 會在所有動畫之前執行，如果我們要使用 (動畫、粒子、物理等等)更新後才調用操作，就需要用到 lateUpdate
- onEnable	當物件從enabled變為 true/false，就會使 onEnable 調用。若該物件第一次創建 enable 就為 true，則會在 onLoad 和 start 之間調用
- onDestroy	當使用了destroy()，就會調用 onDestroy 回調
- onDisable	當物件 enable 從 ture->false時，就會調用
```

keyCode


https://docs.cocos.com/creator/manual/zh/scripting/internal-events.html  (重要)事件監聽
https://docs.cocos.com/creator/manual/zh/scripting/events.html  輸入事件監聽

https://blog.csdn.net/foupwang/article/details/80474072 滑鼠座標處理

取得 mouse Screen 
```
start () 
{
	this.addEventListeners();
}

private addEventListeners()
{
	this.node.on(cc.Node.EventType.MOUSE_DOWN , this.onMOuseDown , this);
}
// update (dt) {}

private onMOuseDown(event){
	let mouseType = event.getButton();
	if(mouseType === cc.Event.EventMouse.BUTTON_LEFT)
	{
	    console.log("input mouseDown");
	}
}
```


Move Action

```
var actionBy = cc.moveTo(5 , 100 , 100).easing(cc.easeBackOut());
this.node.runAction(actionBy);
* (cc.moveTo 用来移动节点到某个位置；cc.rotateBy 用来旋转节点一定的角度；cc.scaleTo 用来缩放节点)
	cc.delayTime(5)		//延遲時間

	sequence => cc.sequence(cc.moveBy(0.5, 200, 0), cc.moveBy(0.5, -200, 0));	批次執行
	spawn => cc.spawn(cc.moveBy(0.5, 0, 50), cc.scaleTo(0.5, 0.8, 1.4)); 		同步執行
	repeat => cc.repeat(
		     cc.sequence(
			 cc.moveBy(2, 200, 0),
			 cc.moveBy(2, -200, 0)
		     ), 5);			//重複執行
	repeatForever => cc.repeatForever 	//永遠重複動作
	speed => cc.speed(
			 cc.spawn(
			     cc.moveBy(2, 0, 50),
			     cc.scaleTo(2, 0.8, 1.4)
			 ), 0.5);		//可以改變移動速度  : (1)是正常速度 (0.5)兩倍速 (2)0.5倍數

```


switch 了解
get; set;
