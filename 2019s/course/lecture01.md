# チュートリアル

## はじめに

* 分からないときは素直に手を挙げる
  * 分からないことは次に持ち越さないこと
* 予習/復習は必ず行うこと。
  * 講習では知識がついているかの確認は取らない
  * 前回までの知識は全て習得しているものとして進行する
* 時間外の質問/相談は直接もしくはSlackで<br/>
直接聞いた方がいいこともあります

### プロジェクトの作成
* C(大学PCはZ)ドライブ直下に ”prmn2019s” フォルダを作る
* IntelliJを起動後、Create New Project を選択する
* 左側のメニューから Java を選択
* 上部の Project SDK で 12 を選択し、Nextを押す
* もう一度Nextを押す
* Project locationに ”prmn2019s” フォルダへのパスを入れる
* Finishを押す


### パッケージの作成

* 左側のメニューの “prmn2019s” を開く
* ”src” フォルダを右クリックし、New > Packageを選択
* package nameには、”lecture01”と記入しOKを押す

今後特に指示が無い場合は ”lectureXX” の形式で作成する。

例: 第3回講義では、 prmn2019s/lecture03/


### クラスの作成

* 左側のメニューのsrc > lecture01を 右クリックする
* New > Java Class を選択する
* Nameには "Main" と記入しOKを押す

今後クラス作成をするときは、各lectureXXパッケージ内に作成すること


## 何もしないプログラム

* Mainクラスの {} の中にカーソルを合わせる
* `psvm` とタイプしTabキーを押す
  * 生成されたコード部分をmain()メソッドと呼ぶ
* コード入力スペース上で右クリックをする
* Run ‘Main.main()’ をクリック

画面下部に `Process finished with exit code 0` と表示されることを確認する


## 標準出力
`System.out.println(String str)`

この関数を用いることで標準出力に改行付きで文字列を表示させる事ができる</br>
(soutでショートカット入力することもできる)</br>
引用strには、`"`(Shift + 2キー)で囲った文字列を渡す</br>

例:

```java
System.out.println("We are Project Member.");`
```


## 四則演算
演算記号 `+`, `-`, `*`, `/`, `%` を用いることで四則演算ができる

例:</br>
```
int sum = 5+3;  //sumには8が入る
int sub = 5-3;  //subには2が入る
int mul = 5*3;  //mulには15が入る
int div = 5/3;  //divには1が入る(小数点以下は切り捨て)
int mod = 5%3;  //modには2が入る
```

## 文字列連結

Javaでは`+`演算子を用いることで文字列(もしくは数値を文字列へ変換したもの)を連結する事ができる

例：
```java
double temp = 18.7;
System.out.println("The temperature is " + temp + " degrees");	//"The tempareture is 18.7 degrees"と表示
```

## 条件分岐 if

処理を分岐させたい場合には `if`, `else if`, `else` を用いる
```
if(条件式1) {
	/* 条件式1が真の時実行 */
}
else if(条件分岐2) {
	/* 条件式1が偽かつ条件式2が真の時実行 */
}
else {
	/* 条件式1も2も偽だった時実行 */
}
```

比較には以下の記号を用いる
==(等値), !=(等値でない), >, >=, <, <=, &&, ||, !, ....


## 配列

Javaにおいて配列を定義するには以下のように記述する</br>
`型名[] 変数名 = new 型名[要素数];`

例：
`int[] array = new int[10];	//int型の配列を10要素分確保`

アクセスするには以下のように記述する</br>

```java
	array[4] = 3;	//arrayの4番目に3を代入する
```

## 繰り返し文 for
指定回数同じ処理をさせる場合にはfor文を用いる</br>
```java
for(初期化式; 条件式; 変動値) {
	/*条件式が真の繰り返しを処理する内容*/
}```

例：
```
for(int i=0;i < 10;i++){
  /*処理が終わるたびにiが+1され,i<10でなくなった時にfor文を抜ける*/
}
```


## 繰り返し文 while
繰り返し処理をする回数が定かでない場合にwhile文を用いる</br>
`whike(条件式){/*条件式が真の間繰り返される*/}`

