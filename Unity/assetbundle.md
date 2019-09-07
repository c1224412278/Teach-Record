AssetBundle 使用介紹
===========================

<h3 id="autoescape"> 基本打包 </h3>

        static void BuildAllAssetsBundles()
        {
                string folder = "bundleFloder";                                                                               
                if (!Directory.Exists(folder)) Directory.CreateDirectory(folder);                                                  
                BuildPipeline.BuildAssetBundles("ChinarAssetBundles", BuildAssetBundleOptions.None, BuildTarget.StandaloneWindows); 
        }

        
        	            Gzip LZMA LZ4
        壓縮率（節省儲存空間   普   好   差
        壓縮速度              普   慢   快
        解壓縮速度            普 慢 快
        壓縮記憶體需求          少 多 普
        解壓縮記憶體需求       少 多 普

        BuildAssetBundleOptions.None - 使用 LZMA 格式來進行壓縮
        BuildAssetBundleOptions.UncompressedAssetBundle  -  不進行壓縮
        BuildAssetBundleOptions.ChunkBasedCompression - 使用 LZ4 格式來進行壓縮


<h3 id="autoescape"> 本地端 - 物件下載 </h3>

        string path = Application.dataPath + "/StreamingAssets/sfassetbundle/test.assetbundle";
        AssetBundle myLoadedAssetBundle = AssetBundle.LoadFromMemory(File.ReadAllBytes(path));
        GameObject target = myLoadedAssetBundle.LoadAsset(myLoadedAssetBundle.name , typeof(GameObject));
  

<h3 id="autoescape"> 本地端 - 圖片下載 </h3>

        string path = Application.dataPath + "/StreamingAssets/sfassetbundle/icon1.unity3d";
        AssetBundle myLoadedAssetBundle = AssetBundle.LoadFromMemory(File.ReadAllBytes(path));
        object sprite1 = myLoadedAssetBundle.LoadAsset("icon1", typeof(Sprite));
        target.sprite = (Sprite)sprite1;
        
<h3 id="autoescape"> 網路加載 </h3>
        
     string path = "http://127.0.0.1/bundle/target";
     while (!Caching.ready) {
            yield return null;                  //判斷快取是否可以使用
     }

     UnityWebRequest request = UnityWebRequestAssetBundle.GetAssetBundle(path);
     UnityWebRequestAsyncOperation op = request.SendWebRequest();
     while (op.isDone == false) {
        yield return null;
     }
        
     AssetBundle bundle = (request.downloadHandler as DownloadHandlerAssetBundle).assetBundle;
     GameObject target = bundle.LoadAsset<GameObject>(bundle.name);
     Debug.Log(target);
     
     
<h3 id="autoescape"> 網路加載 + 驗證 </h3>    
     
     string path = "http://127.0.0.1/bundle/target";
     Hash128 hash = Hash128.Parse("xxxxxx");
     uint crc = xxxxxxxx;

        
     while (!Caching.ready) {
        yield return null;
     }

     UnityWebRequest request = UnityWebRequestAssetBundle.GetAssetBundle(path , hash , crc);
     UnityWebRequestAsyncOperation op = request.SendWebRequest();
     while (op.isDone == false) {
        yield return null;
     }
        

     AssetBundle bundle = (request.downloadHandler as DownloadHandlerAssetBundle).assetBundle;
     GameObject target = bundle.LoadAsset<GameObject>(bundle.name);
     Debug.Log(target);
     
 
<h3 id="autoescape"> 網路加載 + 進度顯示 </h3>  
     
     string path = "http://127.0.0.1/bundle/target";
     Hash128 hash = Hash128.Parse("xxxxxxxxxxxx");
     while (Caching.ready == false) yield return null;

     UnityWebRequest httpRequest = UnityWebRequestAssetBundle.GetAssetBundle(path, hash, 0);
     {
        UnityWebRequestAsyncOperation op = httpRequest.SendWebRequest();
        while (!op.isDone)
        {
                yield return null;
        }

        if (httpRequest.isNetworkError)
        {

        }
     }

     AssetBundle bundle = (request.downloadHandler as DownloadHandlerAssetBundle).assetBundle;
     GameObject target = bundle.LoadAsset<GameObject>(bundle.name);
     Debug.Log(target);
     
     
<h3 id="autoescape"> 網路加載 - 取得bundle相關資料 (http通訊協定) </h3> 

        string path = "http://127.0.0.1/bundle/target";

        using (var httpRequest = UnityWebRequest.Head(path)) {
            yield return httpRequest.Send();
            if (httpRequest.responseCode == 200) {
                string contentLength = httpRequest.GetResponseHeader("Content-Length");         //取得bundle檔案的長度
                Debug.Log(contentLength);
            }
        }
        
        
        

     
***
參考網址 = 

https://dev.twsiyuan.com/2017/09/unity-assetbundle-cache-and-load-example.html      - assetBundle API使用
https://dev.twsiyuan.com/2016/09/brief-talk-on-http-using-postman.html      - http 網路通訊介紹
***
