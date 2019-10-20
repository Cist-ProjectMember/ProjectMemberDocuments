# インターフェイス

## キーワード

* インターフェイス
* interface
* 実装
* implements

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
mainメソッドでIPowerToggleable型の変数を3つ宣言し、それぞれComputer、AirConditioner、UnmotivatedHumanをインスタンス化しなさい。
インスタンス化したComputer、AirConditioner、UnmotivatedHumanのtogglePowerメソッドをそれぞれ呼び出しなさい。

### 課題7

Exercise07クラスを作成し、mainメソッドを追加しなさい。</br>
mainメソッドでIPowerToggleableを型引数にとるListを宣言しなさい。
Computer、AirConditioner、UnmotivatedHumanをインスタンス化し、addメソッドを用いて上で宣言したListに追加しなさい。
Listに追加後、for文を用いてそれぞれのtogglePowerメソッドを呼び出しなさい。

#### 実行結果

```text
電源の状態が変化しました。
北海道ではエアコンはレアです。
やる気出たー！
```
