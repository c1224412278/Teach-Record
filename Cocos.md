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

