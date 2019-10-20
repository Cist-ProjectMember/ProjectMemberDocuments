# インターフェイス

## キーワード

* インターフェイス
* interface
* 実装
* implements

## インターフェイスとは

インターフェイス(interface)とは、境界や接触面を表す英語で、Javaにおいてはメソッドの宣言のみが書かれたものの事である。
C言語を学んだ者に対しては、「Javaにおけるインターフェイス ≒ C言語における関数のプロトタイプ宣言」だと思ってもらって差し支えない。
Javaでインターフェイスを宣言するには <i>interface</i> キーワードを用いて以下のように記述する。

```java
public interface IHogeHoge {
  void hoge();
}
```

インターフェイスは継承のときと同じように、メソッドを引き継ぐことができるが、その呼び方は「継承」ではなく「実装」となる。
呼び間違えないように気を付けること。
以下にインターフェイスを実装する場合の例を示す。

```java
// FugaFugaクラスはIHogeHogeインターフェイスを実装している
public class FugaFuga implements IHogeHoge{
  @Override
  void hoge(){
    System.out.println("ほげ");
  }
}
```

また、一度に複数のインターフェイスを実装する場合は、カンマ区切りでimplementsする。

```java
public class Hoge implements Fuga, Piyo, Bar, Baz {
  // 省略
}
```

## 演習課題

### 取り組む前に

第1回講習にて作成したProjectMember2019aプロジェクトにlecture02パッケージを作成しなさい。</br>
以下の課題では、作成したlecture01パッケージ内で作業を行うこと. 引数および戻り値は各自判断すること。

### 課題1

IPowerToggleableインターフェイスを作成し、以下のコードを書き込みなさい。</br>
IPowerToggleableインターフェイスの持つtogglePowerメソッドではインスタンスの電源の状態を切り替えることができるとする。</br>
以下、コード例を示すが[]内には必要な語句を入れること。

```java
// IPowerToggleableインターフェイス
public [] IPowerToggleable {
  void togglePower();
}
```

### 課題2

Computerクラスを作成し、IPowerSwitchableインターフェイスを実装しなさい。</br>
ComputerのtogglePowerメソッドでは、"電源の状態が変化しました。"と表示しなさい。</br>
以下、コード例を示すが[]内には必要な語句を入れること。

```java
public class Computer [] IPowerToggleable {
  @[]
  void togglePower(){
    [];
  }
}
```

### 課題3

AirConditionerクラスを作成し、IPowerToggleableインターフェイスを実装しなさい。</br>
AirConditionerのtogglePowerメソッドでは、"北海道ではエアコンはレアです。"と表示しなさい。

### 課題4

Exercise04クラスを作成し、mainメソッドを追加しなさい。</br>
mainメソッドでComputer型の変数にComputerを、AirConditioner型の変数にAirConditionerをインスタンス化しなさい。<br>
インスタンス化したComputerとAirConditionerのtogglePowerメソッドをそれぞれ呼び出しなさい。

#### 実行結果

```text
電源の状態が変化しました。
北海道ではエアコンはレアです。
```

### 課題5

UnmotivatedHumanクラスを作成し、IPowerToggleableインターフェイスを実装しなさい。</br>
UnmotivatedHumanのtogglePowerメソッドでは、"やる気出たー！"と表示しなさい。

### 課題6

Exercise06クラスを作成し、mainメソッドを追加しなさい。</br>
mainメソッドでIPowerToggleable型の変数を3つ宣言し、それぞれComputer、AirConditioner、UnmotivatedHumanをインスタンス化しなさい。</br>
インスタンス化したComputer、AirConditioner、UnmotivatedHumanのtogglePowerメソッドをそれぞれ呼び出しなさい。

### 課題7

Exercise07クラスを作成し、mainメソッドを追加しなさい。</br>
mainメソッドでIPowerToggleableを型引数にとるListを宣言しなさい。</br>
Computer、AirConditioner、UnmotivatedHumanをインスタンス化し、addメソッドを用いて上で宣言したListに追加しなさい。</br>
Listに追加後、for文を用いてそれぞれのtogglePowerメソッドを呼び出しなさい。

#### 実行結果

```text
電源の状態が変化しました。
北海道ではエアコンはレアです。
やる気出たー！
```

## コラム

### そもそも継承やインターフェイスは必要か

必ずしも必要ではない。</br>
現にオブジェクト指向ではない言語にはそういった機能は存在しない(代替となるような機能は存在する)。</br>
それでも必要とされる理由には、「他人に実装を強制させられるから」といった理由や、「必ず特定のメソッドやフィールドを持っているということを保証できるから」という理由がある(その他理由はさまざま)。

### 宣言と定義

いくつかのプログラミング言語にも言えることだが、「Xを宣言しなさい」と「Xを定義しなさい」は別物である。</br>
文字で説明すると分かりづらいため、以下にそれぞれの例を挙げる。

```java
public class Hoge {
  // これは宣言
  public int fuga;
}
```

```java
public class HogeHoge {
  // これは定義
  public int fuga = 0;
}
```

「fugaという変数があります」というただの宣言と、「fugaという変数は0という値です」という定義をしているかという違いである。</br>
学習サイトなどでも混同されがちなため、よく注意すること。</br>
上と関連して、C言語で良くあるミスの中に「メソッドの定義のし忘れ」がある。</br>
以下にその例を示す。

```c
void hoge();  // プロトタイプ "宣言"

int main(void){
  hoge();
}
```

1行目の記述はあくまでhoge関数の"宣言"であり、具体的な処理内容は記述されていないため、エラーが発生するはずである。

### インターフェイスにフィールドを持たせる

Javaにおけるinterfaceは、メソッドの宣言のみしか記述できないというわけではなく、定数(staticかつfinal指定された値)も定義することができる。

```java
public interafce IHoge {
  static final long bar = 2019;
  void fuga();
}
```
