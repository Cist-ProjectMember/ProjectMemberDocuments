# Javaまとめ

本日はこれまでのJava基礎編の知識をフル活用して課題に取り組んでもらいます。  
課題で求められていることを達成できているのであれば、講習で教えた内容以外のコードを記述しても構いません。(lambdaや型推論、Streamなど)  
省略できる処理は省略してしまいましょう。(無駄に長いコードを ”冗長なコード” とも呼ぶ)  


## 演習課題

### 演習課題に取り組む前に

これまで通り、prmn2020sプロジェクト内にlecture07パッケージを作成してください。  
これより後の演習ではすべてのクラスをこのパッケージ内に作成してください。  

### 課題1

以下のクラスを作成しなさい。

![](http://www.plantuml.com/plantuml/png/ZLBjQi904FpTUuh5Nug9jD1VGOgsK5geLF09phWaXybUk5ihz0Dyrxv8xox96SGV3KcOtGaxCvjRM9Q63tKbx5vH8usi8Q-ajKjcexO7njTSqqPz8jmAiT9a6GtClzETFb8ADokK3bqXdhL1orU8znmbnJwCxaO0EZMgA3drvMnsFuAL_a3807vFftYBq8o3daf91LusDR7CMVWhn81Uw4j0IhB6REDoKU4gsISyjqh5Qws8C_UqNyXytnNRIaTi6yHTXsjdu4rPplnhxkqy207JJdSyq4mk5PENjH-IBADEyjYh955Z8iHFdoOipsUP1ZIUdAbsuO5huP1iVrCWMpWalUV_xQVHHpGXj_UqGDgva_C7)

* Exercise7_1クラスを作成し、mainメソッドを作成しなさい。
* 作成したクラスをカプセル化し、必要に応じてアクセサを新たに追加しなさい。
* 可視性は省略されているから自分で判断しなさい。
* Meadow(草原),Forest(森),Ocean(大洋)はMonsterの生息地を示す。
* MeadowにはTurtle、ForestにはMonkey、OceanにはPenguinが生息している。
* name(名前),attribute(属性),hitPoint(体力),attack(攻撃力),block(防御力),speed(素早さ)は引数付きコンストラクタにて初期化せよ。
* moveListには技リストを参考にname,attiribute,powerの要素を持つ技を追加しなさい。
* effectを持つ技は、その効果を満たすようにメソッドを作成しなさい。
* 
* 
* 
* 

技リスト  

|name|attribute|power|effect|
|:-------:|:------:|:------:|:------:|
|tackle(たいあたり)|Normal(ノーマル)|10|-|
|scratch(ひっかく)|Normal(ノーマル)|10|-|
|bite(かみつく)|Dark(悪)|15|-|
|razorLeaf(はっぱカッター)|Grass(草)|12|-|
|ember(ひのこ)|Fire(炎)|10|-|
|waterGun(みずてっぽう)|Water(水)|10|-|
|synthesis(こうごうせい)|Grass(草)|-|recover half of HP|
|withdraw(からにこもる)|Water(水)|-|block+3|
|groml(なきごえ)|Normal(ノーマル)|-|enemy's attack-3|
|scaryFace(こわいかお)|Normal(ノーマル)|-|enemy's speed-6|
|leer(にらみつける)|Normal(ノーマル)|-|enemy's block-3|






|Turtle(草)|Crocodile(水)|Cat(炎)|
|:-------:|:------:|:------:|
|HP:30|HP:30|HP:30|
|attack:10|attack:10|attack:10|
|block:8|block:8|block:8|
|speed:4|speed:4|speed:4|
|absorb(すいとる)|waterGun(みずてっぽう)|ember(ひのこ)|
|withdraw(からにこもる)|screech(いやなおと)|groml(なきごえ)|
|tackle(たいあたり)|tackle(たいあたり)|tackle(たいあたり)|


