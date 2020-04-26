# インターフェース

## ライブラリ(クラスライブラリ)とは

汎用的に使われる機能を誰もが利用できるようにまとめたもの。  
Javaの場合はクラス群となる(クラスライブラリとも呼ぶ)。  
自ら開発しなくても様々なプログラム部品がライブラリとして用意されている。  

## 標準ライブラリと外部ライブラリ

プログラミング言語に元から備わっているライブラリを「標準ライブラリ」と呼ぶ。  
Javaにおいては、標準で付属しているクラスのこと。  
C言語における <stdio.h> や <stdlib.h> などと同じ扱い。  
Javaでは対応するパッケージを import することでそのパッケージに属するクラスを使用することが出来る。  
例えば`import java.util.Scanner;`と記述すると、java.util パッケージ内のScannerというクラスを使用します、という意味になる。  
/*image*/
普段使用するクラスは、基本的に java.util パッケージ内に存在する

有志の開発者などが独自に開発するなど、プログラミング言語の外部で開発されたライブラリを「外部ライブラリ」呼ぶ。  


## クラスライブラリの種類

Javaにはクラスライブラリとして様々なクラスが標準で用意されている。</br>
例としては、</br>
* `java.util.ArrayList`
    * 可変長な配列(長さが理論上無限な配列)ArrayListを提供する
* `java.util.Scanner`
    * 標準入力からの入力を受け付けるScannerを提供する(scanf()のようなもの)
* `java.util.Random`
    * 乱数を生成するRandomを提供する(rand()のようなもの)</br>
