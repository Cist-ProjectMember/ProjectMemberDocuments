# 継承

## はじめに

今回の内容「継承」は、Javaの基礎を学習する上での最大の壁です。  
講習時間にスライドを1から見るのでは課題に取り組む時間が足りませんので、事前に資料を読み、読んでも分からない点はインターネットを活用してください。  
重要なキーワードは次のスライドに記載していますので、それをもとにしてください。  

## 継承の概念

大規模な開発においては、コードの様々な場面で似たようなコードが使われている。  
コード量や変数の量、バグの量は比例関係にあるため、いかにコード量、変数量を減らすかがカギとなる。  
関数により一部のまとまった処理は1つの関数の呼び出しに置き換えることが出来るが、それだけでは限界がある。  
ここで用いるのが __継承__ という概念である  
オブジェクト指向言語では、オブジェクト間の関係を考えつつプログラムを構築する必要がある。  
プロジェクト中のクラスの数が数十、数百と増えてくると、似たような機能を持ったクラスが必ず出てくる。  
ここで、似たような機能を持つクラスの元となるクラスを作成し、その機能を引き継いだ(継承した)クラスに分割することで、コードの重複を減らし、コード量を減らすことが出来る。  

## Javaにおける継承

Javaにおいて、SubClassがSuperClassクラスを継承するとき、extendsキーワードを用いて、

```java
class SubClass extends SuperClass {  
/* フィールドやメソッド */  
}
```

と記述する。  
この時、SuperClassはスーパークラスといい、それを継承したSubClassはサブクラスという。  

```java
// 家電クラス(スーパークラス)
class Appliance {    }
// テレビクラス(家電クラスのサブクラス)
class Television extends Appliance {    }
// オーブンクラス(家電クラスのサブクラス)
class Oven extends Appliance {    } 
```

スーパークラスを継承したサブクラスでは、スーパークラスで定義されたpublicやprotectedなメソッド、フィールドにアクセスすることが出来る。  
protected修飾子の付いたメソッド/フィールドは、同一クラスや同一パッケージ、サブクラスからのみアクセス可能である。  
アクセス修飾子ごとのアクセス可能範囲については #3の資料を見ること。  
__注意__
サブクラスが一度に継承できるスーパークラスは1つまでとなっている。  

```java
// ダメな例
/* 人間は生物(Creature)であり哺乳類(Mammalian)だが、一度に継承できるのは1クラスのみ */
class Human extends Creature, Mammalian {    }
```

前スライドの解決策(例):
矢印の先が向いているクラスがスーパークラスである
/*image*/


## オーバーライド

サブクラスでは、スーパークラスのメソッドを再定義(上書き)することが出来る。  
このメソッドの処理内容を上書きすることをオーバーライドという。  
また、メソッドをオーバーライドするときには、@Overrideアノテーションを用いる。  

```java
@Override
```

"@" から始まる特別な記述はアノテーションと言い、プログラムに対してメタデータを付加することが出来る。  

```java
public class Animal {
		public void bark(){	  }
	}
	public class Dog extends Animal {
		// @Overrideをメソッドの定義の前に書き、bark()をOverrideする
		@Override
		public void bark(){
			System.out.println(“わんわん！”);
		}
}
```


## superキーワード

サブクラスの中からスーパークラスで定義したフィールドやメソッド(コンストラクタは除く)には、superキーワードとドット演算子を用いてアクセスすることが出来る。  

```java
public class SmartPhone extends CellPhone {
		public void showPhoneNumber(){
			System.out.println(super.phoneNumber);
    }	// CellPhoneで定義されているphoneNumber
}
```

サブクラスからスーパークラスのコンストラクタを明示的に呼び出したい場合、super()を用いる。  
super()は、サブクラスのコンストラクタの引数として受け取った値をスーパークラスに渡したい場合に用いる。  

```java
public SmartPhone(long phoneNumber){
	super(phoneNumber);
}	// CellPhoneのコンストラクタを呼び出している
```


## superクラスとサブクラスの関係

