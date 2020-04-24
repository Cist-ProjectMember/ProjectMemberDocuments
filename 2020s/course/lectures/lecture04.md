# アクセス修飾子とカプセル化

## アクセス範囲/アクセス修飾子

全てのクラス、フィールド、メソッドにはアクセス範囲が定められており、各クラス、フィールド、メソッドの宣言の前に以下のようなキーワード(アクセス修飾子と呼ぶ)を記述することでアクセス範囲を指定することが出来る。  

|修飾子|公開範囲|
|:-|:-|
|public|全てのクラスから参照可能|
|private|同一クラスのみ参照可能|
|protected|同一クラス/同一パッケージ/サブクラスのみ参照可能|
|(なし/package private)|同一クラス/同一パッケージのみ参照可能|

理解し辛い人は、とりあえず全てのフィールド/メソッドをprivateとして定義し、必要に応じてprotectedやpublicにすると良い。  

```java
public class Television {
	private boolean power; // Televisionクラスの中でのみアクセス可能
	private double volume;
	private int channel;

	public Television() { // 全てのクラスからアクセス可能
		this.power = false;
		this.volume = 0.0;
		this.channel = 0;
	}	
	
	public void turnPower() {
		this.power = !this.power;
	}
}
```


## アクセサ(セッター, ゲッター)

どのクラスにおいても、全てのフィールドは基本的にprivateもしくはprotected修飾子が付加されているため、外部からアクセスすることが出来ない。そこで、外部からアクセスする必要があるフィールドにのみ、setter(セッター)、getter(ゲッター)というメソッドをpublicで定義する。セッターとゲッターをまとめてアクセサと呼ぶ。アクセサはメソッド名の命名に規則があり、それぞれ  

```java
public void setChannel(int channel) {
	this.channel = channel;
}

public int getChannel() {
	return channel;
}
```

と記述する。  


## カプセル化

アクセス修飾子により外部からのアクセス範囲を制限し、アクセサにより利用してもらいたいフィールド/メソッドへのアクセスを提供することをカプセル化と呼ぶ。カプセル化はオブジェクト指向プログラミングにおける大きな要素の一つである。大きなプロジェクトにおいては、カプセル化により、利用してもらいたくないクラス/フィールド/メソッドへのアクセスを禁止することで人為的なバグを減らすことが出来る。  

現実的な例 :  
テレビのチャンネルは直接ではなく、テレビに付属するチャンネル変更ボタンやリモコンのチャンネル変更ボタンにより変更してほしい。  

カプセル化されていないと以下のようなことができてしまう。

```java
Television television = new Television();

television.channel = 2020;
```

このようなことを防ぐために、正しくカプセル化を行い、アクセサによりフィールドの値の取りうる範囲を制限する

```java
public void setChannel(int channel){
	if(channel < 0 || channel > 12) this.channel = 0;
	else this.channel = channel;
}
```

上記のアクセサを利用することで正しく範囲を制限することができるので以下のような場合はchannelが0になる。

```java
Television television = new Television();

television.setChannel(2020);
```

## クラス図について

クラス図は基本的に以下のように構成される。  
![](http://www.plantuml.com/plantuml/png/SoWkIImgAStDuIhEpimhI2nAp5L8paaiBdOiAIdAJ2ejIVLCpiyBpgnALJ3W0aieF6vQ_xXvvUEcdKydz5PpAJpjN_zYsRHd3SiLWFoddRqALWfFvtKZYp-RtFjaxnoWh8B6qprJdqtTyBXn7LmjN0IeIHEgjvRB8JKl1UWe0000)

|可視性|意味|
|:--|:--|
|+|public|
|-|private|
|#|protected|
|~|修飾子なし|

## 演習課題

### 課題1

以下のクラスを作成せよ。可視性は省略されているから自分で判断せよ。  
![](http://www.plantuml.com/plantuml/png/LSwn3e903CRnlK_H4H86vvjWCRgPy0G5AZGSFNDN63I-knVHHCUclt_orSaeshfuIBFeZI8js7jAgJ6Bqgt6vpveAtV60xmVU9HnCeuFmDF5YHfWiiWwshHVIWkxDjSw0dnriTlgprQ_jWGaC-hdufeJZkvJbcuBCW1AQhniN9Ik2y4pAJoXPXtozXS0)
* 作成したクラスをカプセル化し、必要に応じてアクセサを新たに追加せよ。
* attack()では引数で受け取ったFighterのHPを自分のstrength分減らし、与えたダメージ量と、ダメージを与えたということを表示する。
* isAlive()では自分のHPを比較し、生きているかををbooleanで返す。
* HP, strength, nameは引数付きコンストラクタにて初期化せよ。
* Fighterを2つインスタンス化し、互いに戦わせる。
* Fighterのコンストラクタに各自適当に値を見繕いインスタンス化し、main内に保持せよ。
* whileを用いて、どちらかのFighterが倒れるまで攻撃を繰り返す。
* ダメージが発生するごとに残りHPを表示する。
* ifを用いて勝敗を表示する。

#### 実行結果

```
Fighter1はFighter2に100ダメージを与えた。
Fighter2の 残りHP: 80
Fighter2はFighter1に150ダメージを与えた。
Fighter1の 残りHP: 60
Fighter1はFighter2に100ダメージを与えた。
Fighter2の 残りHP: -20
Fighter2は倒れた。
Fighter1は勝利した。
```

[戻る](../README.md)
