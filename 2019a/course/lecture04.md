# Apache Wicket

## キーワード

* Apache
* Wicket

## 概要

### プロジェクトの作成

1. Wicketの[QuickStartページ](https://wicket.apache.org/start/quickstart.html)を開く
2. Group IDを"com.prmn"に書き換える
3. Artifact IDを"prmn-wicket"に書き換える
4. generated command line内のコードをコピーする
5. プロジェクトを配置したいディレクトリを開く(大学PCなら"端末から開く"、自前のPCならCドライブ直下、Macはそれに準ずるディレクトリ)
6. 4でコピーしたコマンドをペーストして実行する
7. 指定したディレクトリに"prmn-wicket"ディレクトリが生成されていれば完了

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
3. "\[main] INFO org.eclipse.jetty.server.Server - Started @2505ms"と表示されるのを確認する("2505ms"の部分は環境により変動する)
4. ブラウザで"localhost:8080"を検索する
5. "Congratulations!"と表示されていれば成功

## 演習課題

### 課題に取り組む前に

HomePage.htmlを開き、\<body>タグ内のすべての要素を削除する

### 課題1
