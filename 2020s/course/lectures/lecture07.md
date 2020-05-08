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

![](http://www.plantuml.com/plantuml/png/PP3VQgj048Vlvoc6N2MeuHperL92UbbeeE0Jh3eaIznTsHqj_LF8k_P5wcfSbOAAlt7zlfavUfQEMrs3lohJI2SrbhNq_edPgQ9bUYwjoTK7uJ-0a-q8SVD_lt_O86PEdI-SsL3PuCaQp-HG8FxSRl627YJBw_1drZRPrm73E-GikVL_oZ388-mJUesHcaJEJfbpY1V5hrOP5lqTiXm4KofgEmVV45LJq3t_HNaMuV4OR0S0JEwgxSAIujAHucn8CV9JZFGTV0F8mhEJ9UCqGKUX_NNtWw-ZfMpNrqR1bWpfTt5lQ2Swgwf07e7pmW8sYN4DcyylzXxQQEmRkN4LoVnfFNKy4p17CbMhwry0)

* Exercise7_1クラスを作成し、mainメソッドを作成しなさい。  
* 作成したクラスをカプセル化し、必要に応じてアクセサを新たに追加しなさい。     
* 3匹の中から気に入った1匹を選択しインスタンス化しなさい。  
* name(名前),hitPoint(体力),attack(攻撃力),block(防御力),speed(素早さ)は引数付きコンストラクタにて初期化しなさい。  
* Monsterのコンストラクタに入れる値は下記のモンスターリスト①を参照しなさい。  
* StatusMoveはステータスに変化をもたらす技、AttackMoveはダメージを与える技とする。  
* moveListには下記の技リストを参照しname,powerの要素を持つ技を追加しなさい。 
* 各モンスターが持つ技はモンスターリスト②を参照しなさい。
* effectを持つ技は、その効果を満たすようにメソッドを作成しなさい。  
* 
* 
* 
* 

技リスト  

|name|power|effect|
|:-------:|:------:|:------:|
|tackle(たいあたり)|10|-|
|scratch(ひっかく)|10|-|
|Peck(つつく)|15|-|
|razorLeaf(はっぱカッター)|12|-|
|ember(ひのこ)|10|-|
|bubble(あわ)|10|-|
|synthesis(こうごうせい)|-|最大HPの半分を回復する|
|withdraw(からにこもる)|-|自分のblockを3上昇させる|
|groml(なきごえ)|-|相手のattackを3減少させる|
|leer(にらみつける)|-|相手のblockを3減少させる|

モンスターリスト①

|Turtle|Monkey|Penguin|
|:-------:|:------:|:------:|
|HP:55|HP:44|HP:53|
|attack:17|attack:14|attack:12|
|block:16|block:11|block:13|
|speed:15|speed:31|speed:20|

モンスターリスト②

|Turtle|Monkey|Penguin|
|:-------:|:------:|:------:|
|tackle|tackle|tackle|
|razorLeaf|scratch|Peck|
|synthesis|ember|bubble|
|withdraw|leer|groml|

  
  
### 課題2

* Exercise7_2クラスを作成し、mainメソッドを作成しなさい。  
* 課題1でインスタンス化したMonsterとは別に野生のMonsterを新たにインスタンス化しなさい。  
* Monsterクラスにactionメソッドを作成しなさい。  
* actionメソッドではmoveListの中に入っている4つの技の中から1つ選択し、相手を攻撃する。  
* 野生のMonsterはランダムに4つの技の中から一つを使ってくるようにしなさい。
* ここでは、attack+power-block=ダメージとする。  

[目次へ](../README.md)
