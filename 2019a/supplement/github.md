# github講習テキスト(Edit now)

## 対象者レベル
今回のgithubの講習では、githubを使って最低限のグループ開発ができることを目標として行います。今後、さらに深い部分もやっていきたい

- git未経験者
- git初心者
- github初心者

## 目次
- gitとは
- gitの環境導入
- gitのよく使うコマンド
- 集団開発の注意点
- handson~githubでの開発の流れを体験しよう

## gitとは
`git`とは、システムのバージョンを管理するシステムである。あるファイルに変更を加えていくと、戻りたい時もあるだろう。そんなときに戻れたりもする。今回はgitのコマンドでバージョン管理の仕組みをマスターしましょう。また、それをgithubに応用して集団開発をスムーズにしていきましょう。  

## git講習の環境導入
### git install for windows

[Gitのインストール](https://github.com/Cist-ProjectMember/ProjectMemberDocuments/blob/master/2019a/supplement/git.md)
 
### git install for mac
macはデフォルトでgitが入っているはずです。試しにターミナルで`git --version`と叩いてみましょう。もし見つからない人がいれば教えてください。 

### githubの登録

[Sign up](https://github.com/join?source=header-home)

## gitのよく使うコマンド

### status
stashはステージング情報を確認するためのコマンド  
勉強会内では何かあるたびにこれで確認しながら作業していきます。  
`git status`


### add
編集した内容を変更するための場所に置いておくためのコマンド。  

`git add file.txt`(file.txtをaddする)

`git add .`(ディレクトリ内の全てのファイルをaddする)



### commit
編集した(addされたファイルの)内容を変更（ローカルリポジトリを更新）するためのコマンド。  
基本的に変更した内容をコミットログとして残しておく必要がある。

`git commit -av`(viエディタで変更した内容のコメントを入力する)

`git commit -m "file.txtを作成"`(""の中に変更した内容のコメントを入力する)

### push
リモートbranchに変更した内容を更新するためのコマンド。  
`origin`はリモートということで、`origin master`はリモートの`master`ブランチのことである。

`git push -u origin master`(初回のみ-uを付けて実行する)

`git push origin crud`(originのcrudを変更する)

注意：リモートのリポジトリにpushする際、remoteのurlを指定しないといけないので、以下のコマンドを使用して、指定します。

`git remote add origin branchName`

### branch
作業場所についてのコマンド。

`git branch`(ローカルのブランチを確認できる)

`git branch -a`(ローカルとリモートの両方のブランチを確認できる)

`git branch crud`(crudブランチをローカルに作成)

### checkout
作業場所の変更をするコマンド。

`git checkout crud`(crudブランチに入る)

`git checkout master`(masterブランチに入る)

## 集団開発の注意点
git(github)を使う上で一番気をつけないといけないのが`競合(conflict)`が起こることです（なってしまってもどうにかなりますがややこしいです）。なるべくこれを回避しなければいけません。原因は代表的なもので言うと、

1. 同じファイルを複数人で作業する
2. データベースやサーバなどの設定ファイルを各々の環境に合わせて書き換えている

などが挙げられます。これらを解決するためにルールを設けることが必要です。決まったルールはありませんが、それを立てておくことで、競合が起こる可能性を低くすることができるでしょう。


---
# handson〜githubでの開発の流れを体験しよう
ただ、話だけ聞いても分けがわからないと思うので、実際に手を動かしてみてみましょう！  

## 準備
- githubのアカウントを作成していない人またはgitが入っていない人は上の`git講習の環境導入`からやってください！
- 今回は集団開発の流れを体験するので、4人程度のグループを作成してください！

## Lecture01

1. `git branch yamada`と入力して、自分のブランチを作成してください。
2. `git checkout yamada`と入力して、自分のブランチにcheckoutしてください。
3. 早速作業してみましょう。`GitLectureGroup`ディレクトリの直下に`自分の名前のクラス`を適当に作ってみてください。
4. 作ったクラスを編集してみましょう。なお、`MountPath("yamada")`というように





---
# 補足資料

## 知ってて便利！コマンド集

### diff
ファイルの変更の差分を表示してくれるコマンド。

`git diff`(add-commit間の差分を見てくれる)

`git diff --cached`(commit-commit間の差分を見てくれる)

### 

## gitの概念
