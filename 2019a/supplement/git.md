# Git

## Gitとは

## Gitのインストール

### For Windows

1. [Git for Windows](https://gitforwindows.org/)にアクセスする
1. `Download`をクリックしてGitのバイナリをダウンロードする
1. Git-x.x.x.x.-64-bit.exeを実行する
    1. `Information`をよく読んで`Next`をクリックする
    1. `Select Components`は`Git Bash Here`にチェックを付けて`Next`をクリックする
    1. `Choosing the default editor used by Git`は`Use Vim (the ubiquitous text editor) as Git's default editor`を選択して`Next`をクリックする
    1. `Adjusting your PATH environment`は`Use Git from the Windows Command Prompt`にチェックを付けて`Next`をクリックする
    1. `Choosing HTTPS transport backend`は`Use the OpenSSL library`にチェックを付けて`Next`をクリックする
    1. `Configuring the line ending conversions`は`Checkout Windows-style, commit Unix-style line endings`にチェックを付けて`Next`をクリックする
    1. `Configuring the terminal emulator to use with Git Bash`は`Use MinTTY (the default terminal of MSYS2)`にチェックを入れて`Next`をクリックする
    1. `Configuring extra options`は`Enable file system caching`と`Enable Git Credential Manager`にチェックを入れて`Next`をクリックする
    1. `Configuring experimental options`はどれにもチェックを入れずに`Next`をクリックする
    1. `Install`をクリックする

### For Mac

デフォルトでインストール済みのためインストールの必要なし

### インストールの確認

コンソールで以下のコマンドを実行する

```sh
git --version
```
