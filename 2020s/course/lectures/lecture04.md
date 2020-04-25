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

以下のクラスを作成せよ。  

![](http://www.plantuml.com/plantuml/png/LSwn3e903CRnlK_H4H86vvjWCRgPy0G5AZGSFNDN63I-knVHHCUclt_orSaeshfuIBFeZI8js7jAgJ6Bqgt6vpveAtV60xmVU9HnCeuFmDF5YHfWiiWwshHVIWkxDjSw0dnriTlgprQ_jWGaC-hdufeJZkvJbcuBCW1AQhniN9Ik2y4pAJoXPXtozXS0)

* 作成したクラスをカプセル化し、必要に応じてアクセサを新たに追加せよ。
* 可視性は省略されているから自分で判断せよ。 
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
Fighter1 は Fighter2 に 100 ダメージを与えた。
Fighter2 の残り HP : 80
Fighter2 は Fighter1 に 150 ダメージを与えた。
Fighter1 の残り HP : 60
Fighter1 は Fighter2 に 100 ダメージを与えた。
Fighter2 の残り HP : -20
Fighter2 は倒れた。
Fighter1 は勝利した。
```

### 課題2

以下のクラスを作成せよ。 

![](http://www.plantuml.com/plantuml/png/VL31IWCn4BtdAuOzxOfRgXTX4MaF7WGzrPk8p6Q7xU1cKf9PMotzTxSsmHx4GmBllNalRxA8Ya57DvZuphB1W0xiW34kLGEtezA3zRBYBuAv-H5W-VoqDu3M-b4qDeySzNPvGdVcg9QLWK3zn5D8Gbar7vux0xIRw9XPGKVDIWDBVmaokfP2WbNJUZyGYe6EDZwobbbFuyuBVJQ3bpvdRrdNNS3jVvF7snnCMYNrcDOvQs9oamnR750idRpmH_VgD_5-Hy5of9ktwobr7nMLxG4SifGO-fWSBw-fz6Gyiq0Tk5zhVVn5CnqehWhmTGt5V3QxAFBRPa7IZMxu1W00)

* 作成したクラスをカプセル化し、必要に応じてアクセサを新たに追加せよ。
* 可視性は省略されているから自分で判断せよ。 
* mainの中でATMをインスタンス化する。
* AccountのコンストラクタでRandomクラスを用いて5桁の数字を生成し、numberを初期化せよ(数字は０から始まる可能性もある　例:00321)。
* ATMのコンストラクタでaccountsを初期化する。
* registerAccount()はScannerを用いてユーザーが入力したnameを用いてアカウントを登録する。
* exitsAccount()は引数のnameとnumberからaccountsに存在するかどうかをbooleanで返す。
* deposit()とwithdraw()は引数のnumberがaccountsに存在するとき、引数のmoneyを利用して入金と引出を行う。
* withdraw()は残高が足りないときは行えないようにする。
* それぞれ何か行うたびに、何をしたかわかるように標準出力で表示するようにせよ。

#### 実行結果

```

```

[戻る](../README.md)
