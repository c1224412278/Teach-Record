參考網址
==================

<h3 id="autoescape"> Editor ReorderableList </h3>

https://dev.twsiyuan.com/2016/07/unity-editor-reorderablelist.html?fbclid=IwAR2k7kOjvnNOVfqn3hZyFnIqY_PC5P_xipdIPR751-EycxAMG5qbPS5qTow


<h3 id="autoescape"> Excel 讀取 </h3>

http://apperdog.pixnet.net/blog/post/378471388-%5Bunity%5D-c%23-%E8%BC%95%E9%AC%86%E8%AE%80%E5%8F%96-excel%E6%AA%94?fbclid=IwAR069aZnXTGRFbFb5hUXmMHgFA-0uIZhy3PSeQHui1Dl_uBZ-JWngQ94VC0

http://www.xuanyusong.com/archives/2429?fbclid=IwAR0GajPfownvzy7p3Axtp0dLXlWxPUmJS2Qhh4QVY3FOZBer3ipXm46mDbU


<h3 id="autoescape"> Json 產生器 </h3>

http://json.parser.online.fr/

http://json2csharp.com/?fbclid=IwAR0ccfSMvgFLMVHwal3BMgqvlCFcneHB4hdeMqCDywiMQWv9xgG_gq3Xoe4


<h3 id="autoescape"> Light Probe Group 詳細介紹 </h3>

http://www.300460.net/unity3d/21701644695410210051.html


<h3 id="autoescape"> Light 詳細介紹 </h3>

http://www.xionggf.com/…/graph…/u3d/u3d_gi_introduction.html        // Light 設定解析

http://www.cnblogs.com/tonge/p/3899981.html                         // 一般光源介紹


<h3 id="autoescape"> Material 詳細介紹與設定 </h3>

https://nuysoft.gitbooks.io/unity-manual/content/Manual/StandardShaderMaterialParameterNormalMap.html?fbclid=IwAR2X6y6RYWauiQX4CrxLnlBP-3HlOJAtwGK1glLBR4le2EWwL0IWeefU-UY


<h3 id="autoescape"> Mesh 詳細介紹 </h3>

https://blog.csdn.net/ecidevilin/column/info/12888


<h3 id="autoescape"> Prefab 尋找預製物件 (Editor功能套件) </h3>

```
[MenuItem("Assets/Check Prefab Use ?")]
public static void OnSearchForReferences()
{
	if(Selection.gameObjects.Length != 1)
	{
		Debug.Log("錯誤");
		return ; 
	}
	foreach(EditorBuildSettingsScene scene in EditorBuildSettings.scenes)
	{
		if(scene.enabled)
		{
			EditorApplication.OpenScene(scene.path) ;

			GameObject[] gos = (GameObject[])FindObjectsOfType(typeof(GameObject)) ;
			foreach(GameObject go in gos)
			{
				if(PrefabUtility.GetPrefabType(go) == PrefabType.PrefabInstance)
				{
					UnityEngine.Object parentObject = EditorUtility.GetPrefabParent(go) ;
					string path = AssetDatabase.GetAssetPath(parentObject); 
					if(path == AssetDatabase.GetAssetPath(Selection.activeGameObject))
					{
						Debug.Log(scene.path) ; 
					}
				}
			}
		}
		else 
		{
			Debug.Log("操作錯誤");
		}
	}
}
```



<h3 id="autoescape"> ScriptableObject 詳細介紹 </h3>

https://blog.csdn.net/candycat1992/article/details/52181814


<h3 id="autoescape"> Tile Map 詳細介紹 </h3>

https://kendevlog.wordpress.com/2018/01/18/unity%E5%AD%B8%E7%BF%92%E7%AD%86%E8%A8%9811-%E5%88%B6%E4%BD%9C%E7%B0%A1%E5%96%AEscriptable-tile/?fbclid=IwAR0dRl7NYtum_qf1PplkEr5kImjHgWlRbUAjI1_-xj0E6GqP4rHCPekBt_Q
https://docs.unity3d.com/ScriptReference/Tilemaps.TileBase.RefreshTile.html?fbclid=IwAR2Q73CaWWeZZ1cRDEQlXNpg6FZ5q_lJRjGkwoChYcgsmYPLC7D836ZrwX0


