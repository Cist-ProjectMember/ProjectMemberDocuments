# Maven

## Mavenとは

MavenはApacheによりライセンスされている、Javaのプロジェクト全体を管理するためのツールである。<br/>
POM(Project Model Object)という考えに基づき、プロジェクトの全ての設定をXML形式のファイルであるpom.xmlに記述することでプロジェクトを管理することができる。<br/>

## Mavenの導入

### For Windows

1. [Mavenのダウンロード](https://maven.apache.org/download.cgi)を開く
2. サイト中部の、"Binary zip archive" の "apache-maven-3.6.2-bin.zip" からzipファイルをダウンロードする(`3.6.2`の部分はバージョン)
3. DLしたzipファイルを展開してCドライブ直下(好みに合わせて場所を変える)に配置する
4. システム環境変数"Path"に展開したフォルダへのPathを登録する(Cドライブ直下なら"C:/apache-maven-3.6.2/bin")
5. コマンドプロンプトにて、`mvn -v`を入力して実行
6. バージョン情報が表示されたら導入完了

### For Mac

macには`homebrew`という機能がある。`homebrew`は簡単にバージョン管理やインストールが行える優れものです。まずはこれをインストールします。  

詳しい手順については [こちらから](https://github.com/Yoshiki-Yamada/JavaSettingsDocument/blob/master/home-brew-install.md) 

では早速`homebrew`を使ってインストールしていきましょう。 
 
1. ターミナルを開く（よく使うと思うので、Dockに追加しておくといいかも）  
2. ここで`brew install maven`とコマンドを叩く  
3. `mvn -v`と入力して以下の文字が出てきたらOKです。もし出なかった場合は近くのB3に相談してください。

```
Apache Maven 3.6.0 (97c98ec64a1fdfee7767ce5ffb20918da4f719f3; 2018-10-25T03:41:47+09:00)
Maven home: /usr/local/Cellar/maven/3.6.0/libexec
Java version: 1.8.0_191, vendor: Oracle Corporation, runtime: /Library/Java/JavaVirtualMachines/jdk1.8.0_191.jdk/Contents/Home/jre
Default locale: en_JP, platform encoding: UTF-8
OS name: "mac os x", version: "10.15.1", arch: "x86_64", family: "mac"
```

これでインストールは終了です。この他にもAPPやjavaなどもbrewでインストールできるので調べてやってみてください！
