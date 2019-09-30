UnityWebRequest
==============================


```
log檢查API

webRequest.responseCode 當前連線狀態
webRequest.downloadHandler.text 文件內容
```


```
Get
------------
private IEnumerator DoRequest()
{
	var request = UnityWebRequest.Get("http://twsiyuan.com");
        yield return request.Send();

        if (request.isNetworkError)
        {
            Debug.Log(request.error);
            yield break;
        }
        
        var html = request.downloadHandler.text;		// print 出 html碼
        Debug.Log(html);
}
```

```
POST
---------------
UnityWebRequest webRequest = UnityWebRequest.Post("http://127.0.0.1/test.php");
yield return webRequest.SendWebRequest();

if(webRequest.isHttpError || webRequest.isNetworkError){
	Debug.Log(webRequest.isHttpError);
	Debug.Log(webRequest.isNetworkError);
}
else{
	Debug.Log(webRequest.responseCode);
	Debug.Log(webRequest.downloadHandler.text);
}
```

```
圖片載入
-------------
var request = UnityWebRequestTexture.GetTexture("http://twsiyuan.com/images/profile.jpg");
yield return request.Send();

if (!request.isNetworkError)
{
	var tex = (request.downloadHandler as DownloadHandlerTexture).texture;
	var rect = new Rect(0, 0, tex.width, tex.height);
	var pivot = new Vector2(0.5f, 0.5f);
	var sprite = Sprite.Create(tex, rect, pivot);

	// TODO: Sprite Rendering
	image.sprite = sprite;
}
```

```
音效載入
--------------
var request = UnityWebRequest.GetAudioClip("http://example.com", AudioType.MPEG);
yield return request.Send();

* var audioClip = DownloadHandlerAudioClip.GetContent(request);		// 可使用 DownloadHandlerAudioClip 做銜接
* var request = UnityWebRequestTexture.GetTexture("http://twsiyuan.com/images/profile.jpg");	// UnityWebRequestTexture
```


```
WWWForm / POST
---------
WWWForm form = new WWWForm();
form.AddBinaryData("file" , texture2D.EncodeToPNG() , "test.jpg");
		

UnityWebRequest webRequest = UnityWebRequest.Post("http://127.0.0.1/test.php" , form);
yield return webRequest.SendWebRequest();

if(webRequest.isHttpError || webRequest.isNetworkError){
	Debug.Log(webRequest.isHttpError);
	Debug.Log(webRequest.isNetworkError);
}
else{
	Debug.Log(webRequest.responseCode);
	Debug.Log(webRequest.downloadHandler.text);
}

```



參考文獻
https://dev.twsiyuan.com/2016/09/unity-web-request.html		// 思元大的筆記
