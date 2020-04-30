# 継承

## キーワード

* 継承
* extends
* super

## 継承とは

似たようなクラスの共通部分(フィールド、メソッド)を別クラスとして切り出し、そのフィールドやメソッドを別クラスに受け継いだり、上書きや追加をすることである。
とは言っても、なかなか想像しがたいと思われるので、継承のイメージを以下の例でつかんでいただきたい。

## イメージ

ここではRPGを題材として継承を考えてみたい。
プレイヤーキャラクターはattackメソッドを用いてスライムに対して通常攻撃をすることができる。

```java
public class Player {
    // スライムへの攻撃メソッド
    public void attack(Slime slime){
        slime.setHitPoint(slime.getHitPoint() - 10);
    }
}
```

また、コウモリに対しても通常攻撃することができる。

```java
public class Player {
    // スライムへの攻撃メソッド
    public void attack(Slime slime){
        slime.setHitPoint(slime.getHitPoint() - 10);
    }
    
    // コウモリへの攻撃メソッド
    public void attack(Bat bat){
        bat.setHitPoint(bat.getHitPoint() - 10);
    }
}
```

ここで、引数の型が異なる同名のメソッドを定義しているが、これを **メソッドのオーバーロード** と呼ぶ。

さらに、トラやライオンに対しても通常攻撃できるとすると以下のようになる。

```java
public class Player {
    // スライムへの攻撃メソッド
    public void attack(Slime slime){
        slime.setHitPoint(slime.getHitPoint() - 10);
    }
    
    // コウモリへの攻撃メソッド
    public void attack(Bat bat){
        bat.setHitPoint(bat.getHitPoint() - 10);
    }
    
    // トラへの攻撃メソッド
    public void attack(Tiger tiger){
        tiger.setHitPoint(tiger.getHitPoint() - 10);
    }
    
    // ライオンへの攻撃メソッド
    public void attack(Lion lion){
        lion.setHitPoint(lion.getHitPoint() - 10);
    }
}
```

続いて、ダンジョンに潜むスケルトンや魔術師、最終階に待ち受ける魔王を...
そろそろ気づいたかと思われるが、この設計ではモンスターが増えるたびにPlayerクラスの持つattackメソッドが数十、数百と増えることになる。
ただ、それぞれのattackメソッドの処理を見てみると、どれも変数名は違えど体力をへらすという処理は同じである。
ここで用いるのが継承である。

継承を使うと、上の膨大なモンスター達は以下のようにまとめることができる。

```java
// モンスタークラス
public class Monster {
    // フィールドやアクセサは省略する
}

// スライムクラス
public class Slime extends Monster {
    // フィールドやアクセサは省略する
}

// プレイヤークラス
public class Player {
    public void attack(Monster monster){
        monster.setHitPoint(monster.getHitPoint() - 10);
    }
}
```

同じようなフィールド、メソッドを持つと分かっているクラスが設計段階で存在するのであれば、事前に抽象的なクラスとしてクラスを定義しておけば、これを継承したクラスを逐一作成することでコード量を削減することに繋がり、加えてバグの発生確率も減らすことができる。
今回の例の場合では、Playerのattackメソッドに3行程度消費しているため、モンスターの種類が100種類いるのであれば3行\*100種類の300行減らしたことになる。
実際には何でもかんでも継承を用いればすべてが解決するというわけではないため、場合によって使い分けることが必要である。どういった場合には継承を用いるべきなのかを判断できるようになれば、Java以外のその他のオブジェクト指向言語でもその知識が生かせるだろう。

## 演習課題

### 取り組む前に

IntelliJにてProjectMember2019aプロジェクトを作成し、lecture01パッケージを作成しなさい.</br>
以下の課題では、作成したlecture01パッケージ内で作業を行うこと.
引数および戻り値は各自判断すること.

### 課題1

Exercise01クラスを作成し、mainメソッドを作成せよ.</br>
Insectクラスを作成せよ.</br>
moveメソッドを作成せよ.</br>
moveメソッドでは"歩いたよ"とコンソールに出力せよ.</br>

mainメソッドにてInsectクラスをインスタンス化し、moveメソッドを呼び出せ.

### 課題2

Exercise02クラスを作成し、mainメソッドを作成せよ.</br>
Butterfly(チョウチョウ)クラスを作成しなさい.</br>
ButterflyはInsectを継承する.</br>
Butterflyのmoveメソッドでは"飛んだよ"とコンソールに出力せよ.</br>

mainメソッドにてButterflyクラスをインスタンス化し、moveメソッドを呼び出せ.

### 課題3

Exercise03クラスを作成し、mainメソッドを作成せよ.</br>

mainメソッドにてButterflyクラスのインスタンスを、Insect型の変数に代入せよ.</br>
また、インスタンス化したButterflyのmoveメソッドを呼び出せ.

### 課題4

Exercise04クラスを作成し、mainメソッドを作成せよ.</br>

Locust(バッタ)クラスを作成しなさい.</br>
LocustはInsectを継承する.</br>
Locustのmoveメソッドでは"跳んだよ"とコンソールに出力せよ.</br>

mainメソッドにてLocustクラスをインスタンス化し、moveメソッドを呼び出せ.

### 課題5

Exercise05クラスを作成し、mainメソッドを作成せよ.</br>

mainメソッドにてLocustクラスのインスタンスを、Insect型の変数に代入せよ.</br>
また、インスタンス化したLocustのmoveメソッドを呼び出せ.

### 課題6

Exercise06クラスを作成し、mainメソッドを作成せよ.</br>

SwallowtailButterfly(アゲハチョウ)クラスを作成しなさい.</br>
SwallowtailButterflyはButterflyを継承する.</br>
SwallowtailButterflyのmoveメソッドでは"綺麗に飛んだよ"とコンソールに出力せよ.</br>

mainメソッドにてSwallowtailButterflyクラスのインスタンスを、Insect型の変数に代入せよ.</br>
また、インスタンス化したSwallowtailButterflyのmoveメソッドを呼び出せ.

### 課題7

Exercise07クラスを作成し、mainメソッドを作成せよ.</br>

mainメソッドにてSwallowtailButterflyクラスのインスタンスを、Insect型の変数に代入せよ.</br>
キーワード "super" を用いることで、一度のmoveメソッド呼び出しで、"歩いたよ 飛んだよ 綺麗に飛んだよ" と表示するよう処理を書き換えなさい.
