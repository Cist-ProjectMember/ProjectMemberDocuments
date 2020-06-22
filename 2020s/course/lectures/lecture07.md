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

![](http://www.plantuml.com/plantuml/png/RLFR2jim37ttLvZi9UcQifOzXL7QFOmDrZ785pYDQ4qTEyHkkyiA_TVzo6J5Tb8Oj44-biwHZfATTM9mrqunUv6w5uFe-549Q_VE3RAvElXoDBgMlu2_O-nWj7Kmy6oJyR9Sy6oTyKyIL1jl25cKWpoTNOc7rUfznW_c1hpw-toc7qDsSRpGHNdjopzRIcACf7aa-yrugKK7LOszw1EUpj9zDrAx2lzu54GJ3eqoAROzG1lY3fc_Ikig__ZWTRQCyRT199y9B3dozv5_oSSkn_YZCZ5Cv0NIYBRrbBbNgNnKL3SZMtz3rJbew7vMGMt9fMxX1nN7F7isTw98YBHx9GbeZ54WD68dSDz4XrWqWw3FmG-4yUd9PjXaLbAZed6iL898xISA07kmk0TQBMsX6zkVsqW0EKbfUKXPJwC6P1CHRrU3hYYe_KiNvtrCQxy1YhsPhnnBo9iPLlpFZGTBNK_l5hNUcpiCD1dMJNUlUqz9HLfS76YQvsMJeNaKte5kyGFw1m00)

* Exercise7_1クラスを作成し、mainメソッドを作成しなさい。  
* 上記のクラス図に従ってMonsterクラス、AttackMoveクラス、Fieldクラス、Moveクラスを作成しなさい。
* Turtle、Monkey、Penguinの中から気に入った1匹を選択しインスタンス化しなさい。  
* name(名前),hitpoint(体力),attack(攻撃力),block(防御力),speed(素早さ)は引数付きコンストラクタにて初期化しなさい。  
* Monsterのコンストラクタに入れる値は下記のモンスターリスト①を参照しなさい。  
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