以降、上のタイトルがついているスライドでは以下のクラス(Animal, Dog)が定義されているものとする。

```java
class Animal {
	protected String barkSound;  // protectedはサブクラスからのアクセス可
	public Animal(String barkSound){
		this.barkSound = barkSound;
  }
  public void bark(){
	  /* 処理なし */
  }
}
```


```java
class Dog extends Animal {
	public Dog(String barkSound){
		super(barkSound);
}
@Override
public void bark(){
	System.out.println(“犬の鳴き声: ” + super.barkSound);
}
}
```

DogがAnimalを継承している時、A is B(Dog is Animal)の関係が成り立つ。  
そのため、Animal型の変数にDog型のインスタンスへの参照を代入することも出来る。

```java
	Animal animal = new Dog(“わんわん！”);	
	animal.bark();	// Animalであれば必ずbark()メソッドを持っている
```

さらに、Animalを継承したCat、Birdクラス・・・ などを作ることで、すべてのクラスをAnimal型として扱うことが出来る。
これより、以下のような記述も可能である。

```java
Animal animal = new Dog(“わんわん！”);
animal.bark();	// 犬の鳴き声: わんわん！
animal = new Cat(“にゃーにゃー”);
animal.bark();	// 猫の鳴き声: にゃーにゃー
animal = new Bird(“ちゅんちゅん”);
animal.bark();	// 鳥の鳴き声: ちゅんちゅん
```

さらに、配列を用いることで以下のような記述も可能である。

```java
Animal[] animals = { 
	new Dog(“わんわん！”), 
	new Cat(“にゃーにゃー”), 
	new Bird(“ちゅんちゅん”)  
};
```

```java
	for(Animal animal : animals) {
		animal.bark();		// Animalを継承していればbark()を持っている
	}
```


## 抽象クラス

Javaではnewによるインスタンス化が出来ないクラスを定義することが出来る。</br>
このクラスを抽象クラスといい、classの前に abstract修飾子 を付けることで定義することが出来る。

```java
	abstract class AbstractAnimal {
		public AbstractAnimal(){		}
}
```

`AbstractAnimal abstractAnimal = new AbstractAnimal();`とするとエラーが出る。

## 抽象メソッド

メソッドにabstract修飾子を付けることで、メソッドの定義を省くことができる。  
ただし、abstract修飾子の付いたメソッドを持つクラスは抽象クラスとなるため、インスタンス化できなくなる。  
また、abstract修飾子の付いたメソッドを持つクラスを継承したサブクラスは、そのメソッドを必ずOverrideしなければならない。  
C言語のプロトタイプ宣言と同じような記述が可能である。

```java
public 	abstract class AbstractClass {
		public abstract void execute();		// {} は必要ない
}
public class SubClass extends AbstractClass {
	@Override
	public void execute(){
		// 処理
	}
}
```


## 演習課題

### 課題1

以下のクラス図で示されるクラスを作成しなさい。  
/*image*/

#### Computerクラス

* boot()
  * 自身を構成するパーツが正常に組み込まれているかを確認する
  * また、組み込まれている/組み込まれていないおよび、各パーツの性能を標準出力に表示する

#### Storageクラス

このクラスは抽象クラスとして作成しなさい。  
* Storage()
  * 引数と同名のフィールドを、引数の値で初期化する
* getProperty()
  * 自身の性能を表す文字列を返す(抽象メソッド)

#### Exercise4_1クラス

* main()
  * Computerを1つインスタンス化し、直後にboot()する
  * HDDをインスタンス化し(capacity=500000000000, rpm=7200)、上でインスタンス化したComputerにsetStorage()を用いてセットする
  * Computerをboot()する
  * SSDをインスタンス化し(capacity=250000000000)、ComputerにsetStorage()を用いてセットする
  * boot()する

#### 実行結果


