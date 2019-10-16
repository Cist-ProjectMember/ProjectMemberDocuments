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

さらに、各スキルには基礎ダメージ値(basePower)やクールタイム(coolTime)、スキル発動のためのコスト(cost)が必ず存在し、毒のような付与効果のあるスキルには付与効果リスト(effects)が存在することとする。

```java
// 通常攻撃
class AttackSkill {
    private long basePower;
    private long coolTime;
    private long cost;
    public void cast(Target t){}
    public String getDescription(){}
}

// 毒攻撃
class PoisonSkill {
    private long basePower;
    private long coolTime;
    private long cost;
    // Effectは付与効果の情報を持つ
    private List<Effect> effects;
    public void cast(Target t){}
    public String getDescription(){}
}
```

加えて、防御無視ダメージを与えるスキル、与えたダメージの一部を吸収するスキルなど、数百種類のスキルがこのほかに存在するとする。
このとき、上に挙げたクラスのbasePowerフィールドやcast()メソッド、getDescription()メソッドはどのクラスにも存在するため、各クラスに同じようなコードが書かれることになる。

ここで、"継承" を用いることによりこの状況を回避できる。
以下に例を示す。


## 例

```java
// すべてのスキルの元となるクラス
public class Skill {
    protected long basePower;
    protected long coolTime;
    protected long cost;
    public void cast(Target t){}
    public String getDescription(){}
}

// Skillを継承したAttackSkill
public class AttackSkill extends Skill {
    @Override
    public void cast(Target t){}
    @Override
    public String getDescription(){}
}

// 付与効果を持つスキル
public class ElementalSkill extends Skill {
    protected List<Effect> effects;
    @Override
    public void cast(Target t){}
    @Override
    public String getDescription(){}
}

// ElementalSkillを継承したPoisonSkill
public class PoisonSkill extends ElementalSkill {
    @Override
    public void cast(Target t){}
    @Override
    public String getDescription(){}
}
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
