# Apache Wicket

## キーワード

* Apache
* Wicket
* Maven
* localhost

## 概要

### プロジェクトの作成

1. Wicketの [QuickStartページ](https://wicket.apache.org/start/quickstart.html) を開く
2. Group IDを `com.prmn` に書き換える
3. Artifact IDを `prmn-wicket` に書き換える
4. generated command line内のコードをコピーする
5. プロジェクトを配置したいディレクトリを開く(大学PCなら"端末から開く"、自前のPCならCドライブ直下、Macはそれに準ずるディレクトリ)
6. 4でコピーしたコマンドをペーストして実行する
7. 指定したディレクトリに "prmn-wicket"ディレクトリが生成されていれば完了

### IntelliJでImport

1. IntelliJの起動画面(Welcome to IntelliJ IDEA)を開く(既にプロジェクトを開いている場合には"File"->"Close Project")
2. "Import Project"を選択し、作成したプロジェクトを指定する
3. ラジオボタンで"Import project from external model"を選択し、Mavenを選択する
4. "Import Maven projects automatically"にチェックを付けて"next"を押す
5. そのまま"next"を押す
6. SDKを選択(今期のプロジェクトメンバーではAdoptOpenJDKのバージョン11を使用する)し、"next"を押す
7. そのまま"Finish"を押す

### 起動の確認

1. IntelliJで"prmn-wicket"->"src"->"test"->"java"->"com.prmn"->"Start"を開く
2. mainを実行する
3. `\[main] INFO org.eclipse.jetty.server.Server - Started @2505ms`と表示されるのを確認する("2505ms"の部分は環境により変動する)
4. ブラウザで `localhost:8080"` を検索する
5. "Congratulations!"と表示されていれば成功

## 演習課題

### 課題に取り組む前に

1. HomePage.htmlを開き、\<body>タグ内のすべての要素を削除する
2. 同じくHomePage.html内の、`<link href='https://fonts.googleapis.com/css?family=Yanone+Kaffeesatz:regular,bold' rel='stylesheet' type='text/css'/>` を削除する
3. 同じくHomePage.html内の、`<link rel="stylesheet" href="style.css" type="text/css" media="screen" title="Stylesheet"/>` を削除する
4. HomePage.javaを開き、`add(new Label("version", getApplication().getFrameworkSettings().getVersion()));` を削除する

### 課題1

HomePage.htmlとHomePage.javaを編集し、Labelを用いて自分の学籍番号を表示しなさい。

1. HomePage.htmlのbodyタグ内に `<span wicket:id="studentNumber"></span>` を追加する
2. HomePage.javaのコンストラクタ内に以下のコードを追加する

```java

```

編集後、Startクラスのmainメソッドを実行し `localhost:8080` で自分の学籍番号が表示されることを確認する。<br/>
以下、特に指示しなくても `localhost:8080` で検索し動作確認を行うこと。

### 課題2

ButtonでLabelの内容を変更する

### 課題3

Linkで別のページに移動する

### 課題4

ListViewでコレクションの内容を表示する
