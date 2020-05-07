## 型推論

### 型推論とは

Java 10以降には、ローカル変数の型推論という言語機能が新しく導入された。定型挿入文を減らし、コードの可読性を向上させることができる。  
ローカル変数を宣言する際に、型を`var`キーワードで置き換えると、コンパイルするときに、自動的に変数を初期化する記述から推論した適切な型を当てはめてくれる機能である。  

### 利用例

今までScannerをインスタンス化する時には

```java
Scanner scanner = new Scanner(System.in);
```

と記述してきたと思う。  
しかし、この型推論の`var`を使うことで以下のように記述することができる。

```java
var scanner = new Scanner(System.in);
```

これだけでは実際あまり良さがわからないんだが(?)という感じかもしれないが、  
ローカル変数の記述を始める際にとりあえず`var`から始めればいいと考えれば楽だと思う。(個人的意見)

拡張for文の利用でも`var`は使うことができる。

```java
for (var num : array) {
    System.out.println(num);
}
```

### 注意点

#### ArrayList<E>での注意点

ローカル変数の記述を始める際にとりあえず書けばいいと説明してすぐ掌返しみたいで申し訳ないが、何でもかんでも`var`から始めればいいというものではない。  

lecture03 > Exercise3_3.java でVegetableクラスのArrayList<Vegetable>を作成したと思う。  
これの左辺の型をただ`var`を使って書くと、

```java
var vegetableList = new ArrayList<>();
```

このようになると思う。しかしお分かりいただけただろうか、どこにも`Vegetable`クラスの記述がないじゃないか。  
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

上記のint型とInteger型の差で注意すべき点は`var`を用いて、

```java
var num = getNum();
```

という記述をしたときである。一見なんの問題もないように思えるが、`getNum()`メソッドの戻り値の型が、int型かInteger型なのか判断する事ができない。  
実際戻り値がIntegerである場合は`null`である可能性があるのでtry-catchを用いてNullPointerExceptionのチェックを行う必要がある。見た目で戻り値の型が判断できない場合はできる限り`var`の利用は控えて、しっかりと型の指定をしよう。このように思わぬ点でエラーが発生してしまう可能性があるために、大規模な開発では話し合っておくべき必要があると思う。(個人的意見)

## 匿名クラス

### 匿名クラスとは

匿名クラス(別名:無名クラス)はとあるメソッドの中で一回しか使わない場合などに使われることがある。Javaにおける特殊なクラスのひとつである。  
イメージがつきにくいと思うが、つまり「その場で使い捨てる」クラスを作りたい場合のためにあると考えればいいと思う。(個人的意見)

### 利用例

実際、匿名クラスなんてどんなときに使うの(?)って思うかもしれない。実際使う場面は限られている。思いつく簡単な場合を考えてみる。  

とあるButtonクラスがあり、メソッドでonClick()を持っていたとする。

```java
public class Button {
    public void onClick() {
        System.out.println("ボタンが押された。");
    }
}
```

さらにこのボタンをバスの降車ボタンとして利用する場面があるとする。その場合はこのButtonクラスを継承して、

```java
public class StopButton extends Button {
    @Override
    public void onClick() {
        System.out.println("次止まります。");
    }
}
```

と記述することができるが、このボタンの種類がどんどん増えていく場合に、それ相応にクラスが増えていくことになる。  
それではどれがどのボタンか判断することも困難になりかねない。  
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

はっきり言って僕本人も完璧には理解していないし、こんな時使うぜ。くらいにしか思っていない。  
今回のこの例では、バスの降車ボタンを例にしたが、よく考えるとバスに降車ボタンが一つしかついていないことなんてないので、ちゃんとButtonクラスを継承したStopButtonクラスを作成したほうがいいと思う。(バカ)

## Stream API

### Stream APIとは

Java 8以降から導入された機能で、配列やCollectionなどの集合体を扱い、値の集計やデータを使った処理などが出来る便利なAPIである。

### 使い方

#### 基本的な操作の流れ

1. Collectionからstreamを取得する。
2. 取得したstreamに対して何度でも __中間操作__ を行い、自分が意図した形に変換する。
3.  __終端操作__ を行い、変換したCollectionに適用する。

#### 利用例

この操作の流れだけを見てもしっくりこないと思うので既存のfor文を使った形と今回の __stream__ を使った形を比較しながら見ていく。

- 既存の方法
```java
List<String> numTextList = Arrays.asList("0", "1", "2", "3");
List<Integer> numList = new ArrayList<>();
for (String numText : numTextList) {
    numList.add(Integer.parseInt(numText));
}
```

- streamを利用した方法
```java
List<String> numTextList = Arrays.asList("0", "1", "2", "3");
List<Integer> numList = numTextList.stream()
        .map(s- > Integer.parseInt(s))
        .collect(Collectors.toList());
```

これらのプログラムは、`List<String>`を`List<Integer>`に変換する場合のプログラムである。今回はListの中身がnullである可能性は考えないこととする。  
パッと見だとあまり良さがわからないと思う、が明らかに可読性がよくなっている。具体的にどの点が良くなっているのかであるが、  
既存の方法だと、for文の中でStringからInteger型に変換しているのがわかる。今回はこの処理しか行っていないからまだ理解ができるのである。  
さらに明らかな違いは既存の方法だとひとつひとつ変換するたびにListに追加しているのがわかる。しかし、streamを利用した場合は、｢中間操作｣を終えて形を変換し終わった後に、終端操作を行いListに変換していることがわかる。  
つまりstreamを利用した場合はピリオドごとに何かが行われていることがわかるので可読性がいいと言える。  

他のパターンを用意した。

- 年齢が入っている`ages : List<Integer>`を用意する。  
- このListから __20歳以上__ の人のみのListに変換したいとする。

この場合のプログラムは、

```java
List<Integer> ages = Arrays.asList(17, 19, 20, 18, 23);
ages = ages.stream()
        .filter(s -> s >= 20)
        .collect(Collectors.toList());
```

 このようになる。今回は既存のfor文でのやり方は用意していないが、どう考えてもfor文より見やすいとは思いませんかね?僕は見やすいと思う。  
 
 こんなのどこで使うんだよ(?)と思うかもしれないが、実際使えなくてもどうにかなる場面は多い。しかし、streamを利用することで楽になる場面や、可読性が良くなって、後から自分でプログラムを読み直したときや、他人にプログラムを読んでもらった時などにフィーリングで理解しやすいものになると思う。  
 
 今回のこのprmn2020sの課題の中で頻繁に利用する
 
 ```java
 for (String text : textList) {
    System.out.println(text);
 }
 ```
 
 このようなプログラムがあったと思う。  
 
 このプログラムをstreamを利用して記述すると、
 
 ```java
 textList.stream().forEach(s -> System.out.prinln(s));
 ```
 または
  ```java
 textList.stream().forEach(System.out::prinln);
 ```
 
 と記述できる。  
 
 ここで登場した`.forEach()`も終端操作の一つである。
 
 今更であるが、`.forEach(s -> System.out.println(s))`の`s -> System.out.println(s)`ってなんやねん って思うかもしれないが、これはLambda式という記法である。これに関しての説明は今回はしないが`Java Lambda式`とでも調べたら出てくると思う。ちなみに`System.out::println`はメソッド参照と言う。
 
 streamやLambda(ラムダ)式はとても幅広く活用でき、可読性も向上させることができてJava特有の冗長性も少しは減らすことができるのでぜひとも興味がある人は学んでみてください。そして、新しい発見があった場合はぜひとも皆さんで共有してみてください。僕にも教えて下さい。(b2182360)
