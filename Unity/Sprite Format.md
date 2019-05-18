
Texture Format
==============================

| 尺寸 | ETC 4bits | RGBA 16bit | RGBA 32bit |
| ------ | ------ | ------ | ------ | 
| 2048 | 2.7mb | 10.7mb | 21.3mb |
| 1024 | 682.8 | 2.7 mb | 5.3mb |
| 512 | 170.8 | 682.7 | 1.3mb |
| 256 | 42.8 | 170.7 | 341.3 |
| 128 | 10.7 | 42.8 | 85.3 |
| 64 | 2.7 | 10.7 | 21.3 |

***
```
bit 的差別 => 
  8bit:圖片中的顏色只會有2的8次方256種色彩。
      (若圖片顏色不超過256種，使用8bit可以節省效能) (通常圖片只使用256種色彩都會非常難看)
  32bit:圖片中的顏色只會有2的32次方xxx種色彩。


Unity打包圖片出來的資源會比原檔案還來得大，以下為主要判斷 : 
  1. 圖片長寬大小
  2. 圖片是否是2的冪次方
  3. 圖片是否是正方形
  4. 圖片的壓縮格式
```
***

```
Crunched vs Compressed (類似的功能，Crunched 會顯示較多的壓縮訊息)


在不支持sRGB DXT的Web瀏覽器運行時，在執行時會變成 RGBA32。(不支持的原因可能有瀏覽器版本過舊)

RGB Compressed DXT1 : 格式將圖片壓縮成 4位/像素，並在PC，控制台和Windows Phone平台上得到廣泛的支持。
                      壓縮大多數RGB紋理是很好的格式，但對於 RGBA（帶alpha）紋理，請使用 DXT5。
                     
RGBA Compressed DXT5 : 壓縮RGBA紋理，為漫反射和高光控制紋理的主要格式 1位/像素(64KB, 256x256)。

RGB Compressed ETC 4bits : 壓縮RGB纹理，是Android平台默認的纹理格式，不支持alpha通道。(32KB, 256x256)
RGBA Compressed ETC2 8bits : 壓縮的RGBA紋理。這是Android項目具有Alpha通道的紋理的默認紋理壓縮格式。

RGB 16bits : 不帶 alpha，壓縮的格式會使用更多內存，只適合 UI纹理(128KB,256x256)。
RGBA 16bits or RGBA 16bits : 低質量彩色，有16bit的紅藍綠和alpha通道，容量是ETC的"4"倍(128KB, 256x256)
RGB 24bits : 色彩不带alpha通道(192KB, 256x256)
Alpha 8bits : 高質量alpha通道，不帶颜色(64KB, 256x256)

Automatic Turecolor : 最高質量的色彩，是32位的色彩(256x256的纹理大小为256KB)

PVRCT : 貼圖尺寸須為二的冪次方之正方貼圖，適合 "IOS" 平台使用

```