例：
```java
int count = 0;
while(count < 100) {
	count++;	//count=100になると抜ける
}
```


## 条件分岐 switch
条件式により処理を複数分岐にしたい場合,それぞれの条件が独立している場合にswitch文を使う事ができる
```java
switch(分岐の処理である変数){
  case 条件1: /*処理内容*/ break;
  case 条件2: /*処理内容*/ break;
    ・・・
  default: /*上記に当てはまらなかったときの処理*/ break;
}
```
例：
```java
String series = "XS";  //Java SE 7よりStringのswitchが可能に
switch(series){
case "7":
	System.out.println("携帯で決済可");
	break;
case "8":
	System.out.println("ワイヤレス充電可");
	break;
case "X":
	System.out.println("画面に耳が生えた");
	break;
case "XS":
	System.out.println("充電がなくても携帯で決済可");
	break;
default:
	System.out.println("古き良き時代");
	break;
}
```
各ケースの末尾のbreakは忘れずに記述する</br>
    記述しなくてもエラーとはならないが、大抵が機銃者の意図と異なる挙動となる</br>
breakをかけない場合はしたのcaseの処理をbreakされるもしくはswitchのスコープから出るまで次々に行う</br>
    ->Fall through

    
## メソッド
処理を分割する際に用いるメソッドは以下のように記述する</br>
`修飾子 戻り値の型 メソッド名(引数1,引数2,...){/*処理内容*/}`

修飾子については後の講義で解説するため、それまでは就職しには何も記述しなくて構わない

例：
```java
public class Main {
	public static void main(String[] args) {
		print("Project Member");
  	}
	
	void print(String str) {
		System.out.println(str);
	}
}
```


## 演習課題
### 課題1-1
System.out.println()関数を用いて自分の情報を表示させる</br>
実行結果:`B21xxxxx Sosuke Kawagoe`

### 課題1-2
int型変数studentNumberに学籍番号の数値の部分を代入し、自分の情報を表示させる</br>
ただし,studentNumberを文字列連結させて表示させること</br>
実行結果:`B21xxxxx Sosuke Kawagoe`

### 課題1-3
int型変数ageに任意の値を代入し、行見識によって処理を分岐させ、実行結果のようになるようにしなさい</br>
また、文字列連結を用いてageによって表示される年齢を変動させること</br>
実行結果:
```
// ageが20未満の時
I am XX years old so I cannot drink liquor. //XXにageを表示
// ageが20以上の時
I am XX years old so I can drink liquor.  //XXにageを表示
```

### 課題1-4
要素数100のint型の配列arrayを用意し、それぞれに要素番号+1の値を代入し、配列arrayの数値を用いて偶数の値の総和を求めよ</br>
  代入処理及び総和を求める処理には繰り返し文を用い、総和をint型変数sumに代入すること</br>
  for,whileのどちらの繰り返し文を用いるかは各自考えること</br>
  ただし、なぜその繰り返し分を記述したのかの理由を答えよ</br>
  
### 課題1-5
前川小学校の1年生は全部で３クラスあります。</br>
1年生全員を対象として算数のテストを行い,成績をつけることになりました.</br>
int型の1次元配列(テストの点数表)を引数にとる関数min(),max(),average()を作成し、各クラスのそれぞれの最低点をint型,最高点をint型,平均点をdouble確で返すようにせよ.</br>

また、条件分岐を用いて60点未満を不可、60\~70点未満を可、70\~80点未満を良、80\~90点未満を優、90\~100点を秀とし表示例のように表示せよ。</br>
※テストの点数表はこちらが用意するものを用いること</br>
表示例:
```
1組 0番 82点 優
1組 1番 34点 不可
.....
最高点:82点
最低点:1点
平均点 72.3422222点
.....
2組 0番 34点 不可
2組 1番 98点 秀
.....
最高点:98点
最低点:1点
平均点 78.2388888点
```
#### テストの点数表
以下のコードを適切な箇所に挿入してください</br>
`int[][] score = {{41,85,72,38,80},{69,65,68,96,22},{49,67,51,61,63}};`
