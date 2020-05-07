# オブジェクト指向プログラミング

## はじめに

* プロメンの活動についての連絡はSlackで行う
  * 各自Slackの通知を設定し、Slackで連絡が来てないか逐一確認すること
* lecture02パッケージを作成する
  * lecture02パッケージを作成し、この中に課題のクラスを作成すること
* main()メソッドを記述するクラス
  * main()メソッドはExerciseX_X(X_Xは課題番号)内に作成すること
  * 指示のある場合は指示に従うこと


## オブジェクト指向プログラミングとは

大規模なプロジェクトではコード量が数千、数万行にも及び、バグを見つけ出すことが困難となる。  
そこで考えられたのがオブジェクト指向であり、機能(メソッド)や状態(フィールド)を1つにまとめてクラスとし、プログラムの内部構造をモノの集まりとしてとらえる考え方である。  
このオブジェクト指向を取り入れたプログラミングを行うことをオブジェクト指向プログラミング(OOP)という。  
JavaはOOPが出来る言語の一つである。(Cは手続き型)  


## Javaにおけるクラス

Javaにおいてクラスを定義するには以下のように記述する。  

```java
class クラス名 {   }
class Television {    }     // テレビクラス
```

今後、クラス同士の相互作用を考えながらプログラミングをする必要が出てくる。  

クラス名とクラスが定義されているファイル(xxxx.java)の名前は統一することとする。

```java
// Main.java
public class Main {
	public static void main(String[] args){
		// 処理
	}
}
```


## クラスとインスタンス

クラスはあくまでどのような機能や状態を持つのかを定義している設計図であるため、単体で用いることは出来ない。  
クラスの持つ機能を利用するにはインスタンス化をする必要がある。  
インスタンス化により生成された実体のことをインスタンスもしくはオブジェクトと呼ぶ。  

Javaではインスタンス化をする際にnew演算子を用いる。  
以下にインスタンス化をする場合の例を示す。  

```java
クラス名　変数名（インスタンス名）　＝　new　クラス名();
Television television = new Television(); //テレビインスタンスもしくはテレビオブジェクトが生成された
```
new 演算子によりメモリ上に領域を確保することができる。  
また、変数名を変えてnewすることで同じ機能を持つ異なるインスタンスを生成することが出来る。  
```java
Television colorTelevision = new Television();
Television monochromeTelevision = new Television(); // colorTelevisionとmonochromeTelevisionはTelevisionクラスから生成された別々のインスタンス
```
以降の例文では、Televisionクラスは既に定義されているものとする。  

### インスタンスの配列

プリミティブ型と同じく、インスタンスも配列の形をとることが出来る。

```java
Television[] televisions = { 
  new Television(), new Television(), new Television() 
};		// 末尾のセミコロンを忘れずに記述する
```

### フィールドとメソッド

クラス内には変数や関数を定義することができ、それぞれフィールド、メソッドと呼ぶ。

```java
class Television {
	int channel;			// これはフィールド
	void turnPower(){		// これはメソッド
		/* 処理 */
	}		
}
```

引用strには、"(Shift + 2キー)で囲った文字列を渡す。

### インスタンス化とコンストラクタ 

Javaではインスタンス化をすると同時に呼び出される特別なメソッド(コンストラクタと呼ぶ)を定義することが出来る。  
コンストラクタの名前はクラス名と同じでなければならず、戻り値を記述してはならない。

```java
class Television {
	Television(){ 
		// 処理
	}
}
```

### コンストラクタと初期化

引数付きのコンストラクタを定義することも出来る。  
以下に引数付きコンストラクタの例を示す。  
this演算子により同名の変数を区別することができる。

```java
class Television {
	int channel;
	Television(int channel){
		this.channel = channel;
	}
}
```

### フィールドやメソッドの使用法

インスタンスのフィールドやメソッドはドット演算子 “.” を用いることで利用することが出来る。

```java
// TelevisionにturnPower()が定義されているものとする
Television television = new Television();
television.turnPower();		// “.”でメソッド呼び出しや
television.channel = 5;		// 変数の参照が可能
```

### インスタンスを受け取るメソッド

intやdoubleなどと同じく、メソッドの引数としてクラスのインスタンスを渡すことができる。

```java
// Plugクラスは既に定義されているものとする
class Television {
	Plug powerSupply;		// 電源
	void jointPlug(Plug plug){
		this.powerSupply = plug;
	}
}
```

## 演習課題

### 取り組む前に

#### 配列を宣言&定義する方法

```java
型名[] 変数名 = new 型名[];

```

new演算子がついているかや、[]の位置を確認すること。  

注意:</br>
上記の記述法では、配列の箱が作成されただけで、中身は何も入っていない。  

