# github講習テキスト ~ 入門編(Edit now)

### 講習の前の準備
以下のセッティングをしていてください。

1. Gitのインストール（目次より資料を参考にしてください）
2. Githubへの登録（目次より資料を参考にしてください）
3. [参加スプレッドシート](a)の方に情報を入力しておいてください。

## 対象者レベル
GitやGithubって何？名前はしってるけど、よくわからないといったGit初心者向けな内容にしています。Git講習応用編はまた今後やりたいと思いますので、自分で判断して参加してください。

- git未経験者
- git初心者
- github初心者

## 講習の目標
- GitとGithubを使えるようにする
- Githubを用いて基本的な集団開発の流れを身につける

## 動作確認
- windows 10
- macOS (Catarina , Mojave)

---
## 目次
- Git講習の環境構築(Gitのインストール,Githubの登録)
- Gitとは
- バージョン管理の流れ
- Gitのよく使うコマンド
- 集団開発の注意点
- Handson~Githubでの開発の流れを体験しよう

## Git講習の環境構築
### Git install for windows
[Gitのインストール](https://github.com/Cist-ProjectMember/ProjectMemberDocuments/blob/master/2019a/supplement/git.md)
 
### Git install for mac
macはデフォルトでgitが入っているはずです。試しにターミナルで`git --version`と叩いてみましょう。もし見つからない人がいれば教えてください。 

### Githubの登録

[Sign up](https://github.com/join?source=header-home)

## Gitとは
Gitとはバージョン管理システムである。
バージョン管理とは、ファイルの状態をその都度保存しておくことでバージョンを行き来できることである。
あるファイルに変更を加えていくと、戻りたい時もあるだろう。
そんなときに戻れたりもする。
今回はGitのコマンドでバージョン管理の仕組みを理解しましょう。
また、それをGithubに応用して集団開発をスムーズにしていきましょう。  


## Gitのよく使うコマンド
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
変更した内容はコミットとして保存される。  
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
git(github)を使う上で一番気をつけないといけないのが`競合(conflict)`が起こることです（なってしまってもどうにかなりますがややこしいです）。なるべくこれを回避しなければいけません。
原因は代表的なもので言うと、

1. 同じファイルを複数人で作業する
2. データベースやサーバなどの設定ファイルを各々の環境に合わせて書き換えている

などが挙げられます。これらを解決するためにルールを設けることが必要です。決まったルールはありませんが、それを立てておくことで、競合が起こる可能性を低くすることができるでしょう。

---
## handson〜githubでの開発の流れを体験しよう
ただ、話だけ聞いても分けがわからないと思うので、実際に手を動かしてみてみましょう！  

### 準備
- githubのアカウントを作成していない人またはgitが入っていない人は上の`git講習の環境導入`からやってください！
- 今回は集団開発の流れを体験するので、4人程度のグループを作成してください！


### ステージングの考え方
Gitには大きく分けて4つのステージがらなります。図を参考にしてください。

![image](a)  


### Gitでのバージョン管理での流れ
あるファイルを作成して、それを変更していきます。なお、今回は `git status`を多用していきます。

- 適当なディレクトリーに行ってテストファイルを作成します。

このままではファイルの変更は管理できません。
まずはGitを使えるようにしましょう。

- `git init`でGitを立ち上げます。

```git
dhcp10:git-prac kklab$ git init
Initialized empty Git repository in /Users/kklab/git-prac/.git/
```

これで`ls -a`でファイルを確認すると、`.git`ファイルができていますね。ちなみに`.git`ファイルは[こちら](https://qiita.com/HALU5071/items/ab27f596f27a14c29762)のようになっているみたいです。

- `vi test.txt`でテキストファイルを作成してください。（viが嫌な人は違うエディタで新規作成して、`git-prac`の中にそのファイルを突っ込んでください。）
`test.txt`の中に書く内容は自由です。なんか適当に書いてください。
保存してください。（この時点ではまだバージョン管理できていません。）
ここで、今のファイルの場所を確認しておきましょう。

- `git status`で状況を確認します。

```git
dhcp10:git-prac kklab$ git status
On branch master

Initial commit

Untracked files:
  (use "git add <file>..." to include in what will be committed)

	test.txt

nothing added to commit but untracked files present (use "git add" to track)
```

この中の `Untracked files:` が追跡されていないファイル、つまりバージョン管理をしていないファイルになります。
見てみるとこの中に `test.txt` が入っていますね。これを追跡してもらう必要があります(add)。

- `git add test.txt`でファイルを追跡してもらいます。

```git
dhcp10:git-prac kklab$ git add test.txt
```

これで再度statusしてみると、

```git
dhcp10:git-prac kklab$ git status
On branch master

Initial commit

Changes to be committed:
  (use "git rm --cached <file>..." to unstage)

	new file:   test.txt

```

変わりましたか？ここに `Changes to be committed:`とあります。これが、stagedにいる状態です。これでコミットされるべきファイルができました。早速コミットしていきましょう。

- `git commit -m "first commit!"`でコミットしていきます。

```git
dhcp10:git-prac kklab$ git commit -m "first commit!!"
git commit -m "first commitgit status"
[master (root-commit) a01252c] first commitgit status
 1 file changed, 1 insertion(+)
 create mode 100644 test.txt
```

こんな具合でコミットできましたね。ちなみにstatusしてみましょう。

```git
dhcp10:git-prac kklab$ git status
On branch master
nothing to commit, working tree clean
```

これで `Unmodifed` にいる状態です。コミットできるファイルはなく、ワーキングツリーは最新の状態ですので、これで最初のコミットが完了です。
ここからコミットを重ねていきましょう。

- `test.txt`を変更します。 `vi test.txt`でファイルを開き何かしら変更して保存してください。

保存したらstatusしてみましょう。

```git
dhcp10:git-prac kklab$ git status
On branch master
Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git checkout -- <file>..." to discard changes in working directory)

	modified:   test.txt

no changes added to commit (use "git add" and/or "git commit -a")
```

こんな感じのが出てきたでしょうか。よくみると赤色で `modifed`と書いてますね。これが変更後のファイルです。ただ、addしていないので `not staged`と言われています。

これを同じ感じでaddしてコミットしていきます。また、statusもしてみましょう。

```git
dhcp10:git-prac kklab$ git add test.txt 
dhcp10:git-prac kklab$ git status
On branch master
Changes to be committed:
  (use "git reset HEAD <file>..." to unstage)

	modified:   test.txt

```

addすると `modifed`が緑色になりました。これでコミットできるようになります。なのでコミットしていきます。

```git
dhcp10:git-prac kklab$ git commit -m "second commit!!"
git commit -m "second commitgit status"
[master 78909b6] second commitgit status
 1 file changed, 3 insertions(+)
```

できましたか？ではstatusしてみましょう。どんな結果が返ってくるでしょうか？おそらく、もうコミットするものがありません的なやつですかね。

```git
dhcp10:git-prac kklab$ git status
On branch master
nothing to commit, working tree clean
```

予想通りでしたね。こんな感じでコミットを重ねて記録をしていくわけです。

では、前のバージョンに戻したい場合はどうしたらいいでしょうか？Gitの特徴として、コミット履歴を遡って戻すことができます。これを実際にやってみましょう。
そのための方法としていくつかあるので紹介します。

1つ目は`reset`コマンドを使うと、編集内容が全て取り消されます（addする前に戻す感じ）。
例えば、「あ、addしちゃった。戻してえええ」となってしまうときに使います。
これを確認するためにまずはファイルを編集します。viなどで適当にファイルを編集してください。
そしてstatusしてみると

```git
dhcp10:git-prac kklab$ git status
On branch master
Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git checkout -- <file>..." to discard changes in working directory)

	modified:   test.txt

no changes added to commit (use "git add" and/or "git commit -a")
```

もう見慣れてきましたね。ここからstagedに移動します。(add)

```git
dhcp10:git-prac kklab$ git add test.txt 
dhcp10:git-prac kklab$ git status
On branch master
Changes to be committed:
  (use "git reset HEAD <file>..." to unstage)

	modified:   test.txt

```

ここで、addしてしまったものを元に戻す方法があります。これが `reset`です。

```git
dhcp10:git-prac kklab$ git reset test.txt 
Unstaged changes after reset:
M	test.txt
```

これでreset終了です。試しに戻っているか確認してみましょう。

```git
dhcp10:git-prac kklab$ git status
On branch master
Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git checkout -- <file>..." to discard changes in working directory)

	modified:   test.txt

no changes added to commit (use "git add" and/or "git commit -a")
```

赤くなっているので、成功です。

次は、コミットの取り消しです。そのためには `revert`を使います。

`git revert コミットハッシュ`が基本です。まあ、難しいので、流れだけ載せますね。

```git

```




ちなみに `diff`コマンドというものもあって、コードの差分を表示してくれます。

```git
dhcp10:git-prac kklab$ git diff --cached
diff --git a/test.txt b/test.txt
index 7d687c7..959ad74 100644
--- a/test.txt
+++ b/test.txt
@@ -6,4 +6,4 @@
 
 変更3回目ですうううう！！！これはcheckoutで内容をaddする前に持っていくことを確
認するためのものです。
 
-reset用のテストコード
+reset用のテストコード2
```

`--cached`はaddした後に変更点を確認することができます。他にもcommit間での差分を確認するためのコマンドもある。

そのためにはコミットのハッシュが必要である。確認するためには `git log`コマンドを使う。

```git
dhcp10:git-prac kklab$ git log
commit c53470a0af73e09aab43a35a079f379132b6c298
Author: ito <cist.b211.ito@gmail.com>
Date:   Thu Jan 30 15:40:47 2020 +0900

    diff commit

commit bf4277a4707fa25943ef427b20e156237bdc165f
Author: ito <cist.b211.ito@gmail.com>
Date:   Thu Jan 30 14:19:09 2020 +0900

    sub commit

commit 90a84440d9b2eba3436c748f85bda2d2712ee5a3
Author: ito <cist.b211.ito@gmail.com>
Date:   Thu Jan 30 13:33:26 2020 +0900

    sub commitgit status

commit 78909b6839c0f47e4eb2c21877cb4d5e44ac07dc
Author: ito <cist.b211.ito@gmail.com>
Date:   Wed Jan 29 11:09:09 2020 +0900

    second commitgit status

commit a01252c466eef79ac3e78068b0b868460705e6c2
Author: ito <cist.b211.ito@gmail.com>
Date:   Tue Jan 28 19:24:50 2020 +0900

    first commitgit status
```

過去のコミット履歴をログと同時に確認できます。すると黄色い16進数が出てくるのですが、これがハッシュです。

この値を用いて差分を確認できます。そのためには `git diff 以前のハッシュ..今回のハッシュ`を用いる。

```git
dhcp10:git-prac kklab$ git diff bf4277a4707fa25943ef427b20e156237bdc165f..a01252c466eef79ac3e78068b0b868460705e6c2
diff --git a/test.txt b/test.txt
index 7d687c7..113d276 100644
--- a/test.txt
+++ b/test.txt
@@ -1,9 +1 @@
 変更1回目ですううううう！！
-
-
-変更2回目ですううう！！てへぺろ
-
-
-変更3回目ですうううう！！！これはcheckoutで内容をaddする前に持っていくことを確
認するためのものです。
-
-reset用のテストコード
```

まず、確認したい部分のハッシュを `log` から確認してください。



---
# 補足資料

## 知ってて便利！コマンド集

### diff
ファイルの変更の差分を表示してくれるコマンド。

`git diff`(add-commit間の差分を見てくれる)

`git diff --cached`(commit-commit間の差分を見てくれる)


