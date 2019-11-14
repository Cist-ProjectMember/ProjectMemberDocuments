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

課題1で作成したFormに送信ボタンをつけなさい。

なお、htmlでは `<button>` タグの代わりに、typeを"submit"に設定した `<input>` を使用しなさい。<br/>
また、Formに紐づけるButtonのwicket:idは `submitButton` とすること。<br/>
さらに、Buttonがクリックされた場合に標準出力に `ボタンがクリックされました` と表示するようにしなさい。

ヒント1. Formに紐づいたButtonがクリックされると、Button#onSubmit() が自動的に呼び出される

### 課題3

ボタンを

