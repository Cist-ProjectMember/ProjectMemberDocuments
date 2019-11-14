# Apache Wicket-2

## キーワード

* Form
* Button
* TextField
* PasswordTextField
* setResponsePage
* WebPage

## 概要

### Form

ログイン画面やチャット画面など、ユーザからの入力を受け付ける場合に使われるのがフォームである。<br/>
WicketにおいてはFormクラスでフォームを作成できる。<br/>
ただし、Formだけでは入力を受け付けることができないため、下に示すButtonやTextFieldなどと組み合わせて使用する。

```html
<form wicket:id="reportForm"></form>
```

```java
Form reportForm = new Form("reportForm");
add(reportForm);
```

#### Button

フォームに付随するボタンを作成するにはButtonクラスを使用する。<br/>
このButtonがクリックされると、自動的に Button#onSubmit()が呼び出されるため、これをOverrideすることで具体的な処理を定義できる。

```html
<form wicket:id="reportForm">
  <!-- <form>の中に書くことに注意 -->
  <input wicket:id="submitButton" type="submit"/>
</form>
```

```java
// reportFormに対してButtonを追加する
reportForm.add(new Button("submitButton"){
  @Override
  public void onSubmit(){
    super.onSubmit();
    // 具体的な処理を記述
  }
});
```

#### TextField

フォームに付随するテキストフィールド(自由に文字を入力できる欄)を作成するにはTextFieldクラスを使用する。<br/>
TextFieldに入力された値は、セットされたModelから取得できる。

```html
<form wicket:id="reportForm">
  <!-- <form>の中に書くことに注意 -->
  <input wicket:id="reportTitle" type="text"/>
</form>
```

```java
// reportFormにTextFieldを追加する
IModel<String> reportTitleModel = Model.of("");
reportForm.add(new TextField("reportTitle", reportTitleModel));   // reportFormに対してaddすることに注意!
```

TextFieldに入力された値を取り出す場合の例を以下に示す。

```java
// 入力された文字列を標準出力に表示する
System.out.println(reportTitleModel.getObject());
```

#### PasswordTextField

基本的にはTextFieldと同じだが、入力された文字列が●で表示されるという違いがある。

### 画面遷移

Linkが押された場合に別のページに遷移させたい場合、`setResponsePage()` を用いることで画面遷移を実現できる。<br/>
setResponsePageの引数には、WebPageを継承したクラス自体か、もしくはそれをインスタンス化したものを渡す。

```java
// AnotherPageに遷移するLinkを追加する(型引数はVoid)
Link<Void> link = new Link<Void>("link"){
  @Override
  public void onClick(){
    setResponsePage(AnotherPage.class);
    // あるいは、
    // setResponsePage(new AnotherPage());
  }
}
add(link);
```

## 演習課題

### 課題に取り組む前に

前回作成した `Report` クラスを、`Serializable` インターフェイスを実装するように変更しなさい。<br/>
なお、`Serializable` インターフェイスを実装する際に特にメソッドをOverrideする必要は無い(抽象メソッドが存在しない)。

### 課題1

HomePage.javaおよびHomePage.htmlを編集して、フォームを作成しなさい。

なお、作成する `Form` の変数名は `form` とし、対応するwicket:idも `form` とすること。

### 課題2

課題1で作成したFormに送信ボタンを追加しなさい。

なお、htmlでは `<button>` タグの代わりに、typeを"submit"に設定した `<input>` を使用しなさい。<br/>
また、Formに紐づけるButtonのwicket:idは `submitButton` とすること。<br/>
さらに、Buttonがクリックされた場合に標準出力に `ボタンがクリックされました` と表示するようにしなさい。

Startクラスのmain()を実行し、`localhost:8080` で送信ボタンが表示されていることを確認しなさい。

ヒント1. Formに紐づいたButtonがクリックされると、Button#onSubmit() が自動的に呼び出される

### 課題3

課題1で作成したFormに文字列を入力する欄を追加しなさい。

htmlではtypeを"text"に設定した `<input>` タグを使用し、wicket:idは `userNameTextField` としなさい。<br/>
`IModel<String>`型の`userNameModel`を作成する。<br/>
また、`TextField`型の`userNameTextField` にTextFieldをインスタンス化する(コンストラクタに上で作成した`userNameModel`を渡す)。

Startクラスのmain()を実行し、`localhost:8080` でテキストフィールドが表示されていることを確認しなさい。

ヒント1. TextFieldに渡したModelから、実際に入力された値をString型で取り出せる

### 課題4

課題1で作成したFormにパスワードを入力する欄を追加しなさい。

htmlではtypeを"password"に設定した `<input>` タグを使用し、wicket:idは `userPasswordTextField` としなさい。<br/>
`IModel<String>`型の`userPasswordModel`を作成する。<br/>
また、`TextField`型の`userPasswordTextField` にTextFieldをインスタンス化する(コンストラクタに上で作成した`userPasswordModel`を渡す)。

Startクラスのmain()を実行し、`localhost:8080` でパスワードフィールドが表示されていることを確認しなさい。

### 課題5

課題2で追加したButtonのonSubmit()の処理内容を変更して、`userNameTextField` と `userPasswordTextField` に自分の学籍番号が入力された場合のみ標準出力に `自分の学籍番号が入力されました` と表示しなさい。

Startクラスのmain()を実行し、`localhost:8080` で各フィールドに自分の学籍番号を入力した場合のみ `自分の学籍番号が入力されました` と表示されるのを確認しなさい。

ヒント1. onSubmit()の中で、条件分岐を用いることで文字列比較しなさい<br/>
ヒント2. 文字列比較は `==` ではなく、String#equals(String) を用いること

### 課題6(発展)

新たにページを作成し、HomePageからリンクをクリックすることで画面遷移できるようにする。

新しくWebPageを継承したFortunePageクラスを作成する。<br/>
また、FortunePage.javaに対応する同名のhtmlファイルも作成する。

リンク元を作成するために、HomePage.javaおよびHomePage.htmlを編集し、FortunePageへのリンクを追加しなさい。<br/>
ただし、作成するLinkのwicket:idは `toFortunePage` とする。

ヒント1. 追加したLinkの `onClick()` の処理を書き換えることで画面遷移を実現する

### 課題7(発展)

FortunePage.javaおよびFortunePage.htmlを編集して、HomePageに戻るリンクを作成しなさい。
