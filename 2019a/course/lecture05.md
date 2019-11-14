# Apache Wicket-2

## キーワード

* Form
* Button
* TextField
* PasswordTextField
* setResponsePage

## 概要

### Form

#### Button

#### TextField

#### PasswordTextField

### 画面遷移

setResponsePage()

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

htmlではtypeを"text"に設定した `<input>` タグを使用しなさい。<br/>
また、上の`<input>`に紐づけるwicket:idは `userNameTextField` とすること。<br/>

Startクラスのmain()を実行し、`localhost:8080` でテキストフィールドが表示されていることを確認しなさい。

ヒント1. Formに紐づけるTextFieldに渡したModelから、実際に入力された値をString型で取り出せる

### 課題4

課題1で作成したFormに文字列を入力する欄を追加しなさい。

htmlではtypeを"password"に設定した `<input>` タグを使用しなさい。<br/>
また、上の`<input>`に紐づけるwicket:idは `userPasswordTextField` とすること。<br/>

Startクラスのmain()を実行し、`localhost:8080` でパスワードフィールドが表示されていることを確認しなさい。

### 課題5

課題2で追加したButtonのonSubmit()の処理内容を変更して、`userNameTextField` と `userPasswordTextField` に自分の学籍番号が入力された場合のみ `自分の学籍番号が入力されました` と表示しなさい。

Startクラスのmain()を実行し、`localhost:8080` で各フィールドに自分の学籍番号を入力した場合のみ `自分の学籍番号が入力されました` と表示されるのを確認しなさい。

ヒント1. onSubmit()の中で、条件分岐を用いることで文字列比較しなさい
ヒント2. 文字列比較は `==` ではなく、String#equals(String) を用いること

### 課題6(発展)

新たにページを作成し、HomePageからリンクをクリックすることで画面遷移できるようにする。

新しくWebPageを継承したFortunePageクラスを作成する。<br/>
また、FortunePage.javaに対応する同名のhtmlファイルも作成する。

リンク元を作成するために、HomePage.javaおよびHomePage.htmlを編集し、FortunePageへのリンクを追加しなさい。<br/>
ただし、作成するLinkのwicket:idは `toFortunePage` とする。

ヒント1. 追加したLinkの `onClick()` の処理を書き換えることで画面遷移を実現する

