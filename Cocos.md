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








問題 :

1. AnchorPoint - Sprite Layer 調整
2. AtlasSprite - 效能查看
3. AnimatedWidget - 動畫製作


02_ui_04_progressbar 回頭看
06_layout Layout_ResizeContainer_Normal
video player 只能 android ? 用法 ?
webview     也只能android ? 用法 ?
03_gameplay  code 了解
04_audio  code 了解
05_scripting  code 了解

switch 了解


* 目前理解到 05_scripting

