# PostgreSQL

## PostgreSQLのインストール

### For Windows

1. [PostgreSQLのダウンロード](https://www.enterprisedb.com/downloads/postgres-postgresql-downloads)を開く
2. `Windows x86-64`列の`Download`リンクをクリックする
3. ダウンロードしたインストーラを起動する
  1. `Installation Directory`はデフォルトのまま
  2. `Select Components`のチェックはデフォルトのまま
  3. `Data Directory`はデフォルトのまま
  4. **注意!** 忘れると取り返しがつかないため、ユーザーpostgresのパスワードは`postgres`とすること
  5. `Port`はデフォルトのまま(5432)
  6. `Advanced Options`の`Locale`は`Japanese, Japan`とすること
  7. `Ready to Install`まで`next`を押してPostgreSQLをインストールする
  8. `Completing the PostgreSQL Setup Wizard`と表示されたら、`Launch Stack Builder at exit?`のチェックを外して`Finish`を押して完了

### For Mac

homebrewにて、`brew install postgresql` と入力し実行する

## インストールの確認

コンソールにて、`psql --version`を実行してバージョンが表示されればインストール済み

