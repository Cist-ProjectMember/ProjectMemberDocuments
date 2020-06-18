# Javaまとめ

本日はこれまでのJava基礎編の知識をフル活用して課題に取り組んでもらいます。  
課題で求められていることを達成できているのであれば、講習で教えた内容以外のコードを記述しても構いません。(lambdaや型推論、Streamなど)  
省略できる処理は省略してしまいましょう。(無駄に長いコードを ”冗長なコード” とも呼ぶ)  


## 演習課題(調整中6/4~)

### 演習課題に取り組む前に

これまで通り、prmn2020sプロジェクト内にlecture07パッケージを作成してください。  
これより後の演習ではすべてのクラスをこのパッケージ内に作成してください。  

### 課題1

以下のクラスを作成しなさい。

![](http://www.plantuml.com/plantuml/png/RLDTYzGm57tFhmZpr6AxE288HMH7S55mVUcZYAJDjHCs7oN9xlZ1olvN_uYvcVIQ0M6cJKvopxdd9BqEKVXuRpGBTygkmWl3Por2ECJerNGVuSFixAX-0d_EsBllu6SLuDNNFUyrV8izlr6WvUM2T2VRyqGWvhjRzm3_MxrrDaJmhBmvt-rtdBlUg-KOUvnUNRtSLIHyuFpFqnFz66EvJxun_6AyjyB0CAR6xP9cHnLNfsmSqZzDHUOgaqax6eSLG9QnIL8VLOW3FbwZy1l6-BCYqbG2NKtV7OYyUxjHTqJS9WeX9T8rg33Wg1qUd9AuaciRi61-34MfKrX7MyBHdN8r8IeSjCh0v9m6OHEsGFmaJC8e0uJUbpuJd9v8Lc5aebB3ehCVAad8Y6OAm1uf_dp-6FvlS-wyJYy3ES0RK5esPSkUN1RWnGPWK5FAGyE8ztAp-xYfOGQeLPq3iYFSL5Xx4KR8698KclfQuRLPtGay6aCkMhjWx6XFIoUssI4trGcYbNzjLnz0qZD2sKRu9HJkpr_8vZLOcJx6lm00)

* Exercise7_1クラスを作成し、mainメソッドを作成しなさい。  
* 作成したクラスをカプセル化し、必要に応じてアクセサを新たに追加しなさい。     
* Turtle、Monkey、Penguinの中から気に入った1匹を選択しインスタンス化しなさい。  
* name(名前),hitPoint(体力),attack(攻撃力),block(防御力),speed(素早さ)は引数付きコンストラクタにて初期化しなさい。  
* Monsterのコンストラクタに入れる値は下記のモンスターリスト①を参照しなさい。  
* HealMoveは体力を回復する技、AttackMoveはダメージを与える技とする。  
* moveListには下記の技リストを参照しname,powerの要素を持つ技を追加しなさい。 
* 各モンスターが持つ技はモンスターリスト②を参照しなさい。
* どのモンスターをインスタンス化したのかを分かるように表示させなさい。  

モンスターリスト①

|Turtle|Monkey|Penguin|
|:-------:|:------:|:------:|
|HP:55|HP:44|HP:53|
|attack:17|attack:14|attack:12|
|block:16|block:11|block:13|
|speed:15|speed:31|speed:20|

技リスト  

|name|power|
|:-------:|:------:|
|tackle(たいあたり)|10|
|scratch(ひっかく)|10|
|Peck(つつく)|15|
|razorLeaf(はっぱカッター)|12|
|ember(ひのこ)|10|
|bubble(あわ)|10|


モンスターリスト②

|Turtle|Monkey|Penguin|
|:-------:|:------:|:------:|
|tackle|scratch|Peck|
|razorLeaf|tackle|tackle|
||ember|bubble|  
  
  
### 課題2

* Exercise7_2クラスを作成し、mainメソッドを作成しなさい。  
* 課題1でインスタンス化したモンスターとは別に野生のモンスターを新たにインスタンス化しなさい。  
* Moveクラスにattackメソッドを作成しなさい。
* Monsterクラスにmoveメソッドを作成しなさい。 
* MoveメソッドではmoveListの中に入っている3つの技の中から1つ選択し、attackメソッドを実行しなさい。 
* 野生のモンスターは3つの技の中からランダムに1つを選択し、attackメソッドを実行するようにしなさい。  
* Monsterクラスにjudgeメソッドを作成しなさい。
* judgeメソッドでは、どちらのモンスターの方が素早いかを判定しなさい。
* バトルを行う際には、speedが高いモンスターから行動を開始しなさい。
* whileを用いて、どちらかのFighterが倒れるまで攻撃を繰り返しなさい。  
* ダメージが発生するごとに残りHPを表示させなさい。  
* ここでは、attack+power-block=ダメージとする。 
* ifを用いて勝敗を表示しなさい。

[目次へ](../README.md)
