# mavenのインストール手順

## maven install for windows

## maven install for mac
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
