# 継承

## 継承とは

似たようなクラスの共通部分(フィールド、メソッド)を別クラスとして切り出し、そのフィールドやメソッドを別クラスで受け継ぐことである。

## イメージ

RPGを題として継承を考えてみる。プレイヤーキャラクターは様々なスキルを持ち、あるものはダメージを与え、またあるものは毒効果が付与されるなど、それぞれ対象に与える効果が異なる。ここで「それぞれのスキルクラスを作成せよ」と言われれば、通常なら以下のようにするはずである。

```java
// 通常攻撃
class AttackSkill {  }

// 毒攻撃
class PoisonSkill {  }
```

それぞれのスキルには効果を与える対象がいるため、メソッドが必要となる。(ここではcast(Target)とする)

```java
// 通常攻撃
class AttackSkill {
    public void cast(Target t){}
}

// 毒攻撃
class PoisonSkill {
    public void cast(Target t){}
}
```

ここで新たに、発動するスキルをプレイヤーが選択するのに必要となる、各スキルの持つ効果をString型で返すメソッドを追加する。(ここではgetDescription()とする)

```java
// 通常攻撃
class AttackSkill {
    public void cast(Target t){}
    public String getDescription(){}
}

// 毒攻撃
class PoisonSkill {
    public void cast(Target t){}
    public String getDescription(){}
}
```

さらに、各スキルには基礎ダメージ値(basePower)が必ず存在し、毒のような付与効果のあるスキルには付与効果リスト(effects)が存在することとする。

```java
// 通常攻撃
class AttackSkill {
    private long basePower;
    public void cast(Target t){}
    public String getDescription(){}
}

// 毒攻撃
class PoisonSkill {
    private long basePower;
    // Effectは付与効果の情報を持つ
    private List<Effect> effects;
    public void cast(Target t){}
    public String getDescription(){}
}
```

加えて、


## 例

```java
public class Human {
    protected int height;
    protected int weight;
    protected String name;
    public Human(String name, int height, int weight){
        this.name = name;
        this.height = height;
        this.weight = weight;
    }

    public void say(){
        System.out.println("我は人間なり.");
    }
}
```

```java
// 大統領クラス
public class President extends Human{
    public President(String name, int height, int weight){
        super(name, height, weight);
    }

    @Override
    public void say(){
        System.out.println("我は大統領なり.");
    }
}
```

```java
// メインクラス
public class Main {
    public static void main(String[] args) {
        Human[] humans = new Human[2];
        humans[0] = new Human("Yamada", 180, 84);
        humans[1] = new President("Trump", 182, 140);
        for(Human human : humans){
            human.say();
        }
    }
}
```

実行結果

```text
我は人間なり.
我は大統領なり.
```

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
