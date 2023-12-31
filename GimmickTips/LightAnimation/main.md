# 光がパァーってなってオブジェクトが出現するやつ

## 目次
* [完成イメージ](#完成イメージ)
* [下準備](#下準備)
* [作り方](#作り方)


## 完成イメージ
![](./images/cluster-LightAnimation-2.gif)

## 下準備
* PostProcessingのインポート
![](./images/PostProcessing_install.png)

## 作り方
1. Post-process Volumeを作る<br>
 ![](./images/PostProcessing01.png) 
2. Post-process VolumeのProfileのところにあるNewボタンをクリックして、Post-process Volume Profileを作成する<br>
 ![](./images/PostProcessing02.png)
3. Add effect...ボタンをクリックして、Unity→Bloomを追加する<br>
4. Bloomの値をいい感じに設定する<br>
![](./images/PostProcessing03.png)
  <br>値とその内容(参考までにどぞ)
    * Intensity:明るさ(大きいほど明るくなる)
    * Threshold:輝度の閾値(小さいほどぼやけた感じになる)
    * Color:Bloomの色

      [※他のやつや詳しく知りたい人はここ見てみてね！](https://learn.unity.com/tutorial/posutopurosesuehuekuto-bloom?language=ja#)
5. Post-process VolumenのIs Globalにチェックを入れる
  <br>※Post-processの範囲を自分で決めたいよーって方は、チェックせずにコライダーでいい感じに調整してね！
6. Layerの21にPostProcessingの名前を付けて、Post-process VolumenのレイヤーをPostProcessing(Layer 21)にしてあげる<br>
![](./images/PostProcessing05.png)
![](./images/PostProcessing04.png)

7. スイッチの作成
  <br>適当なオブジェクト(今回はcubeでやります)にInteract Item TriggerとGlobal LogicのCCKスクリプトをつけてあげる<br>
  両者ともTargetの型をGlobalにし適当な名前(同一名)をつけてあげる<br>
  Interact Item TriggerのValueはSignalのままで！<br>
  Global Logicで+ボタンを押して、以下の条件式を記述してあげる<br>
![](./images/PostProcessing06.png)

9. Post-process VolumeにOn Create Item TriggerとSet Game Active GimmickのCCKスクリプトをつけてあげる<br>(On Create Item Triggerはちゃんとコントローラーのオブジェクトを作って管理するのもいいかも)<br>
  両者ともTargetの型をGlobalにし適当な名前(同一名)をつけてあげる<br>
  On Create Item TriggerのValueはBoolにして、初期値はFalse(チェックなし)にしてあげる<br>
![](./images/PostProcessing07.png)

10. Animationを作成する<br>
  ![](./images/PostProcessing08.png)

11. AnimationをPost-process Volumeにアタッチしてあげる<br>
(Post-process VolumeというAnimation Controllerが自動で作成されるよ！)
![](./images/PostProcessing09.png)

12. Animationを開く(AnimationControllerの方じゃないよ)<br>
![](./images/PostProcessing10.png)

13. Add PropertyをクリックしてPost-process VolumeのWeightを追加してあげる<br>
![](./images/PostProcessing11.png)

14. フレーム数を300(5秒)にしてあげて、Add keyframe.(真ん中の◇+)のボタンをクリック<br>
![](./images/PostProcessing12.png)

15. フレーム数を150(2.5秒)にしてあげて、Add keyframe.(真ん中の◇+)のボタンをクリック<br>

16. フレーム数60(1秒)のkeyframeを右クリックDelete Keyで削除<br>
![](./images/PostProcessing13.png)

17. こんな感じになればOK！<br>
![](./images/PostProcessing14.png)

18. Previewの隣にある赤いボタンを押してから、フレーム数0と300のPost-process VolumeのWeightを0にしてあげる<br>
![](./images/PostProcessing15.png)
![](./images/PostProcessing16.png)

19. こんな感じにアニメーションが動けばOK！<br>
![](./images/cluster-LightAnimation-1.gif)

20. 出現させたいオブジェクトを作成(今回はSphereにするよ)
  <br>そのオブジェクトに8で行ったように、On Create Item TriggerとSet Game Active GimmickのCCKスクリプトをつけてあげる<br>
  両者ともTargetの型をGlobalにし適当な名前(同一名)をつけてあげる<br>
  On Create Item TriggerのValueはBoolにして、初期値はFalse(チェックなし)にしてあげる<br>
  ![](./images/PostProcessing17.png)

21. スイッチにGlobal TimerとGlobal Logicを付け加えてあげる<br>
  両者とも型(Target)はGlobalにしてあげる
  <br>Global TimerのKeyはスイッチのInteract Item Timerのやつと同じにする
  <br>Delete Time Secondsは処理を遅延してほしい秒数(今回は3秒)にする
  <br>+ボタンを押して処理を追加するTargetやValueはInteract Item Triggerの時と同様に定める
  <br>Global Logicの方も初めに追加したGlobal Logicと同時に定める
  <br>(※keyの名前は初めに作ったInteract Item TriggerやGlobal Logicと同じにしてはダメだよ)<br>
  ![](./images/PostProcessing18.png)

21. スイッチにマテリアル切り替え機能やCanvas,Textを使ってアレンジを加える(お好みでどうぞ)<br>

22. 完成！<br>