```java
コンピュータを起動しています...		// boot()
ストレージの接続を確認しています...	接続されていません.
正常に起動できませんでした.
コンピュータを起動しています...		// boot()
ストレージの接続を確認しています...	接続されています.
type:HDD	capacity:500000000000Bytes	rpm:7200
正常に起動できました.
コンピュータを起動しています...		// boot()
ストレージの接続を確認しています...	接続されています.
type:SSD capacity:250000000000Bytes
正常に起動できました.
```


### 課題2

#### Computerクラス
* storage変数
  * storagesに名前を変える
  * ArrayList<Storage>を用いることで2つ以上のストレージを搭載できるように変更
  * ArrayList<E>がどういったものなのかは自分で調べること
* setStorage()
  * 引数のStorageを自身のstoragesに追加する
* boot()
  * Storageが何個搭載されているのかを表示
#### Exercise4_2クラス
* main()
  * ComputerとHDD(capacity=500000000000, rpm=7200)とSSD(capacity=250000000000)をインスタンス化する
  * boot()する
  * 上でインスタンス化したComputerにHDDとSSDを搭載させる
  * boot()する
#### ヒント

```java
ArrayList<E>
```

可変長配列の一種であり、要素の最大数が理論上無限な配列。  
配列と同じような操作が可能  
`List<E> list = new ArrayList<E>();`と記述してインスタンス化(Eは任意の型)  
void add(E)メソッドにより配列の末尾に要素を追加できる。  
boolean isEmpty()メソッドにより配列がカラなのかどうかを判定する。  
int size()メソッドにより配列の.lengthのように要素数を取得できる。  
  

#### 実行結果

```
コンピュータを起動しています...		// boot()
ストレージの接続を確認しています...	接続されていません.
正常に起動できませんでした.
コンピュータを起動しています...		// boot()
ストレージの接続を確認しています...	接続されています.
[0]type:HDD capacity:500000000000Bytes rpm:7200
[1]type:SSD capacity:250000000000Bytes
正常に起動できました.
```

### 課題3

#### Storageクラス

新たに以下の機能を追加する。  
* +write()
  * 引数として受け取った文字列をdataに格納する
  * 格納出来る文字数はcapacityの値までであり、書き込めなかった場合はfalseを返す
* +canWrite()
  * 引数として受け取った文字列を書き込むことが出来るかを返す
* +read()
  * dataの値を返す

#### Computerクラス

新たに以下の機能を追加する。
* +writeToStorage()
  * 引数として受け取った文字列をStorageに書き込む
  * Storageが複数ある場合は、受け取った文字列を全て書き込むことが出来るStorageに書き込む
* +showData()
  * Storagesの各dataをread()を用いて表示する
  * dataに何も格納されていない場合はread()がnullを返すため、何かしら文字が格納されているdataのみ内容を表示する

#### Exercise4_3クラス

* main()
  * ComputerとHDD(capacity=15, rpm=5400)とSSD(capacity=30)をインスタンス化し、ComputerにHDDとSSDを搭載させる
  * boot()する
  * 上でインスタンス化したComputerに、 “This is an exercise.” という文字列を保存させる
  * ComputerのStorageに保存されているデータを表示する

#### 実行結果


```java
コンピュータを起動しています...		// boot()
ストレージの接続を確認しています...	接続されています.
[0]type:HDD capacity:15Bytes rpm:5400
[1]type:SSD capacity:30Bytes
正常に起動できました.
[1] のストレージに “This is an Exercise.” と書き込みました.
[1] “This is an Exercise.”
```


## 終わった学生

今回の課題に全て取り組んだ学生のクラス図は下のようになっていると思います。  
クラス設計が下手な人の元で作業すると、クラス間を繋ぐ線がグチャグチャになり、クラス同士の関係を把握し辛くなります。  
みなさんも一度自分で作ったプロジェクトのクラス図を作ってみてはいかがでしょうか？  
/*image*/</br>
[クラス図作成用URL](http://plantuml.com/ja/)  
次回はインターフェイスについて取り扱います。  
今回の課題内容を全て把握/理解することが出来ていればインターフェイスも難なく乗り越えられるものと思われます。 

[目次へ](../README.md)
