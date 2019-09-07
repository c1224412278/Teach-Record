AssetBundle 使用介紹
===========================

<h3 id="autoescape"> 基本打包 </h3>

        static void BuildAllAssetsBundles()
        {
                string folder = "bundleFloder";                                                                               
                if (!Directory.Exists(folder)) Directory.CreateDirectory(folder);                                                  
                BuildPipeline.BuildAssetBundles("ChinarAssetBundles", BuildAssetBundleOptions.None, BuildTarget.StandaloneWindows); 
        }

        BuildAssetBundleOptions.None - 
        BuildAssetBundleOptions.UncompressedAssetBundle  - 
        BuildAssetBundleOptions.ChunkBasedCompression - 


<h3 id="autoescape"> 本地端下載 </h3>
        string path = Application.dataPath + "/StreamingAssets/sfassetbundle/test.assetbundle";
        AssetBundle myLoadedAssetBundle = AssetBundle.LoadFromMemory(File.ReadAllBytes(path)); //读取文件1请求
        GameObject sprite1 = myLoadedAssetBundle.LoadAsset(myLoadedAssetBundle.name , typeof(GameObject));
        
     
***
參考網址 = 

https://dev.twsiyuan.com/2017/09/unity-assetbundle-cache-and-load-example.html      - assetBundle API使用
https://dev.twsiyuan.com/2016/09/brief-talk-on-http-using-postman.html      - http 網路通訊介紹
***