クラスライブラリの詳細は[こちら](https://docs.oracle.com/javase/jp/11/docs/api/index.html)(Java SE 11)から確認可能


## クラスライブラリを使用する

クラスライブラリのScannerをimportし、実際に使用する場合、以下のように記述する(大体の場合はIDEが自動的にimportしてくれる)

```java
import java.util.Scanner;		// Scannerを使うという宣言
public class Main {
  public static void main(String[] args) {
		Scanner scanner = new Scanner(System.in);
		String input = scanner.nextLine();		// 1行分の入力を受け付ける
	}
}
```


## Java.util.ArrayListクラス

ArrayListクラスは、サイズが理論上無制限の配列を提供する。</br>
インスタンス化する際に、どういった型のArrayListを用意するのかを型引数という形で宣言しなければならない。</br>
型引数は <> の中に記述する。</br>
以下、Student型およびDog型のArrayListをインスタンス化する場合の例を示す。</br>

```java
ArrayList<Student> students = new ArrayList<>();
ArrayList<Dog> dogs = new ArrayList<>();
```

上の <> の中に書かれている型が型引数である。</br>
= の前後で型引数を同じにしなければならない。</br>


## java.util.ArrayListクラスの持つメソッド

ArrayListクラスはインスタンス化することで以下のメソッドが使用可能になる。</br>
ただし、ここではよく使うメソッドのみを挙げる。

```java
void add(E e)			//E型のeを末尾に追加する(例: Car型のcar、Tire型のtire )
E get(int index)		//index番目の要素を返す(例: arrayList.get(15) )
int size()				//要素数を返す(例: for(int i=0; i<arrayList.size(); i++){ /*  */ } )
boolean isEmpty()	//要素数が0ならtrue、そうでなければfalseを返す
					(例: if(arrayList.isEmpty()){  /* 処理 */  }  )
```


## java.util.ArrayListクラスの使用例

以下、Animal型を継承するDogおよびCatを、Animal型を型引数とするArrayListに追加しbark()を呼び出す例を示す。

```java
ArrayList<Animal> animals = new ArrayList<>();
animals.add(new Dog(“わんわん”));			// Dogを末尾(0番目)に追加
animals.add(new Cat(“にゃーにゃー”));		// Catを末尾(1番目)に追加
for(int i = 0; i < animals.size(); i++){
	animals.get(i).bark();					// animalsの i 番目
}
```


## 型引数にプリミティブ型をとるArrayList(発展)

ArrayListの型引数に、int型やlong型、double型などのプリミティブ型を渡そうとすると、エラーが出る。</br>
つまり、
`ArrayList<int> numbers = new ArrayList<>();	// ダメ！`
と記述が出来ないということである。</br>
ここで用いるのが、各プリミティブ型のラッパークラスであり、プリミティブ型をその名の通りラッピングするクラスのことである。</br>
例えば、int型ならIntegerクラス、double型ならDoubleクラスなど、プリミティブ型それぞれに対応するラッパークラスが用意されている。</br>

以上のことから、int型の値をListとして保持しておきたい場合、以下のように記述する。</br>
`ArrayList<Integer> numbers = new ArrayList<>();`</br>
ただし、実際にはnumbersにはInteger型のインスタンスが入っているため、Integerクラスのインスタンスの持つint型の値を表示するためには、Integerクラスの持つメソッド、</br>
`int intValue() `
を用いる。

## より詳しく知りたい場合

ArrayListの型引数にプリミティブ型の値を渡せないのは、ArrayListの定義が,

`ArrayList<E>`

でありそもそもEという型はクラスでなければならないためである。</br>
加えて、ArrayList<E>というクラスは、List<>というインターフェースを実装しているため(厳密には違う)、
	
`List<E> list = new ArrayList<>();`
という書き方が一般によく用いられる。

さらに詳しく知りたい場合は[こちら](https://docs.oracle.com/javase/jp/8/docs/api/java/lang/Integer.html)からドキュメントを参照すること。


## java.util.Scannerクラス

Scannerクラスは標準入力からの入力を受け付ける。</br>
コンストラクタにはどこからの入力を受け付けるのかを記述する。</br>
コンソールからの入力を受け付ける場合の例:
`Scanner scanner = new Scanner(System.in);`  
また、Scannerは以下のメソッドを持つ(よく使うもののみ抜粋する)</br>

```java
String nextLine()		// 入力された1行分の文字列を読み取って返す
String next()			// 入力された文字列の内、空白までの文字列を返す
int nextInt()			// 入力された32bit整数値を返す
double nextDouble()	// 入力された64bit浮動小数点値を返す
```

以下、標準入力から32bit整数値を受け取り、その値を表示する例を示す。

```java
	Scanner scanner = new Scanner(System.in);
	int input = scanner.nextInt();		// 32bit整数値の入力受け付け
	System.out.println(“入力された整数 = ” + input);

実行例:
> 64
入力された整数 = 64
```


## 演習課題

### 課題1

Exercise5_1クラスを作成し、その中にmain()メソッドを作成すること。</br>

#### Exercise5_1クラス

* main()
  * Scannerを用いて標準入力から任意の文字列を1行分取得し、それを標準出力に表示せよ

#### 実行結果

```java
任意の文字列を入力してください: 
> こんにちは。
	“こんにちは。” と入力されました
```

以降、 実行結果のうち、 “>” から始まる行は標準入力に入力した文字列とする。

### 課題2

Exercise5_2クラスを作成し、その中にmain()メソッドを作成すること。</br>
標準入力からの入力を受け付け、任意の行数分、任意の文字列を受け取るプログラムを作成しなさい。</br>

#### Exercise5_2クラス

* main()
  * Scannerをインスタンス化し、初めに何行分の文字列を入力させるかを入力させる
  * 指定された行数分入力を受け付け、それらの文字列をArrayListに追加しなさい
  * また、入力終了後、入力したすべての文字列を表示しなさい

__注意__

数値を読み取る際、ストリームに改行コードが残ってしまうため、nextLine()で空読みすること。

#### 実行結果


```java
何行分入力しますか？
	> 2
	1行目:
	> これは1行目の文字列かもしれない
	2行目:
	> これは2行目の文字列だと思います
	入力した文字列:
	[0]	これは1行目の文字列かもしれない
	[1]	これは2行目の文字列だと思います
```

### 課題3

Exercise5_3クラスを作成し、その中にmain()メソッドを作成すること。</br>
標準入力からの入力を2回分受け付けて、それを32bit整数値に変換した値を変数に代入し、それらの和を表示させなさい(実行結果を参照)</br>

#### Exercise5_3クラス

* main()
  * Scannerクラスを用いて標準入力から2回文字列を受け取り、その値を32bit整数に変換したのち、その和を表示させる
  * 受け取った文字列を32bit整数値に変換するには、Scannerクラスのメソッドである
  * `int nextInt()`を用いること

#### 実行結果


```java
1つ目の整数を入力してください:
> 35
2つ目の整数を入力してください:
> 42
35 + 42 = 77
```


### 課題4

課題5-3で作成したプログラムにおいて、整数以外の値(例: 23.8やhogehogeなど)を入力したときに、どのような結果が得られるか、b3の前で実演しなさい。</br>
また、そのような結果になったのはなぜかを、__例外__ という言葉を用いて説明しなさい。</br>
さらに、そのような結果になるのを回避するにはどういった処理が必要かを説明しなさい。</br>

## 課題が終わった学生

今回の課題は、今までのものと比べれば比較的簡単だったと思います。</br>
Javaを習得するということはクラスライブラリの使い方を習得することだと言っても過言ではありません。</br>
それほどクラスライブラリは重要なものなのです。</br>


次回は課題の中でも軽く触れたように、例外および例外処理について学習します。</br>
以降のデータベース講習でも例外および例外処理はどこにでも出てくるため、この時点で例外とは何なのか、雰囲気だけでも掴んでおいてください。</br>