<h3 id="autoescape"> Unity Event System </h3>

http://k79k06k02k.com/blog/440/unity/unity-ugui-%E5%8E%9F%E7%90%86%E7%AF%87%E5%9B%9B%EF%BC%9Aevent-system-manager-%E4%BA%8B%E4%BB%B6%E8%88%87%E8%A7%B8%E7%99%BC?fbclid=IwAR3P4dewdsQ17mC3rTjKvXL5cNzEFMOcODGYRaHv4ygRERTz5lgR8rnWKJg

<h3 id="autoescape"> Unity 優化小技巧 </h3>

http://blog.csdn.net/candycat1992/article/details/42127811

<h3 id="autoescape"> 矩陣教學  </h3>

http://www.cnblogs.com/jeason1997/p/5778374.html?fbclid=IwAR3HAK452H2qEcVRNBHYpkE9WZ0IRXAr2eSTPIhu-ay_aCJQZESGsRTd1ug

https://indienova.com/indie-game-development/use-matrices-to-transform-space/?fbclid=IwAR1wtlvbbJ85Qpt55cO9Zdp1MtNGsTbCuVCQOO7_DDiBiPQEziqMvE471z8

<h3 id="autoescape"> 攝影機晃動 </h3>

https://gist.github.com/ftvs/5822103?fbclid=IwAR0YaZ4L32Ws91DvpBWG76vb94xFmJy0trlxxRDmvluzSwzv1EXYY-4BwkM#file-camerashake-cs-L27





<h1 id="autoescape"> Shader </h1>

<h3 id="autoescape"> shader 範例參考 </h3>


http://www.shaderslab.com/shaders.html		- 多 shader 範例


- 邊緣光
https://home.gamer.com.tw/creationDetail.php?sn=3648617&fbclid=IwAR1fmchC84LcQrZu57wKadZgTKeo9n_y4Nz6yzzCN50MqVyPaQ2cboVbR30


- 複雜光照 詳解
https://blog.csdn.net/u010848412/article/details/72955213?fbclid=IwAR32VfVO-Z5uDUBDRPaNHzEpsaVrbNMTNMf3oQHHFluscoAo_EhqiSbN2ig


- Normal Map
https://home.gamer.com.tw/creationDetail.php?sn=3635492&fbclid=IwAR2K_1M9XREpO3qjbj1vRU3s7N776VtaY0w0ZL8ly356mHM_bjCfKlLzKuo


- 官方教學
https://docs.unity3d.com/Manual/SL-ShaderSemantics.html?fbclid=IwAR1Qt14W-37FTNEG2vVr6WP8ucFW2b3JJaC2XajITzCnWDWAejOg1mGtg2E


<h3 id="autoescape"> 法線預覽器 </h3>

https://cpetry.github.io/NormalMap-Online/?fbclid=IwAR1uQnuGYt6w3SFQ2h2tY_WgIyRQrOB24-N0aO0gGqmBLUychEos0x3qzZk

<h3 id="autoescape"> 法線介紹 </h3>

https://www.facebook.com/notes/hui-ku-shih/unity-shader-04-%E7%9C%8B%E4%BC%BC%E7%B0%A1%E5%96%AE%E5%AF%A6%E9%9A%9B%E4%B8%8A%E5%BE%88%E8%A4%87%E9%9B%9C%E7%9A%84normal-map-shader/10153340555852284/

http://gad.qq.com/article/detail/28348?fbclid=IwAR0rhgJciZnba9yCRjSRHcqQkLiPbxIVajnwGjcmd0T5vqfabuF4lNapoWk

https://blog.csdn.net/candycat1992/article/details/41605257?fbclid=IwAR1Ysz6ij2YQML6ILLj1J2pP3raPXrJBRxluzFr4luzKlRhenPaDyFj5z0w

https://www.cnblogs.com/guxin/p/unity-normal-map-shader-demo.html?fbclid=IwAR1kAb5DnGmoO1a1YPoCgWmLATaCL4X6JgZt-QgW48wQsIDh03RoZC2fgJI
