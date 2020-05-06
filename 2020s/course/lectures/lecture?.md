## 型推論

### 型推論とは

Java 10以降には、ローカル変数の型推論という言語機能が新しく導入された。定型挿入文を減らし、コードの可読性を向上させることができる。  
ローカル変数を宣言する際に、型を`var`キーワードで置き換えると、コンパイルするときに、自動的に変数を初期化する記述から推論した適切な型を当てはめてくれる機能である。  

### 利用例

今までScannerをインスタンス化する時には

```java
Scanner scanner = new Scanner(System.in);
```

記述してきたと思う。  
しかし、この型推論の`var`を使うことで以下のように記述することができる。

```java
var scanner = new Scanner(System.in);
```

これだけでは実際あまり良さがわからないんだが(?)という感じかもしれないが、  
ローカル変数の記述を始める際にとりあえず`var`から始めればいいと考えれば楽だと思う。(個人的意見)

拡張for文の利用でも`var`は使うことができる。

```java
for (var num : array){
    System.out.println(num);
}
```

### 注意点

#### ArrayList<E>での注意点

ローカル変数の記述を始める際にとりあえず書けばいいと説明してすぐ掌返しみたいで申し訳ないが、  
何でもかんでも`var`から始めればいいというものではない。  

lecture03 > Exercise3_3.java でVegetableクラスのArrayList<Vegetable>を作成したと思う。  
これの左辺の型をただ`var`を使って書くと、

```java
var vegetableList = new ArrayList<>();
```

このようになると思う。しかしお分かりいただけだろうか、どこにも`Vegetable`クラスの記述がありません。  
これが何を意味するか。この記法でArrayListを作成した場合、型は`ArrayList<Object>`となってしまう。  
これを回避するには、右辺のインスタンス化するときに省略している部分をしっかり書いてあげるだけでよい。

```java
var vegebleList = new ArrayList<Vegetable>();
```

#### その他の注意点

普段、int型の変数を宣言するとき、`int num = 123;`と記述しているが、`Integer num = 123;`  
と記述することもできる。これは`List<Integer>`を宣言したときにわかるが、あまりint型とInteger型では  
変化がないように思える。しかし大きな違いとしてInteger型では変数の中身が`null`である可能性がある。  


```java
//int型にnullは代入できない。
int num = null;

//Integer型にはnullは代入できる。
Integer num = null;
```

この上で注意すべき点は`var`を用いて、

```java
var num = getNum();
```

という記述をしたとする。一見なんの問題もないように思えるが、`getNum()`メソッドの戻り値の型が、int型かInteger型なのか判断する事ができない。  
実際戻り値がIntegerである場合は`null`である可能性があるのでtry-catchを用いてNullPointerExceptionのチェックを行う必要があるため、見た目で戻り値の型が判断できない場合はできる限り`var`の利用は控えて、しっかりと型の指定をしよう。このように思わぬ点でエラーが発生してしまう可能性があるために、大規模な開発では話し合っておくべき必要があると思う。(個人的意見)

## 匿名クラス

### 匿名クラスとは

匿名クラス(別名:無名クラス)はとあるメソッドの中で一回しか使わない場合などに使われることがあるJavaにおける特殊なクラスのひとつである。  
イメージがつきにくいと思うが、つまり「その場で使い捨てる」クラスを作りたい場合のためにあると考えればいいと思う。(個人的意見)

### 利用例

実際、匿名クラスなんてどんなときに使うの(?)って思うかもしれません。実際使う場面は限られてきます。  
思いつく簡単な場合を考えてみます。  

とあるButtonクラスがあり、メソッドでonClick()を持っていたとします。

```java
public class Button {
    public void onClick() {
        System.out.println("ボタンが押された。");
    }
}
```

さらにこのボタンをバスの降車ボタンとして利用する場面があるとします。その場合はこのButtonクラスを継承して、

```java
public class StopButton extends Button {
    @Override
    public void onClick() {
        System.out.println("次止まります。");
    }
}
```

と記述することができるが、このボタンの種類がどんどん増えていく場合に、それ相応にクラスが増えていくことになる。  
これはどれがどのボタンか判断することも困難になりかねない。  
匿名クラスの宣言はこのように行う。 

```java
Button stopButton = new Button() {
    @Override
    public void onClick() {
        System.out.println("次止まります。");
    }
}
```

実際に、この匿名クラスを用いることでその場の一回きりのクラスとして宣言することで解消することができる。

## Lambda式

### Lambda(ラムダ)式とは