```java
// ダメな例
Television[] televisions = new Televisions[10];
televisions[2].channel = 3;		// エラー！配列の中身がカラ

// 良い例
Television[] televisions = new Televisions[10];
for(int i=0; i < televisions.length; i++){
	televisions[i] = new Television();	// 配列の中身にインスタンスを入れる
}
television[2].channel = 3;		// OK
```

#### 配列の全要素に処理を適用する方法 (その1)

```java
// arrayは既に定義されているものとする
for(int i = 0; i < array.length; i++) {
	// 処理
}
```

配列変数名.length によって、配列内の要素数を取得することが出来る。  

#### 配列の全要素に処理を適用する方法 (その2)

```java
for(型名 変数名 : 配列変数名){
	// 処理
}
```

この記述法を 範囲ベースfor文 と呼ぶ。

```java
int[] array = {2, 8, 3, 5, 7};
for(int number : array){  
	System.out.print(number + “,”);
}
/* “2,8,3,5,7,” と表示 */
```

### 課題1

以下の要件を満たすクラスを作成しなさい。  
* クラス名は Human、フィールドとしてString型の変数Nameとint型のageを持つ  
* 引数ありコンストラクタでNameとageを初期化する（名前と歳は何でもよい）  
* メソッドとして戻り値、引数無しのPrint() を持つ  
* Print()メソッドではNameとageを表示させる  
	  (例:  “Name age歳です。”)  
*ageが18歳以下の時は"生徒"、22歳以下の時は"学生"ということが分かる文言を表示させる(23歳以上は表示しない)

Humanをmain()メソッドでインスタンス化しPrint()を呼び出した後、新たにHumanをインスタンス化しそれぞれのPrint()を呼び出しなさい。

ヒント1.新しいクラスを作成するには  
* 左側のメニュー中のパッケージ (今回はlecture02)上で右クリックをし、 New > Java Class を選択  
* クラス名を入力する  
     main()メソッドは、Exercise2_1クラスに作成すること

#### 実行結果

```
生徒:たかし 18歳です。
学生:まい 20歳です。
```

### 課題2(発展)

以下の要件を満たすクラスを作成しなさい。
 * クラス名は Car、フィールドとしてint型の変数fuelを持つ
 * 引数なしコンストラクタでfuelを0で初期化する
 * メソッドとして戻り値、引数無しのrun() を持つ
 * run()メソッドではfuelを1消費して、走ったことが分かる文言を表示させる
 * (例: “燃料を1消費して走りました。”)
 * fuelが0以下の時走れなかったことが分かる文言を表示させる
        
Carに給油をするGasStationクラスを作成しなさい。  
* クラス名はGasStation、コンストラクタ無し
* void refuel(Car car)メソッドを持つ
* refuel()ではCarのfuelを20増やす
* refuel()では給油したことが分かる文言を表示する

main()ではCarとGasStationをインスタンス化し、GasStationで給油をする前と後でCarのrun()を呼び出しなさい。  
    main()メソッドは、Exercise2_2クラスに作成すること。
    
#### 実行結果

```java
燃料が足りないため走れませんでした。
給油したことによりfuelが20増えました。
燃料を1消費して走りました。
```

### 課題3(発展)

Carにタイヤとエンジンを組み込みなさい。
* TireクラスとEngineクラスを作成しなさい
* Carクラスのフィールドに、Tire型の配列tiresと、Engine型のengineを定義しなさい
* Carの引数無しコンストラクタを書き換え、Tire型のインスタンスの配列tires、Engine型のengineを受け取るようにし、上で定義したフィールドに代入しなさい
* Tireクラスはフィールドとしてint型のsizeを持ち、引数付きコンストラクタにて初期化する
  * Engineクラスはフィールドとして回転数を表すint型のrpmを持ち、引数付きコンストラクタにて初期化する
  * Engineクラスは戻り値/引数無しのstart()を持ち、自身のrpmの値と”エンジンを始動させました”と表示する
* Carクラスに戻り値/引数無しのstartEngine()を追加し、自身のengineのstart()を呼び出す

ここまで到達した学生は Exercise2-3クラスのmain()で、
* Tire型の配列tires(最大要素数4,要素数4)をインスタンス化(sizeは全て65)
* Engine型のengineをインスタンス化(rpmは4,000)
* これらをCarのコンストラクタに渡してCar型のcarをインスタンス化
* GasStation型のgasStationをインスタンス化し、refuel()でcarに給油する
* CarのstartEngine()、run()を呼び出しなさい

#### 実行結果

```java
給油したことによりfuelが20増えました。
rpm = 4000 でエンジンを始動させました。
fuelを1消費して走りました。
```

[目次へ](../README.md)
