# SkyBoxをいい感じに切り替えれるスイッチ

## 目次
* [完成イメージ](#完成イメージ)
* [下準備](#下準備)
* [作り方](#作り方)

## 完成イメージ
![](./images/cluster_SkyBoxSmoothChange15s.gif)

## 下準備
* ほびわんぷらねっと様の「[【無料】ObjectSkyboxシェーダー](https://hobione.booth.pm/items/2972214)」をダウンロード
* 適当なSkyBoxのテクスチャをインポート(今回は、ai_works様の[【CC0】4K HDR SKYBOX for Unity 2019（24種類）](https://booth.pm/ja/items/3201726)を使用させていただきます)

## 作り方
1. 空のオブジェクトを作成(全ての機能を入れる箱みたいなものだよ)<br>
  ![](./images/SkyBoxSwitch01.png)

2. スイッチボードとスイッチを作成<br>
(今回は6つのSkyBoxを切り替えられるスイッチを作るよ)

3. スイッチを付けるボードを作成<br>
  (x:1.0, y:1.5, z:0.1のCubeを用意してね)<br>
  ![](./images/SkyBoxSwitch02.png)

4. スイッチのオブジェクトを作成<br>
  スイッチをまとめたものを入れるための空オブジェクトを作成してから、その子どもにCubeオブジェクト作成<br>
  ![](./images/SkyBoxSwitch03.png)

5. スイッチの機能を作成<br>
  スイッチにInteract Item Triggerを付けよう(トリガーのTargetとValueは以下のようにしてね)<br>
  ![](./images/SkyBoxSwitch04.png)<br>

  スイッチにGlobal Timerを付けよう(Target,Key等は以下のようにしてね)<br>
  ![](./images/SkyBoxSwitch05.png)

6. 同様の手順でスイッチを6つに増やしてね<br>
  (スイッチの位置やTarget,Keyの名前のパターンに気を付けてね)<br>

  スイッチ2<br>
    ![](./images/SkyBoxSwitch06.png)<br>
  
  スイッチ3<br>
    ![](./images/SkyBoxSwitch07.png)<br>
  
  スイッチ4<br>
    ![](./images/SkyBoxSwitch08.png)<br>
  
  スイッチ5<br>
    ![](./images/SkyBoxSwitch09.png)<br>
  
  スイッチ6<br>
    ![](./images/SkyBoxSwitch10.png)<br>

7. 各Itemのトリガーを管理するオブジェクトを作成<br>
  (空のオブジェクトを作成したら、On Create Item Triggerを付けて、TargetとValueを以下のようにしてね)
  ![](./images/SkyBoxSwitch11.png)<br>

8. SkyBoxにあたるオブジェクトを作成<br>
  各SkyBoxオブジェクトを入れる空のオブジェクトを作成し、その子どもに大きさ100のSphereを作成(コライダーは削除する)<br>
  Set Game Object Active Gimmickを付けて、TargetをGlobal,KeyをSkyBox01にしよう<br>
  ![](./images/SkyBoxSwitch12.png)<br>

9. SkyBoxオブジェクトを操作するAnimation Controllerを作成<br>(Projectのタブで右クリックCreate→Animation Controllerで作成できるよ)<br>

10. Animation ControllerをSkyBoxオブジェクトにアタッチ

11. Animationタブを開いて(Ctrl+6)、Create New ClipでSkyBoxオブジェクトがActivateにするAnimationクリップとDeactivateするAnimationクリップを作成<br>
  ![](./images/SkyBoxSwitch14.png)<br>
  ![](./images/SkyBoxSwitch15.png)<br>

12. AnimationクリップでAdd PropertyでMesh Renderer.Material._Opacityの項目を追加<br>
Activateするアニメーションでは、値の大きさを5秒かけて0から1にする<br>
Deactivateするアニメーションでは、値の大きさを5秒かけて1から0にする<br>

13. Animatorタブを開いて、先程の作ったAnimation Clipを以下の様に配置する<br>
  ![](./images/SkyBoxSwitch16.png)<br>

14. SkyBoxOFFのパラメーターをTriggerで追加する<br>13でSkyBoxONステートからSkyBoxOFFステートに行くためのConditionをSkyBoxOFFトリガーにする<br>

15. SkyBoxオブジェクトにSet Animator Value Gimmickを付けて、以下の様に設定しよう<br>
  ![](./images/SkyBoxSwitch17.png)<br>

16. 同様の手順でSkyBox02～SkyBox06を設定するオブジェクトを作成<br>(AnimatorやAnimationは使いまわしてOK)<br>

  SkyBox02<br>
  ![](./images/SkyBoxSwitch18.png)<br>

  SkyBox03<br>
  ![](./images/SkyBoxSwitch19.png)<br>

  SkyBox04<br>
  ![](./images/SkyBoxSwitch20.png)<br>

  SkyBox05<br>
  ![](./images/SkyBoxSwitch21.png)<br>

  SkyBox06<br>
  ![](./images/SkyBoxSwitch22.png)<br>

17. 各SkyBoxオブジェクトに対応するSkyBoxのTextureをObjectSkyboxCube(ほびわん様のSharderを使用したマテリアル)のマテリアルを用いて貼る<br>
[ObjectSkyboxSharderの使い方](https://note.com/homura_cluster/n/n668499b6e4f8)<br>

18. スイッチに色を付けたり、押したら赤くなる様にしたりアレンジを加えて完成！<br>