# Docker

## Dockerとは

## Dockerのインストール

### For Windows

#### For Windows 10 Home

1. [DockerToolbox](https://docs.docker.com/toolbox/overview/)を開く
2. `Ready to get started?` の [Install Docker Toolbox for Windows](https://docs.docker.com/toolbox/toolbox_install_windows/) を開く
3. タスクマネージャより、CPUの仮想化が有効になっていること、64bit版OSであることを確認する
4. [DockerToolboxのGitHub](https://github.com/docker/toolbox/releases)より、最新版のexeファイル(DockerToolbox-xx.xx.x.exe)をダウンロードして実行する
5. `Docker Quickstart Terminal` を起動する
6. `Creating machine...` と表示された場合はエンターキーを押す
7. `Waiting for an IP...` と出て、しばらく何も変化がない場合はエンターキーを押す
8. 起動したターミナルにて `docker run hello-world` を入力、実行する
9. 様々な文章とともに、`Hello from Docker.` と表示されれば導入完了

参考: [DockerToolbox](https://docs.docker.com/toolbox/overview/)

#### For Windows 10 Professional

### For Mac

1. ターミナルにて、`brew install docker`コマンドを実行する
2. ターミナルにて、`brew cask install docker`コマンドを実行する

## Dockerのインストール確認コマンド

defaultが起動している状態で以下のコマンドを実行する

```sh
docker -v
```
